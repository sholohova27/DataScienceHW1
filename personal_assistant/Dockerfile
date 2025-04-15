# Базовый образ
FROM python:3.12-slim

# Устанавливаем переменную среды
ENV APP_HOME=/app

# Рабочая директория внутри контейнера (тут app, записанный через переменную среды)
WORKDIR $APP_HOME

# Копируем файлы и зависимости поэтри в рабочую директорию
COPY pyproject.toml $APP_HOME/pyproject.toml
COPY poetry.lock $APP_HOME/poetry.lock

# Устанавливаем Poetry
RUN pip install poetry
# Отключаем создание виртуального окружения Poetry и оставляем только основное
RUN poetry config virtualenvs.create false && poetry install --only main

# Копируем оставшиеся файлы проекта
COPY . .

# Пробрасываем порт
EXPOSE 8000

# Команда запуска
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
