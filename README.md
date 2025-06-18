# IQ_Test – Онлайн IQ тест с Java Spring Boot и MySQL (Dockerized)

Това е уеб приложение за IQ тест, разработено със Spring Boot и MySQL. Приложението е напълно контейнеризирано чрез Docker и може да бъде стартирано с една команда.

---

## Технологии

- Java 21 (Spring Boot)
- Maven
- MySQL 8
- HTML (Thymeleaf шаблони)
- Docker & Docker Compose

---

## Стартиране с Docker Compose

### 1. Изисквания

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

### 2. Команда за стартиране

docker compose up --build
Това ще изгради приложението и ще стартира базата данни и уеб сървъра.

3. Достъп до приложението
След като всичко се стартира успешно, отвори:

arduino
Copy
Edit
http://localhost:8080
Съдържание на проекта
plaintext
Copy
Edit
IQ_Test/
├── docker-compose.yml
├── Dockerfile
├── mysql/
│   ├── conf.d/
│   ├── data/
│   └── init.sql              # SQL скрипт за създаване и попълване на таблица questions
├── src/
│   └── main/
│       ├── java/com/example/IQ_Test/
│       │   ├── config/
│       │   ├── controller/
│       │   ├── entity/
│       │   ├── model/
│       │   ├── repository/
│       │   ├── service/
│       │   └── IqGeneratorApplication.java
│       └── resources/
│           ├── templates/    # HTML страници: login, register, test, results и др.
│           ├── static/
│           └── application.properties
├── pom.xml
 MySQL База данни
Име на база: iqtest

Потребител: root

Парола: rootpass

Таблица questions се създава автоматично от init.sql при първоначално стартиране

SQL скрипт добавя 18 въпроса с логически и числови задачи

 Основни HTML страници
/login – Вход

/register – Регистрация

/test – Старт на теста

/results – Резултати

/home – Начална страница

/error – Грешки

 Променливи на средата (в docker-compose.yml)
yaml
Copy
Edit
SPRING_DATASOURCE_URL=jdbc:mysql://mysql:3306/iqtest?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
SPRING_DATASOURCE_USERNAME=root
SPRING_DATASOURCE_PASSWORD=rootpass
SPRING_JPA_HIBERNATE_DDL_AUTO=update
 Тестови въпроси
Тестът включва логически, математически и езикови въпроси като:

Последователности (напр. 2, 4, 8, 16, ___?)

Аналогии (напр. Книга : Четене :: Химикал : ___?)

Пространствено мислене (фигури и ротации)

Изключения в група (напр. Ябълка, Круша, Морков, Слива)

 Docker образи
Можеш да билднеш локален образ с:

bash
Copy
Edit
docker build -t iq-test-app .
