# ITMO_DL_in_practice_02
Курс "Глубокое обучение на практике" (Project_02)

# company names matching

# Задачи проекта:

1. Задача классификации: определить, совпадают ли названия компаний.

2. Задача ранжирования: вывести N ближайших названий.

## Шаги проекта:

### Ноутбуки воспроизводимые, данные подгружаются ссылками с яндекс диска.

1) Подготовка данных:

   - low register
   - transliteration
   - удаление "ООО", "ОАО", 'общество с ограниченной ответственностью',
     'открытое акционерное общество' etc
   - удаление ltd., LLC etc с использованием CLEANCO
   
   в ноутбуке preproc_naming_classification.ipynb
   
2) Далее были созданы новые фичи, например такие как:

   - Levenshtein
   - Discounted_Levenshtein
   - String Subsequence Kernel Similarity
   - Jaro Similarity
   - и др.
    
    в ноутбуке preproc_naming_classification.ipynb

3) Произведены эксперименты по отбору фичей:

    - использована permutation importance 
      на основе градиентного бустинга и логистической регрессии

4) Обучена модель классификации:

Таблица: Метрики: 
| Metric\Model | GradientBoostingClassifier | LogisticRegression|
|--|--|--|
| precision macro avg | 0.61 | 0.83 |
| precision weighted avg | 0.99 | 0.99 |
| recall macro avg | 0.68 | 0.61 |
| recall weighted avg | 0.99 | 0.99 |
| f1-score macro avg | 0.64 | 0.67 |
| f1-score weighted avg | 0.99 | 0.99 |
| AUC | 0.51 | 0.51 |

![image](https://user-images.githubusercontent.com/60104674/198106275-b3b083a2-4217-48dc-a982-cb19b30045c9.png)


5) Решение задачи ранжирования:

    Для этой задачи были использованы эмбеддинги, построенные на Word2Vec и FastText.
    Модели Word2Vec и FastText были обучены на всем корпусе компаний.
    
    Для решения проблемы долгого поиска соседей была использована библиотека ANNOY, что существенно оптимизировало поиск, без проблем возможно    масштабирование проекта.
    
Таблица: Скорость обработки CPU:
| Model | word2vec | FastText |
|--|--|--|
| -- | 3 µs | 5 µs |


Ноутбук

## Команда 9.

### Вопросы telegram @dum_ai

