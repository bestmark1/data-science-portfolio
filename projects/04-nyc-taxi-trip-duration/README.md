# 04. Длительность поездки на такси в Нью-Йорке (регрессия)

Прогноз длительности поездки (`trip_duration`, секунды) по координатам, времени, погоде и маршрутам OSRM. Задача с Kaggle: [NYC Taxi Trip Duration](https://www.kaggle.com/c/nyc-taxi-trip-duration).

**Файлы:** [`NYC_Taxi_Trip_Duration.ipynb`](NYC_Taxi_Trip_Duration.ipynb) · [`requirements.txt`](requirements.txt)

## Задача

Стоимость поездки складывается из тарифа за время и расстояние, поэтому важно точно предсказывать время в пути. Метрика — **RMSLE**; обучение шло на логарифмическом таргете `log(trip_duration + 1)`, что сводит метрику к обычной RMSE.

## Данные

~1.5 млн поездок, расширенные внешними источниками:

1. **OSRM:** реальная дорожная дистанция, время по графу дорог, число шагов маршрута
2. **Почасовая погода Нью-Йорка:** температура, видимость, ветер, осадки, явления
3. **Праздничные дни США**

## Feature engineering

- **Время:** час, день недели, месяц, выходной, праздник
- **География:** расстояние Хаверсина, манхэттенское расстояние, направление движения, расстояние до аэропортов JFK, LGA, EWR
- **Кластеризация:** K-Means (10 кластеров) по координатам старта и финиша

## Результаты (RMSLE)

| Модель | Train | Validation | Комментарий |
|--------|:-----:|:----------:|-------------|
| Linear Regression (baseline) | 0.53 | 0.54 | |
| Polynomial Regression (deg 2) | 0.46 | 1.52 | сильное переобучение |
| Ridge Regression | 0.48 | 0.48 | |
| Decision Tree (по умолчанию) | 0.00 | 0.57 | переобучение |
| Decision Tree (глубина 8) | 0.41 | 0.43 | |
| Random Forest | 0.40 | 0.41 | |
| Gradient Boosting (sklearn) | 0.37 | 0.40 | |
| CatBoost | 0.36 | 0.40 | |
| **XGBoost** | **0.35** | **0.39** | лучший результат |

Ансамбли снизили ошибку примерно на 28% относительно линейной регрессии.

## Данные не включены

Файлы `train.csv`, `osrm_data_train.csv`, `weather_data.csv`, `holiday_data.csv` и тестовые файлы (`Project5_test_data.csv`, `Project5_osrm_data_test.csv`) слишком велики для GitHub. Исходную выборку скачайте с [Kaggle](https://www.kaggle.com/c/nyc-taxi-trip-duration/data) и положите вместе с остальными файлами в папку `data/` рядом с ноутбуком. Без них ноутбук не запустится, но результаты сохранены в его выводе.

## Запуск

```bash
pip install -r requirements.txt
jupyter notebook NYC_Taxi_Trip_Duration.ipynb
```

## Стек

pandas · numpy · scipy · scikit-learn · CatBoost · XGBoost · matplotlib · seaborn · plotly
