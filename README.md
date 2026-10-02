# Data Science Portfolio

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-data-150458?logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-notebooks-F37626?logo=jupyter&logoColor=white)

Учебные проекты по Data Science и Machine Learning: разведочный анализ данных (EDA), классический ML, временные ряды, NLP. Каждый проект лежит в своей папке со своим `README.md`, ноутбуком и данными, поэтому его можно запускать независимо от остальных.

## Каталог проектов

### ⭐ Flagship

| # | Проект | Задача | Ключевые методы | Результат |
|---|--------|--------|-----------------|-----------|
| 01 | [Smart Replenishment](projects/01-smart-replenishment) | Прогноз спроса на 28 дней и приоритеты пополнения запасов (M5) | LightGBM, CatBoost, DuckDB, FastAPI, Streamlit, Docker | WMAPE 62.99% против 69.70% у лучшего baseline · [код](https://github.com/bestmark1/smart-replenishment) · [демо](https://smart-replenishment.185.79.138.118.nip.io) |
| 02 | [Sales Time Series Forecasting](projects/02-sales-time-series-forecasting) | Прогноз продаж сети магазинов (Kaggle Favorita) | ARIMA, Prophet, XGBoost, CatBoost | Праздники дали главный прирост точности: RMSE ≈109 → ≈74 тыс. |
| 03 | [tutu-swipe](projects/03-tutu-swipe) | Свайп-подбор путешествий поверх MCP Туту (ИИ-хакатон) | TypeScript, Next.js, MCP, байесовский ранжировщик | Первая карточка за 17 мс · [код](https://github.com/bestmark1/tutu-swipe) · [демо](http://45.150.39.20:8030) |
| 10 | [Честная цена?](projects/10-fair-price) | Проверка цены квартиры в объявлении: диапазон, вердикт, объяснение | CatBoost (quantile), CQR, SHAP, FastAPI, Leaflet, Docker | MAPE 11,0% против 20,9% у бейзлайна; интервал покрывает 80,0% цен · [код](https://github.com/bestmark1/fair-price) · [демо](https://fair-price.185.79.138.118.nip.io/?example) |
| 11 | [Мониторинг модели](projects/11-model-monitoring) | Мониторинг ML-модели в работе: качество, дообучение, дрейф данных | Prometheus, Grafana, FastAPI, scikit-learn (`partial_fit`), PSI, Docker Compose | Дообучение на потоке: accuracy 74,8% против 70,1% без дообучения · [код](https://github.com/bestmark1/model-monitoring) · [демо](https://bestmark1.github.io/model-monitoring/) |

### Классический ML и анализ данных

| # | Проект | Задача | Ключевые методы | Результат |
|---|--------|--------|-----------------|-----------|
| 04 | [NYC Taxi Trip Duration](projects/04-nyc-taxi-trip-duration) | Регрессия: длительность поездки такси | OSRM, погода, K-Means, XGBoost, CatBoost | RMSLE 0.39 (XGBoost) |
| 05 | [Bank Customer Classification](projects/05-bank-customer-classification) | Классификация: откроет ли клиент депозит | Тьюки, SelectKBest, Random Forest, Stacking, Optuna | Accuracy ≈ 0.82 |
| 06 | [Hotel Reviews EDA](projects/06-hotel-reviews-eda) | EDA отзывов Booking и бейзлайн рейтинга | Feature engineering, target encoding, RandomForest | MAPE ≈ 13.59% |
| 07 | [HH Resume EDA](projects/07-hh-resume-eda) | EDA резюме hh.ru: зарплатные ожидания | pandas, Plotly, очистка выбросов | Аномалии и зависимость ЗП от города и образования |
| 08 | [HH Vacancies SQL](projects/08-hh-vacancies-sql) | SQL-анализ вакансий hh.ru и рынка DS | PostgreSQL, psycopg2, pandas | 49 197 вакансий; 1 771 DS-вакансия, 51 для junior |
| 09 | [Wine Quality Classification](projects/09-wine-quality-classification) | Бинарная классификация качества красного вина | `StandardScaler`, `SVC` (RBF), `GridSearchCV`, `StratifiedKFold` | Accuracy: 89.1% CV, 92.2% test |

Планируются также детекция аномалий и NLP-проекты.

**Про данные.** У проектов 02, 04, 06, 07 и 08 исходные датасеты (или база данных) слишком велики для GitHub и не входят в репозиторий. Ссылки на источники — в README каждого проекта; результаты сохранены в выводе ноутбуков.

## Стек

Python · pandas · NumPy · scikit-learn · Matplotlib · Jupyter

## Как запустить любой проект

```bash
git clone https://github.com/bestmark1/data-science-portfolio.git
cd data-science-portfolio
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cd projects/09-wine-quality-classification
jupyter notebook
```

Ноутбуки читают данные по относительному пути, поэтому запускать их нужно из папки проекта. У проектов с тяжёлыми библиотеками (Prophet, CatBoost, Optuna, Plotly) есть свой `requirements.txt` в папке проекта.

## Структура репозитория

```
data-science-portfolio/
├── README.md            # общий обзор и каталог (этот файл)
├── requirements.txt     # общие зависимости
└── projects/
    └── NN-project-name/
        ├── README.md    # описание проекта: задача, данные, методы, результаты
        ├── *.ipynb      # ноутбук
        └── *.csv        # небольшие данные проекта (тяжёлые не хранятся в репозитории)
```

## Как добавляется новый проект

1. Папка `projects/NN-короткое-название/` со следующим номером.
2. В ней: ноутбук, данные и свой `README.md` (задача, данные, методология, результаты, ограничения).
3. Строка в таблице «Каталог проектов» выше.
4. Новые библиотеки, если нужны, — в `requirements.txt`.
