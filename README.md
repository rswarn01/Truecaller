# Truecaller
# Truecaller-like Django REST API

This project implements a Django REST API similar to popular caller identification apps. The API allows users to register, manage their contacts, mark numbers as spam, and search for users or numbers in the global database.

## Features

- User registration with phone number and name (email is optional).
- User authentication using token-based authentication.
- Contacts management (add, list).
- Spam reporting for phone numbers.
- Search by name or phone number.
- Token authentication for all endpoints.

## Folder Structure

truecaller/
│
├── manage.py
├── truecaller/
│ ├── init.py
│ ├── settings.py
│ ├── urls.py
│ ├── wsgi.py
│
├── api/
│ ├── init.py
│ ├── admin.py
│ ├── apps.py
│ ├── models.py
│ ├── serializers.py
│ ├── urls.py
│ ├── views.py
│ ├── tests.py
│
├── users/
│ ├── init.py
│ ├── admin.py
│ ├── apps.py
│ ├── models.py
│ ├── serializers.py
│ ├── urls.py
│ ├── views.py
│ ├── tests.py
│
├── contacts/
│ ├── init.py
│ ├── admin.py
│ ├── apps.py
│ ├── models.py
│ ├── serializers.py
│ ├── urls.py
│ ├── views.py
│ ├── tests.py
│
└── spam/
├── init.py
├── admin.py
├── apps.py
├── models.py
├── serializers.py
├── urls.py
├── views.py
├── tests.py

bash
Copy code

## Setup Instructions

1. **Clone the repository:**

git clone https://github.com/rswarn01/Truecaller.git
cd Truecaller

Create a virtual environment:
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`


2. **Install dependencies:**
pip install -r requirements.txt


3. **Set up the database:**
python manage.py makemigrations
python manage.py migrate

4. **Create a superuser:**
python manage.py createsuperuser

5. **Populate the database with sample data:**
python manage.py populate_data

6. **Run the development server:**
python manage.py runserver


# API Endpoints:
# User Registration
URL: /api/users/register/
Method: POST
Payload:
json
Copy code
{
  "phone_number": "1234567890",
  "name": "John Doe",
  "password": "password123"
}


# User Login
URL: /api/users/login/
Method: POST
Payload:
{
  "phone_number": "1234567890",
  "password": "password123"
}
Response:
json
Copy code
{
  "token": "your-auth-token"
}


# Create Contact
URL: /api/contacts/
Method: POST
Headers: Authorization: Token your-auth-token
Payload:
json
{
  "name": "Jane Doe",
  "phone_number": "0987654321"
}


List Contacts
URL: /api/contacts/
Method: GET
Headers: Authorization: Token your-auth-token


# Report Spam
URL: /api/spam/
Method: POST
Headers: Authorization: Token your-auth-token
Payload:
json
{
  "phone_number": "0987654321"
}


# Search by Name
URL: /api/search/name/
Method: GET
Headers: Authorization: Token your-auth-token
Query Params: name=<search_query>


# Search by Phone Number
URL: /api/search/phone/
Method: GET
Headers: Authorization: Token your-auth-token
Query Params: phone_number=<search_query>

Ensure that you have the Faker library installed for the populate_data.py script. If not, install it using:
pip install faker
Adjust the settings in settings.py as needed for your environment.

This project is designed to be a starting point. You can extend its functionalities as required.
