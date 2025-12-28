# lab2-cicd

# Лабораторная работа №2 — CI/CD

Простой Python-проект с настроенными GitHub Actions для непрерывной интеграции (CI) и непрерывной доставки (CD).

## Содержание проекта

- `main.py` — простой модуль с функциями сложения и умножения
- `test_main.py` — тесты на pytest
- `requirements.txt` — зависимости (pytest)
- `.github/workflows/ci.yml` — CI: запуск тестов при каждом push и pull request
- `.github/workflows/cd.yml` — CD: создание релиза при пуше тега вида `vX.Y.Z`

## CI (непрерывная интеграция)

Workflow `CI` автоматически запускается при:
- push в ветку `main`
- открытии pull request

Действия:
1. Checkout кода
2. Установка Python 3.12
3. Установка зависимостей из `requirements.txt`
4. Запуск тестов командой `pytest -v`

Результат можно увидеть во вкладке **Actions**.

## CD (непрерывная доставка)

Workflow `CD` срабатывает при пуше тега вида `v*.*.*` (например, `v1.0.0`).

Действия:
- Создание GitHub Release с помощью действия `actions/create-release`

## Как проверить CD

1. Перейди в репозиторий → **Code** → **Releases** → **Draft a new release**
2. В поле Tag version введи, например, `v1.0.0`
3. Нажми **Publish release**

Через минуту появится релиз, а в **Actions** запустится workflow CD.

## Запуск тестов локально

```bash
pip install -r requirements.txt
pytest -v
