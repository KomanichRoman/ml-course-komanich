# 📉 Module 3 — Customer Churn: Ансамблевые методы

**Автор:** Команич Роман Маркович, АСОиУб-23-2  
**Дата:** 2026-21-10  

## 📊 Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC | Время |
|--------|----------|-----------|--------|-----|---------|-------|
| Random Forest | 0.772 | 0.554 | 0.727 | 0.629 | 0.8409 | 0.883 сек |
| XGBoost | 0.755 | 0.529 | 0.698 | 0.602 | 0.8288 | 0.227 сек |
| LightGBM | 0.760 | 0.534 | 0.754 | 0.625 | 0.8375 | 0.199 сек |
| CatBoost | 0.749 | 0.519 | 0.743 | 0.611 | 0.8409 | 0.544 сек |
| **LightGBM (Optuna)** | **0.740** | **0.507** | **0.797** | **0.620** | **0.8468** | — |

## 📁 Структура модуля

```
module-3-churn/
├── README.md                    ← описание модуля
├── notebook.ipynb               ← полный отчёт: 14 разделов
├── requirements.txt             ← зависимости
├── data/
│   ├── telco_churn.csv          ← исходный датасет
│   └── churn_info.md            ← описание датасета
├── models/                      ← сохранённые модели и метаданные
│   ├── best_model.pkl           ← LightGBM (Optuna), лучшая модель
│   ├── rf_model.pkl             ← Random Forest
│   ├── xgb_model.pkl            ← XGBoost
│   ├── lgbm_model.pkl           ← LightGBM (baseline)
│   ├── cat_model.pkl            ← CatBoost
│   ├── label_encoders.pkl       ← словарь кодировщиков (15 шт.)
│   ├── feature_cols.json        ← список признаков
│   └── metrics.json             ← метрики всех моделей
└── examples/                    ← визуализации
    ├── eda_plots.png
    ├── feature_importance_lgbm.png
    ├── feature_importance_rf.png
    ├── roc_curves.png
    ├── shap_dependence.png
    ├── shap_summary_bar.png
    ├── shap_summary_dot.png
    └── shap_waterfall.png
```

## 🚀 Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/KomanichRoman/ml-course-komanich/main/module-3-churn"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content))