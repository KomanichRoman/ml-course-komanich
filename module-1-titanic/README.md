# Module 1 — Titanic: EDA и бинарная классификация

**Автор:** Команич Роман Маркович, группа АСОиУб-23-2
**Дисциплина:** Машинное обучение и искусственный интеллект
**Дата сдачи:** 2026-09-29

## 📊 Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC |
|--------|----------|-----------|--------|-----|---------|
| **Logistic Regression** | 0.8045 | 0.7833 | 0.6812 | 0.7287 | **0.8486** |
| Decision Tree | 0.7821 | 0.7419 | 0.6667 | 0.7023 | 0.8132 |
| Random Forest (бонус) | 0.7933 | 0.7857 | 0.6377 | 0.7040 | 0.8470 |

**Лучшая модель:** Logistic Regression, ROC-AUC = 0.8486.

**Время обучения:** LR — 0.038 сек, DT — 0.025 сек, RF — 0.915 сек.

## 🎯 Ключевые инсайты

- Женщины выживали в 74% случаев, мужчины — в 19%.
- Пассажиры 1-го класса — 63%, 2-го — 47%, 3-го — 24%.
- Одиночки — 30% выживаемости.
- Пассажиры из Шербура — 55%, из Куинстауна — 39%, из Саутгемптона — 34%.

## 📁 Структура модуля

module-1-titanic/
├── README.md ← этот файл
├── notebook.ipynb ← полный отчёт: 14 разделов
├── requirements.txt ← зависимости
├── data/
│ ├── train.csv ← 891 строка с целевой переменной
│ ├── test.csv ← 418 строк для submission
│ └── titanic_info.md ← описание датасета
├── models/ ← сохранённые модели и метаданные
└── examples/ ← PNG-визуализации

## 🚀 Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/username/ml-course-komanich/main/module-1-titanic"

model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/lr_model.pkl").content))
scaler = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/scaler.pkl").content))
features = requests.get(f"{BASE_URL}/models/feature_cols.json").json()
metrics = requests.get(f"{BASE_URL}/models/metrics.json").json()

print(f"ROC-AUC Logistic Regression: {metrics['logistic_regression']['roc_auc']:.4f}")