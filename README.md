# Biluthyrningssystem 🚗

A RESTful car rental API built with Java Spring Boot, developed as a group project 
during our Java Enterprise studies.

## Tech Stack
- Java 17
- Spring Boot
- Spring Security (Basic Auth)
- Spring Data JPA
- H2 (in-memory database)
- Log4j2
- JUnit 5 + Mockito

## Team & Contributions

### Lynsey Fox — Customer Management
- `Customer` entity and `Address` entity
- `CustomerController` — all customer endpoints
- `CustomerServiceImpl` — business logic, validation, authentication integration
- `CustomerRegistrationDTO`
- `ResourceNotFoundException`
- Unit tests (`CustomerServiceImplTest`)
- Integration tests (`CustomerRepositoryTest`)

### Christoffer Frisk — Car Management & Logging
- `Car` entity
- `CarController` — all car endpoints
- `CarServiceImpl` — business logic
- Log4j2 configuration (`log4j2.xml`)
- `MdcLoggingFilter` — request logging
- Unit tests (`CarServiceImplTest`)
- Integration tests (`CarRepositoryTest`)

### Niklas Einarsson — Security & Statistics
- `SecurityConfig` — Spring Security setup, role configuration
- `StatisticsController` — statistics endpoints
- `StatisticsServiceImpl` — revenue, rental duration analytics
- DTOs: `CarRevenueDTO`, `CustomerRevenueDTO`, `RentalDurationDTO`
- `DataNotFoundException`
- Unit tests (`StatisticsServiceImplTest`)
- Integration tests (`StatisticsControllerIntegrationTest`)

### Benjamin Portsmouth — Order Management
- `Orders` entity
- `OrderController` — all order endpoints
- `OrderServiceImpl` — business logic, pricing calculations
- Custom exceptions: `IncorrectCalculationException`, 
  `RepeatRequestException`, `UnauthorisedRequestException`
- Unit tests (`OrderServiceImplTest`)
- Integration tests (`OrderRepositoryTest`)

## Features
- Role-based access control (CUSTOMER / ADMIN)
- Customers log in with their personal ID number, 
  password is the last 4 digits
- Full CRUD for customers and cars
- Order management — create, cancel, view active and historical orders
- Input validation with meaningful error messages
- Statistics — revenue per car, revenue per customer, 
  average rental duration
- Logging to file on all create, update and delete operations

## API Endpoints

### Admin
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/admin/customers` | List all customers |
| GET | `/api/v1/admin/customer/{customerId}` | Get specific customer |
| POST | `/api/v1/admin/addcustomer` | Add new customer |
| DELETE | `/api/v1/admin/removecustomer/{customerId}` | Remove customer |
| GET | `/api/v1/admin/cars` | List available cars |
| GET | `/api/v1/admin/allcars` | List all cars |
| POST | `/api/v1/admin/addcar` | Add car |
| PUT | `/api/v1/admin/updatecar` | Update car |
| DELETE | `/api/v1/admin/removecar` | Remove car |
| GET | `/api/v1/admin/activeorders` | List active orders |
| GET | `/api/v1/admin/orders` | List historical orders |
| DELETE | `/api/v1/admin/removeorder` | Remove order |
| DELETE | `/api/v1/admin/removeorders-beforedate/{date}` | Remove orders before date |
| GET | `/api/v1/admin/statistics` | View statistics |

### Customer
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/cars` | List available cars |
| POST | `/api/v1/addorder` | Create order |
| PUT | `/api/v1/cancelorder` | Cancel order |
| GET | `/api/v1/activeorders` | View active orders |
| GET | `/api/v1/orders` | View order history |
| PUT | `/api/v1/updateinfo` | Update own details |

## How to Run

### Prerequisites
- Java 17
- Maven

### Steps
1. Clone the repository
```bash
   git clone https://github.com/JavaLynz/Biluthyrningssystem.git
   cd Biluthyrningssystem
```
2. Run the application
```bash
   mvn spring-boot:run
```
3. The API will start on `http://localhost:9090`
4. Test endpoints using Postman

### Default Users

**Admin**
| Username | Password |
|----------|----------|
| admin | admin |

**Customers**
| CustomerId | Password |
|------------|----------|
| 19850101-1234 | 1234 |
| 19900215-5678 | 5678 |
| 19751230-9101 | 9101 |
| 19881122-3456 | 3456 |
| 19950505-7890 | 7890 |
