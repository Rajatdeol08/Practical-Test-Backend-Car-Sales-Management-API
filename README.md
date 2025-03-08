# Car Sales Management API

## A .NET 8 Web API with ADO.NET for Car Models, Sales, and Salesman Management

### Features

- ✅ Full **CRUD operations** for Car Models, Sales, and Salesmen
- ✅ **Sales Commission Calculation API**
- ✅ **ADO.NET Database Connectivity** (No Entity Framework)
- ✅ **Swagger UI for API Testing**
- ✅ **Centralized Error Handling Middleware**

---

## Project Structure

```
CarSalesAPI
│── Controllers            # API Controllers
│   ├── CarModelController.cs
│   ├── SalesController.cs
│   ├── SalesmanController.cs
│
│── Models                 # Data Models
│   ├── CarModel.cs
│   ├── Sales.cs
│   ├── Salesman.cs
│
│── Data                   # Database Repositories
│   ├── CarModelRepository.cs
│   ├── SalesRepository.cs
│   ├── SalesmanRepository.cs
│
│── Interfaces             # Interfaces for Repositories
│   ├── ICarModelRepository.cs
│   ├── ISalesRepository.cs
│   ├── ISalesmanRepository.cs
│
│── DTOs                   # Data Transfer Objects
│   ├── SalesCommissionDTO.cs
│
│── Middlewares            # Custom Middleware for Error Handling
│
│── appsettings.json       # Configuration File
│── Program.cs             # Application Entry Point
```

---

## Prerequisites

- **Visual Studio 2022**
- **.NET 8 SDK**
- **SQL Server**
- **Postman or Swagger UI**

---

## Getting Started

### Clone the Repository

```sh
git clone https://github.com/your-username/carsalesapi.git
cd car-sales-api
```

### Configure the Database

1. Open **SQL Server Management Studio (SSMS)**.
2. Create a new database:
   
   CREATE DATABASE CarSalesDB;
   USE CarSalesDB;

3. Run the following **SQL script** to create tables:
   
   CREATE TABLE CarModels (
       Id INT IDENTITY(1,1) PRIMARY KEY,
       Brand NVARCHAR(50) NOT NULL,
       Class NVARCHAR(50) NOT NULL,
       ModelName NVARCHAR(100) NOT NULL,
       ModelCode NVARCHAR(10) NOT NULL CHECK (ModelCode LIKE '[A-Za-z0-9]%'),
       Description NVARCHAR(MAX) NOT NULL,
       Features NVARCHAR(MAX) NOT NULL,
       Price DECIMAL(18,2) NOT NULL,
       DateOfManufacturing DATETIME NOT NULL,
       Active BIT NOT NULL,
       SortOrder INT NOT NULL,
       CreatedAt DATETIME DEFAULT GETDATE()
   );

   CREATE TABLE Sales (
       Id INT IDENTITY(1,1) PRIMARY KEY,
       Salesman NVARCHAR(100) NOT NULL,
       Class NVARCHAR(10) NOT NULL,
       Brand NVARCHAR(50) NOT NULL,
       CarsSold INT NOT NULL,
       TotalSaleAmount DECIMAL(18,2) NOT NULL
   );

   CREATE TABLE Salesman (
       Id INT IDENTITY(1,1) PRIMARY KEY,
       Name NVARCHAR(100) NOT NULL,
       LastYearTotalSales DECIMAL(18,2) NOT NULL
   );

###  Update Database Connection in 

"ConnectionStrings": {
  "DefaultConnection": "Server=YOUR_SERVER;Database=CarSalesDB;Trusted_Connection=True;TrustServerCertificate=True;"
}

Replace `YOUR_SERVER` with your actual SQL Server name.


## Running the API

### Using Visual Studio

1. Open **Visual Studio 2022**.
2. Click **Open a project** → Select the `CarSalesAPI` folder.
3. Press `F5` or click **Run** to start the API.

### Using .NET CLI

dotnet run

## API Endpoints

### Car Models

| **Operation**   | **API Route**        | **Method** |
| Get All Models  | `/api/carmodel`      | `GET`      |
| Get Model by ID | `/api/carmodel/{id}` | `GET`      |
| Add Model       | `/api/carmodel`      | `POST`     |
| Update Model    | `/api/carmodel`      | `PUT`      |
| Delete Model    | `/api/carmodel/{id}` | `DELETE`   |

### Sales

| **Operation**  | **API Route**     | **Method** |
| Get All Sales  | `/api/sales`      | `GET`      |
| Get Sale by ID | `/api/sales/{id}` | `GET`      |
| Add Sale       | `/api/sales`      | `POST`     |
| Update Sale    | `/api/sales`      | `PUT`      |
| Delete Sale    | `/api/sales/{id}` | `DELETE`   |

### Salesman

| **Operation**      | **API Route**        | **Method** |
| Get All Salesmen   | `/api/salesman`      | `GET`      |
| Get Salesman by ID | `/api/salesman/{id}` | `GET`      |
| Add Salesman       | `/api/salesman`      | `POST`     |
| Update Salesman    | `/api/salesman`      | `PUT`      |
| Delete Salesman    | `/api/salesman/{id}` | `DELETE`   |

### Sales Commission Report

| **Operation**               | **API Route**                  | **Method** |
| Get Sales Commission Report | `/api/sales/commission-report` | `GET`      |


## Testing the API in Swagger

1. **Run the API**
2. Open Swagger UI in your browser:
   http://localhost:5066/swagger

## Error Handling

- The project includes centralized error handling using middleware.
- If an error occurs, you will receive a structured JSON response:
  
{
  "message": "Internal Server Error",
  "details": "Error details..."
}

## Summary

- Complete CRUD Operations
- Sales Commission API
- Swagger API Documentation
- Centralized Error Handling
- Runs on .NET 8 & SQL Server
- Easily Deployable

