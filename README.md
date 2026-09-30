☕ Chai Point Menu API

A read-only FastAPI backend for Chai Point, Bengaluru, designed so kiosk displays and mobile applications can fetch the latest menu without directly hitting a database.

🎯 Problem Statement

Chai Point, Bengaluru wants a read-only menu API so that its kiosk displays and mobile apps can fetch the latest menu data through HTTP APIs.

For this project, the menu is stored in memory in data.py, so no database is required.

🏗️ Solution Architecture



Architecture Flow

Client (App / Kiosk / Mobile)
              ↓
        FastAPI Server
              ↓
        In-memory Menu Data
              ↓
        JSON Response

Available API Operations

Method

Endpoint

Purpose

GET

/

Welcome message

GET

/menu

Get all menu items

GET

/menu?category=chai

Filter menu by category

GET

/menu/{item_id}

Get a single menu item

🛠️ Tech Stack

Python

FastAPI

Pydantic

Uvicorn

In-memory Python data structure

Swagger/OpenAPI documentation

📁 Project Structure

Chai-Menu/
│
├── main.py
├── models.py
├── data.py
├── requirements.txt
├── architecture.jpg
├── .gitignore
└── README.md

File Responsibilities

data.py

Contains the menu data.

Stores menu items in memory.

models.py

Defines Pydantic models.

Validates API response data.

main.py

Creates the FastAPI application.

Defines API routes.

Handles query parameters, path parameters and HTTP errors.

requirements.txt

Contains the Python dependencies required to run the project.

🚀 How to Run

1. Clone the repository

git clone <your-repository-url>
cd Chai-Menu

2. Create a virtual environment

Windows PowerShell:

python -m venv venv

Activate it:

.env\Scripts\Activate.ps1

3. Install dependencies

pip install -r requirements.txt

4. Start the FastAPI server

uvicorn main:app --reload

The API will be available at:

http://127.0.0.1:8000

Interactive Swagger documentation:

http://127.0.0.1:8000/docs

📌 Example API Requests

Get all menu items

GET /menu

Filter by category

GET /menu?category=chai

Get one menu item

GET /menu/4

Example response:

{
  "id": 4,
  "name": "Adrak Chai",
  "category": "chai",
  "price": 10.0,
  "description": "Extra ginger chai for cold evenings",
  "available": true
}

📚 What I Learned

Through this project, I learned and practiced:

Creating a FastAPI application

Creating the FastAPI app instance.

Running the application using Uvicorn.

Understanding the basic request-response flow.

Path Parameters

Using endpoints such as /menu/{item_id}.

Receiving and validating values from the URL.

Query Parameters

Using query parameters such as ?category=chai.

Filtering API data based on query parameters.

Pydantic Response Models

Creating BaseModel classes.

Validating API response data.

Using response_model with FastAPI.

HTTP Exception Handling

Using HTTPException.

Returning meaningful 404 Not Found errors when an item or category does not exist.

API Documentation

Exploring FastAPI's automatically generated Swagger UI.

Understanding how OpenAPI documentation is generated.

Debugging

Understanding Pydantic validation errors.

Debugging field-name mismatches such as Price vs price.

Understanding how indentation can affect Python control flow.

Reading Uvicorn/FastAPI error traces to locate the source of an error.

Git & GitHub

Initializing a Git repository.

Creating commits.

Connecting a local project to GitHub.

Using .gitignore to keep venv and Python cache files out of the repository.

💡 Key Takeaway

This project helped me understand the complete basic flow of a REST API:

Client
  ↓
HTTP Request
  ↓
FastAPI Route
  ↓
Query / Path Parameter
  ↓
Data Processing
  ↓
Pydantic Validation
  ↓
JSON Response

This project is intentionally backend-only because its purpose is to build and expose a menu API. A frontend is not required for the API itself.

🔮 Possible Future Improvements

Connect the API to a real database.

Add POST/PUT/DELETE endpoints if the application later needs menu management.

Add authentication and authorization.

Add automated tests.

Add a frontend/mobile client that consumes the API.

Deploy the API to a cloud platform.
