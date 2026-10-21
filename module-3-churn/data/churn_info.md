# Описание датасета Telco Customer Churn

**Источник:** https://www.kaggle.com/datasets/blastchar/telco-customer-churn

## Структура
- **Всего примеров:** 7043
- **Признаков:** 19 (+ `customerID` + целевая `Churn`)
- **Числовых признаков:** 3 (`tenure`, `MonthlyCharges`, `TotalCharges`)
- **Категориальных признаков:** 16
- **Тип задачи:** Бинарная классификация

## Распределение классов
- **No (остался):** 5174 (73.5%)
- **Yes (ушёл):** 1869 (26.5%)

Дисбаланс умеренный. Основная метрика — ROC-AUC.

## Ключевые признаки
- `Contract` — тип контракта (Month-to-month, One year, Two year).
- `tenure` — месяцев с компанией.
- `MonthlyCharges` — ежемесячная плата.
- `InternetService` — тип интернета (DSL, Fiber optic, No).
- `TotalCharges` — общая сумма (содержит 11 пропусков в виде пробелов).