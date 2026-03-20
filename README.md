# Scooter Rental DB — LiquiBase Lab

Лабораторна робота №3 з дисципліни ДРБД.
Тема: «Оренда скутерів». Група ПЗПІ-22-8.

## Попередні вимоги

- Java 11+
- Maven 3.8+
- Microsoft SQL Server (локальний або Docker)

## Налаштування підключення

1. Скопіюйте файли прикладів і заповніть паролі:

```bash
cp liquibase.properties.example liquibase.properties
cp liquibase-init-db.properties.example liquibase-init-db.properties
```

2. Відредагуйте `liquibase.properties` та `liquibase-init-db.properties` — вкажіть свій пароль SA.

## Запуск

### Крок 1 — Створити базу даних

```bash
mvn liquibase:update -P init-db
```

### Крок 2 — Накатити всі міграції таблиць та початкові дані

```bash
mvn liquibase:update
```

### Відкат

```bash
# Відкатити останній changeSet
mvn liquibase:rollback -Dliquibase.rollbackCount=1

# Відкатити всі зміни до певного тегу
mvn liquibase:rollback -Dliquibase.rollbackTag=v1.0
```

## Структура проекту

```
Scooter_Rental_DB/
├── pom.xml                                  Maven + LiquiBase plugin
├── db.changelog-master.xml                  Master changelog (включає всі інші)
├── liquibase.properties                     Підключення до scooter_rental (git-ignored)
├── liquibase-init-db.properties             Підключення до master для init (git-ignored)
├── liquibase.properties.example             Шаблон (комітиться)
├── liquibase-init-db.properties.example     Шаблон (комітиться)
└── src/main/resources/db/changelogs/
    ├── db-init-changelog.xml                Створення БД scooter_rental
    ├── init/                                Міграції структури таблиць
    │   ├── tables-init.xml                  Сервісна таблиця-реєстр
    │   ├── roles-init.xml
    │   ├── users-init.xml
    │   ├── user_roles-init.xml
    │   ├── locations-init.xml
    │   ├── scooter_models-init.xml
    │   ├── scooters-init.xml
    │   ├── rental_statuses-init.xml
    │   ├── rentals-init.xml
    │   ├── payment_methods-init.xml
    │   └── payments-init.xml
    └── data/                                Початкові дані (seed)
        ├── roles-data-V001.xml
        ├── rental_statuses-data-V001.xml
        ├── payment_methods-data-V001.xml
        ├── scooter_models-data-V001.xml
        └── users-data-V001.xml
```

## Команда

| Розробник | Username | Сервіси |
|---|---|---|---|
| Судакова А.Д. | avokadus725 | USER_SERVICE, SCOOTER_SERVICE |
| Олеся О.О. | OlesiaShevchenko245 | RENTAL_SERVICE,PAYMENT_SERVICE |

