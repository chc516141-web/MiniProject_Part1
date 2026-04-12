# Shopping List Management System

This repository contains a full-stack application developed as a preparatory project for a practicum. The system manages a Shopping List using a three-layer architecture, ensuring a complete separation between data, logic, and presentation.

---

## Architecture and Technologies
The application is built with a decoupled architecture as follows:
* Frontend: Developed with Angular to manage the user interface and logic.
* Backend: A .NET Web API acting as a generic routing conduit between the interface and the database.
* Database: SQL Server containing all business logic within Stored Procedures.

---

## Technical Implementation

### 1. Database Layer (SQL Server)
The database design is based on three relational tables:
* Items Table (Main): Stores shopping items with fields including Id, Name, Description, StatusId, and CreatedAt.
* Status Table: A lookup table for item states.
* Secondary Table: An additional table to organize the shopping list data.

Stored Procedures (SPs):
All data operations are handled strictly via Stored Procedures:
* Create: Adds new items to the list.
* Update: Modifies existing records.
* GetById: Retrieves specific item details using JOIN to fetch readable status names.
* GetAll and Search: Provides a full list with free-text search functionality on titles.
* GetByStatus: Custom filter logic for better organization.

### 2. Backend API (.NET)
The backend is implemented as a generic pipe.
* Generic Controller: The API uses a single endpoint: POST /api/exec.
* Request Model: The API accepts a request model containing the procedureName and a dictionary of parameters.
* Logic: There is no business logic in the API; it serves only to route requests to the SQL Server.
* Testing: The API was verified using Swagger and Postman prior to integration.

### 3. Frontend Layer (Angular)
The application interface was built from scratch:
* Centralized Service: A single Angular Service manages all communication through the generic API endpoint.
* Reactive Forms: Used for data entry and validation when creating or editing items.
* Key Screens:
    * List Screen: Displays all items with a search bar and navigation to view or edit modes.
    * Management Screen: A dedicated form for creating and updating shopping list items.
    * Details Screen: Displays full item data, converting technical IDs into user-friendly text.

---

## Setup and Execution
1. Database: Run the SQL scripts to initialize tables and Stored Procedures.
2. API: Configure the connection string in the .NET project and launch the server.
3. Client: Install dependencies via npm and run the application using the Angular CLI.

---
Developed as part of the Practicum Prep Project.
