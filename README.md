Домашнє завдання #11
REST API для зберігання та управління контактами

> poetry init 
> poetry install

> poetry add sqlalchemy 
> poetry add fastapi
> poetry add uvicorn[standard]

> poetry add sqlalchemy 
> poetry add psycopg2 
> poetry add alembic

1. Підключення до бази даних
src/database/db.py

2. Створення моделей
src/database/models.py

> poetry run docker run --name rest_app -p 5432:5432 -e POSTGRES_PASSWORD=751953 -d postgres

3. Виконуємо міграції моделей
> poetry run alembic init migrations

migrations/env.py
    from src.database.models import Base
    from src.database.db import SQLALCHEMY_DATABASE_URL
    target_metadata = Base.metadata


poetry run alembic revision --autogenerate -m 'Init'
poetry run alembic upgrade head

4. Створюємо схеми валідації
src/schemas.py

5. CRUD операції для тегів
main.py
src/routes/contacts.py
src/repository/contacts.py

6. Перевірка застосунку
uvicorn main:app --host localhost --port 8000 --reload
http://localhost:8000/docs 

Створення контактів
Отримання списку контактів
Отримання одного контакту за ідентифікатором
Оновлення контакту за ідентифікатором
Видалення контакту за ідентифікатором
Пошук за ім'ям, прізвищем, електронною поштою, за кількістю днів до дня народження






