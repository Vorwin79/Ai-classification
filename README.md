# Ai-classification
Задача №3: определить тип самолета по фото с помощью локальных мультимодальных моделей. Сравниваются две модели: `llava` и `minicpm-v4.5`.

## Технологии
- Ollama (локальный запуск моделей)
- Python: `ollama`, `pandas`, `scikit-learn`

## Выборка
30 фото: 15 военных и 15 гражданских. 
Включены сложные случаи (военно-транспортные, необычные ливреи).
Разметка в именах файлов: `_x` — военный (M), `_y` — гражданский (C).

## Как запустить
1. Установить [Ollama](https://ollama.com/download).
2. Скачать модели:
   ```bash
   ollama pull llava
   ollama pull minicpm-v4.5
Установить зависимости:

bash
pip install -r requirements.txt
Открыть aircraft_classification.ipynb и выполнить ячейки.

Результаты
Модель	Valid	Accuracy	Precision	Recall	F1
llava	30/30	0.9000	0.9286	0.8667	0.8966
minicpm-v4.5	30/30	0.9000	0.8333	1.0000	0.9091
Precision, Recall и F1 — для класса «военный» (M).

Ошибки
llava (3): 2 военных назвала гражданскими, 1 гражданский — военным.

minicpm-v4.5 (3): 3 гражданских назвала военными.

Файлы
aircraft_classification.ipynb — код

results_both_models.csv — предсказания моделей

final_report.txt — отчет с метриками

planes/ — картинки

Вывод
Обе модели показали Accuracy 0.9 (по 3 ошибки). llava лучше находит гражданские,
