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
   - удаление ltd., LLC etc usin CLEANCO
   
   в ноутбуке preproc_naming_classification.ipynb
   
2) Далее были созданы новые фичи, например такие как:

   - Levenshtein
   - Discounted_Levenshtein
   - String Subsequence Kernel Similarity
   - Jaro Similarity
   - и др.
    
    в ноутбуке preproc_naming_classification.ipynb

3) Произведены ксперименты по отбору фичей:

    - использована permutation importance 
      на основе градиентного бустинга и логистической регрессии

4) Обучена модель классификации:

Таблица метрик. 
| Method\Model | distiluse-base-multilingual-cased-v2 | all-MiniLM-L6-v2 | all-MiniLM-L12-v2 | paraphrase-MiniLM-L6-v2 | paraphrase-MiniLM-L12-v2 | all-mpnet-base-v2 |
|--|--|--|--|--|--|--|
| Qdrant + Not Preprocessed | 0.3256 | 0.5746 | 0.5860 | 0.5817 | 0.5839 | 0.5394 |
| Qdrant + Preprocessed | 0.4569 | 0.6183 | 0.6233 | 0.621 | 0.6162 | 0.6040 |
| Qdrant + Quanterion Preprocessed | 0.5633 | 0.6205 | 0.6233 | 0.62489 | 0.6133 | 0.6043 |

5) Решение задачи ранжирования:

    Для этой задачи были использованы эмбеддинги, построенные на Word2Vec и FastText.
    Модели Word2Vec и FastText были обучены на всем корпусе компаний.
    
    Для решения проблемы долгого поиска соседей была использована библиотека ANNOY, что существенно оптимизировало поиск, без проблем возможно    масштабирование проекта.
    
    Ноутбук

## Команда 9.

### Вопросы telegram @dum_ai

