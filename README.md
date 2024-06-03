# Django RESTful API for User Authentication and Management

This project implements a RESTful API for user authentication and management using Django and Django REST Framework. The API includes endpoints for user registration, login, logout, and retrieving user profile information. JWT (JSON Web Tokens) is used for authentication, and the API documentation is provided using OpenAPI Specification (OAS) with Swagger UI and ReDoc.

## Features

- User registration
- User login
- User logout
- Retrieve user profile
- JWT-based authentication
- OpenAPI Specification for API documentation
- Unit tests for each endpoint

## Technologies Used

- Django
- Django REST Framework
- Django REST Framework SimpleJWT
- drf-yasg for API documentation
- SQLite for the database (default, can be changed to any other database)

## Setup Instructions

### Prerequisites

- Python 3.8+
- pip (Python package installer)

### Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/prudhvikollanapK/LensAuth.git
    cd users
    ```

2. **Create a virtual environment**:
    ```bash
    python -m venv env
    source env/bin/activate  # On Windows, use `env\Scripts\activate`
    ```

3. **Install the required packages**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Set up the database**:
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

5. **Create a superuser**:
    ```bash
    python manage.py createsuperuser
    ```

6. **Run the development server**:
    ```bash
    python manage.py runserver
    ```

7. **Access the administaor**:
    ```bash
    http://localhost:8000/admin/
    ```

### API Endpoints

1. **User Registration**: `POST /api/register/`
    - Request: 
      ```json
      {
          "username": "testuser",
          "email": "test@example.com",
          "password": "testpassword"
      }
      ```
    - Response: 
      ```json
      {
          "id": 1,
          "username": "testuser",
          "email": "test@example.com"
      }
      ```

2. **User Login**: `POST /api/login/`
    - Request: 
      ```json
      {
          "email": "test@example.com",
          "password": "testpassword"
      }
      ```
    - Response: 
      ```json
      {
          "refresh": "refresh_token",
          "access": "access_token"
      }
      ```

3. **User Logout**: `POST /api/logout/`
    - Request: 
      ```json
      {
          "refresh": "refresh_token"
      }
      ```
    - Response: `HTTP 205 Reset Content`

4. **Get User Profile**: `GET /api/profile/`
    - Headers: `Authorization: Bearer access_token`
    - Response: 
      ```json
      {
          "id": 1,
          "username": "testuser",
          "email": "test@example.com"
      }
      ```

### API Documentation

- **Swagger UI**: [http://127.0.0.1:8000/swagger/](http://127.0.0.1:8000/swagger/)
- **ReDoc**: [http://127.0.0.1:8000/redoc/](http://127.0.0.1:8000/redoc/)

### Testing

To run the unit tests for each endpoint, use the following command:
```bash
python manage.py test
```
