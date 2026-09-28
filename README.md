# Data Science Portfolio

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-data-150458?logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-notebooks-F37626?logo=jupyter&logoColor=white)

Учебные проекты по Data Science и Machine Learning: разведочный анализ данных (EDA), классический ML, временные ряды, NLP. Каждый проект лежит в своей папке со своим `README.md`, ноутбуком и данными, поэтому его можно запускать независимо от остальных.

## Каталог проектов

| # | Проект | Задача | Ключевые методы | Результат | Папка |
|---|--------|--------|-----------------|-----------|-------|
| 01 | Wine Quality Classification | Бинарная классификация качества красного вина | EDA, `StandardScaler`, `SVC` (RBF), `GridSearchCV`, `StratifiedKFold` | Accuracy: 89.1% CV, 92.2% test | [projects/01-wine-quality-classification](projects/01-wine-quality-classification) |

Планируются: детекция аномалий, временные ряды, чат-бот (NLP). Список будет пополняться.

## Стек

Python · pandas · NumPy · scikit-learn · Matplotlib · Jupyter

## Как запустить любой проект

```bash
git clone https://github.com/bestmark1/data-science-portfolio.git
cd data-science-portfolio
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cd projects/01-wine-quality-classification
jupyter notebook
```

Ноутбуки читают данные по относительному пути, поэтому запускать их нужно из папки проекта.

## Структура репозитория

```
data-science-portfolio/
├── README.md            # общий обзор и каталог (этот файл)
├── requirements.txt     # общие зависимости
└── projects/
    └── NN-project-name/
        ├── README.md    # описание проекта: задача, данные, методы, результаты
        ├── *.ipynb      # ноутбук
        └── *.csv        # данные проекта
```

## Как добавляется новый проект

1. Папка `projects/NN-короткое-название/` со следующим номером.
2. В ней: ноутбук, данные и свой `README.md` (задача, данные, методология, результаты, ограничения).
3. Строка в таблице «Каталог проектов» выше.
4. Новые библиотеки, если нужны, — в `requirements.txt`.
