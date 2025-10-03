# E-Commerce Java Microservices

This repository implements a microservice-based e-commerce backend in Java using Spring Boot. It is designed to demonstrate a modular, scalable architecture suitable for handling users, products, and orders, orchestrated by an API Gateway and serviced through a Eureka discovery server.

## Architecture Overview

The system is composed of multiple microservices:
- **API Gateway** (`APIGATEWAY`): Central entry point for all client requests, handling routing, logging, and fallback responses.
- **User Service** (`Userservice`): Manages user data and authentication.
- **Product Service** (`ProductService`): Handles product inventory, creation, deletion, and updates.
- **Order Service** (`Orders`): Manages customer orders and order processing.
- **Eureka Discovery Server** (`EurekaServer`): Enables dynamic service registration and discovery.

Each microservice is a standalone Spring Boot application and communicates with others via REST APIs routed through the API Gateway.

## Key Features

- **Microservice Architecture**: Each domain (users, products, orders) is isolated for scalability and independent deployment.
- **API Gateway**: Centralized request routing, logging (`LoggingGlobalFilter`), and fallback controller for service availability.
- **Service Discovery**: Eureka server for dynamic registration and lookup of services.
- **CORS Configuration**: All services are CORS-enabled for local development via the Gateway.
- **Persistence Layer**: Uses Spring Data JPA repositories (e.g., `ProductRepository`, `OrderRepository`, `UserRepository`) for data access.
- **Validation & Exception Handling**: Domain models like `Product` include validation annotations; global exception handler for REST errors.

## Directory Structure

```
APIGATEWAY/
  src/main/java/com/apigateway/main/...
  - ApigatewayApplication.java
  - LoggingGlobalFilter.java
  - FallbackController.java

ProductService/
  src/main/java/com/firstproject/productservice/...
  - ProductServiceApplication.java
  - service/ProductService.java
  - model/Product.java
  - repo/ProductRepository.java
  - CorsConfig.java

Userservice/
  src/main/java/com/usermicroservice/main/...
  - UserserviceApplication.java
  - repository/UserRepository.java
  - CorsConfig.java
  - GlobalExceptionHandler.java

Orders/
  src/main/java/com/firstproject/productservice/...
  - ProductService1Application.java
  - repository/OrderRepository.java
  - CorsConfig.java

EurekaServer/
  src/main/java/com/firstproject/productservice/...
  - ProductServiceApplication.java
```

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/Aditya251610/e-commerce-java.git
   ```

2. **Run Eureka Server**
   - Navigate to `EurekaServer` and start the Spring Boot application.

3. **Run Microservices**
   - Start each of the `Userservice`, `ProductService`, and `Orders` applications.
   - Ensure each service registers with Eureka.

4. **Run API Gateway**
   - Start the `APIGATEWAY` application. All requests should be routed via the gateway.

5. **Access Endpoints**
   - Use tools like Postman or curl to interact with the API Gateway endpoints.

## Technologies Used

- Java
- Spring Boot
- Spring Cloud Gateway
- Spring Data JPA
- Eureka Discovery Server
- Maven

## Contributing

Feel free to submit issues or pull requests to enhance features, add documentation, or fix bugs.

## License

This project is licensed under the MIT License.
