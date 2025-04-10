# Library Management System API

A robust RESTful API built with Django and Django REST Framework for managing library operations including book management, user management, and book lending services.

## Features

- **Book Management**
  - Create, read, update, and delete books
  - Track book availability
  - ISBN validation
  - Search and filter capabilities

- **User Management**
  - User registration and authentication
  - JWT-based authentication
  - User borrowing history

- **Book Lending**
  - Check out books
  - Return books
  - Automatic copy management
  - Transaction logging

## Technology Stack

- Python 3.8+
- Django 4.0+
- Django REST Framework
- JWT Authentication
- SQLite (development)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/paulokoye001/Library_Management_Lab
cd Library_Management_Lab
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Run migrations:
```bash
python manage.py makemigrations
```

4. Run migrations:
```bash
python manage.py migrate
```

5. Create a superuser:
```bash
python manage.py createsuperuser
```

6. Run the development server:
```bash
python manage.py runserver
```

## API Endpoints

### Authentication
- `POST /api/login`: Obtain JWT token

### Books
- `GET /api/books`: List all books
- `POST /api/books`: Create a new book
- `GET /api/books/{id}`: Retrieve a book
- `PUT /api/books/{id}`: Update a book
- `DELETE /api/books/{id}`: Delete a book
- `POST /api/books/{id}/checkout`: Check out a book
- `POST /api/books/{id}/return_book`: Return a book

### Users
- `GET /api/users`: List all users
- `POST /api/users`: Create a new user
- `GET /api/users/{id}`: Retrieve a user
- `PUT /api/users/{id}`: Update a user
- `DELETE /api/users/{id}`: Delete a user
- `GET /api/users/{id}/borrowing_history`: Get user's borrowing history

## API Usage Examples

### Authentication
```bash
# Obtain token
curl -X POST http://localhost:8000/api/token \
  -H "Content-Type: application/json" \
  -d '{"username": "your_username", "password": "your_password"}'
```

### Check Out a Book
```bash
curl -X POST http://localhost:8000/api/books/1/checkout \
  -H "Authorization: Bearer your_token_here"
```

### Search Books
```bash
curl http://localhost:8000/api/books/?search=python \
  -H "Authorization: Bearer your_token_here"
```

## Data Models

### Book
```python
{
    "id": int,
    "title": string,
    "author": string,
    "isbn": string,
    "published_date": date,
    "copies_available": int,
    "created_at": datetime,
    "updated_at": datetime
}
```

### User
```python
{
    "id": int,
    "username": string,
    "email": string,
    "password": string,
    "date_of_membership": date,
    "is_active": boolean
}
```

### Transaction
```python
{
    "id": int,
    "user": int,
    "book": int,
    "book_title": string,
    "username": string,
    "transaction_type": string,
    "transaction_date": datetime,
    "due_date": date
}
```

## Development

### Running Tests
```bash
python manage.py test
```

### Code Style
This project follows PEP 8 guidelines. Run flake8 to check your code:
```bash
flake8 .
```

## Author

Your Name
- Email: paulokoye4sealx@gmail.com
- GitHub: [paulokoye001](https://github.com/paulokoye001/Library_Management_Lab)
