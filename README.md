# Bookstore REST API with Spring Boot

This project implements a RESTful API for an online bookstore using Spring Boot. It includes functionalities for managing books and users.

## Features

- Book management (create, read)
- User management (create, read)
- Password encryption for user security
- H2 in-memory database for data storage

## Setup and Running the Application

1. Ensure you have Java JDK 21 installed.
2. Clone the repository to your local machine.
3. Navigate to the project directory.
4. Run the application using Maven:
   ```
   ./mvnw spring-boot:run
   ```
   The application will start on `http://localhost:8080`.

## API Endpoints

### Book Management

#### Create a Book

For Windows CMD:

```shell
curl -X POST -H "Content-Type:application/json" -d "{\"title\":\"The Great Gatsby\",\"author\":\"F. Scott Fitzgerald\",\"isbn\":\"9780743273565\",\"price\":12.99,\"stock\":50}" http://localhost:8080/api/books
```

Response:

```json
{
  "id": 1,
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "isbn": "9780743273565",
  "price": 12.99,
  "stock": 50,
  "inStock": true
}
```

#### Get All Books

```shell
curl -X GET http://localhost:8080/api/books
```

#### Search Books by Title

```shell
curl -X GET http://localhost:8080/api/books/search/Great
```

#### Search Book by ISBN

```shell
curl -X GET http://localhost:8080/api/books/isbn/9780743273565
```

#### Check Book Availability

```shell
curl -X GET http://localhost:8080/api/books/availability/9780743273565
```

### User Management

#### Create a User

For Windows CMD:

```shell
curl -X POST -H "Content-Type:application/json" -d "{\"username\":\"alice\",\"email\":\"alice@uowmail.edu.au\",\"password\":\"alice123\",\"role\":\"CUSTOMER\"}" http://localhost:8080/api/users
```

Response:

```json
{
  "id": 1,
  "username": "alice",
  "email": "alice@uowmail.edu.au",
  "role": "CUSTOMER"
}
```

#### Get All Users

```shell
curl -X GET http://localhost:8080/api/users
```

#### Search User by ID

```shell
curl -X GET http://localhost:8080/api/users/1
```

#### Search User by Username

```shell
curl -X GET http://localhost:8080/api/users/username/alice
```

## Note on Security

This project implements basic security measures, including password hashing when creating the user account.

## Database

The application uses an H2 in-memory database. The database is initialized with the application startup and is destroyed when the application stops.
