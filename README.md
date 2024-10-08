# Project Sample 
# Дипломный проект профессии "Тестировщик ПО": "Автоматизация тестирования веб-сервиса для покупки тура"
В проекте представлена автоматизация тестирования веб-сервиса для покупки тура, который взаимодействует с СУБД и API банка. Веб-сервис дает возможность купить тур двумя способами:
1. Оплата по карте
2. Кредит, полученный по данным карты.

Приложение передает данные банковской карты, введенные пользователем, банковским сервисам. После чего сохраняет информацию об успешности или неуспешности платежа в базе данных

## Документация
- [План тестирования](https://github.com/MarinaaBogdanova/Graduate/blob/main/documents/Plan.md)
- [Отчет о тестировании](https://github.com/MarinaaBogdanova/Graduate/blob/main/documents/Report.md)
- [Отчет об автоматизации тестирования](https://github.com/MarinaaBogdanova/Graduate/blob/main/documents/Summary.md)


# Алгоритм запуска автотестов
## Требуемое ПО
- Git
- Java 11
- IntelliJ IDEA Community Version
- Docker Desktop
- Google Chrome
## Установка и запуск

1. Клонирование репозитория на локальный компьютер
- Склонировать на компьютер репозиторий по [адресу](https://github.com/MarinaaBogdanova/Graduate)
- Открыть локальный репозиторий в IntelliJ Idea
2. Подготовка окружения для запуска автотестов

Запустить на компьютере программу Docker Desktop
Для запуска приложения необходимо подготовить следующие Docker-контейнеры:
- Эмулятор банковского сервиса (представлен в каталоге [gate-simulator](https://github.com/MarinaaBogdanova/Graduate/tree/main/gate-simulator), для создания образа используется [Dockerfile](https://github.com/MarinaaBogdanova/Graduate/blob/main/gate-simulator/Dockerfile), запуск описан в [docker-compose.yml](https://github.com/MarinaaBogdanova/Graduate/blob/main/docker-compose.yml))
- MySQL (запуск описан в [docker-compose.yml](https://github.com/MarinaaBogdanova/Graduate/blob/main/docker-compose.yml), данные для подключения к БД описаны в [application.properties](https://github.com/MarinaaBogdanova/Graduate/blob/main/application.properties))
- PostgreSQL (запуск описан в [docker-compose.yml](https://github.com/MarinaaBogdanova/Graduate/blob/main/docker-compose.yml), данные для подключения к БД описаны в [application.properties](https://github.com/MarinaaBogdanova/Graduate/blob/main/application.properties))

**Для запуска контейнеров ввести в терминале:** `docker-compose up --build`

3. Запуск приложения
- Для запуска приложения ввести в терминале `java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar` - для работы с базой данный MySQL
- или `java "-Dspring.datasource.url=jdbc:posgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar` - для работы с базой данных PostgreSQL
- Приложение будет доступно по адресу: http://localhost:8080/
4. Запуск тестов
- Код автотестов, а также вспомогательные классы для получения данных представлены в [папке](https://github.com/MarinaaBogdanova/Graduate/tree/main/src/test/java/ru/netology/diplom/test)
- Для запуска тестов ввести в терминале

`./gradlew "-Ddb.url=jdbc:mysql://localhost:3306/app" test` - при работе с базой данных MySQL

`./gradlew "-Ddb.url=jdbc:postgresql://localhost:5432/app" test` - при работе с базой данных PostgreSQL
5. Отчет
- Для просмотра отчетности Allure Report в браузере после завершения тестов ввести в терминале `./gradlew allureserve`
