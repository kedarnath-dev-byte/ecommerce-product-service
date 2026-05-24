# ecommerce-product-service

A Spring Boot backend service for ecommerce product and category management. The project implements REST APIs for products, categories, cart lookup integration, persistence, caching, DTO mapping, and centralized exception handling.

## Portfolio Role

This repository is maintained by Mamani Kedarnath as a backend portfolio project focused on Spring Boot service design, REST APIs, persistence, caching, and clean project documentation.

## Tech Stack

- Java 17
- Spring Boot 3.2
- Spring Web
- Spring Data JPA
- PostgreSQL / MySQL
- Redis cache
- Maven
- Lombok
- H2 for tests
- FakeStore API integration

## Features

- Product CRUD APIs
- Category CRUD-style service layer
- Product search by name
- Product filtering by price range
- DTO mapping between entities and API responses
- Centralized controller exception handling
- External FakeStore API client integration
- Redis caching for product reads
- Database persistence using Spring Data JPA
- Separate controller, service, repository, mapper, DTO, entity, client, and exception packages

## API Overview

```text
GET    /product
GET    /product/{id}
POST   /product
PUT    /product/{id}
DELETE /product/{id}
GET    /product/name/{productName}
GET    /product/{min}/{max}
```

## Architecture

```text
Controller Layer
  ProductController
  CategoryController
  CartController

Service Layer
  ProductService / ProductServiceImpl
  CategoryService / CategoryServiceImpl
  FakeStoreProductServiceImpl

Repository Layer
  ProductRepository
  CategoryRepository

Integration Layer
  FakeStoreClient

Mapping Layer
  ProductEntityDTOMapper
  CategoryEntityDTOMapper

Domain Layer
  Product
  Category
  BaseModel
```

## Configuration

The service expects database settings through environment variables:

```bash
PRODUCTSERVICE_JDBC_URL=jdbc:postgresql://localhost:5432/productservice
PRODUCTSERVICE_JDBC_USERNAME=your_username
PRODUCTSERVICE_JDBC_PASSWORD=your_password
```

Redis is configured at:

```text
localhost:6379
```

FakeStore API configuration is stored in `src/main/resources/application.properties`.

## How to Run

1. Start PostgreSQL or MySQL and create the product service database.
2. Start Redis locally on port `6379`.
3. Set the required database environment variables.
4. Run the application:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

## What This Project Demonstrates

- REST API design with Spring Boot
- Entity-to-DTO mapping
- JPA repository usage
- External API integration
- Redis caching with `@Cacheable`
- Exception handling with controller advice
- Practical backend layering for maintainable services

## Future Improvements

- Add Swagger/OpenAPI documentation
- Add Docker Compose for database and Redis
- Add authentication and authorization
- Add validation annotations for request DTOs
- Add pagination and sorting for product listing
- Expand integration tests for controller and service behavior
