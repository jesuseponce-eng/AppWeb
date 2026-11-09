# School System – Project (Frontend + Backend)

## 📖 General Description
The School System project is an academic platform focused on providing accessible school content, event management, and user administration through role-based authentication.

The system handles backend CRUD operations via a Django REST API, integrated with a local development environment and prepared for professional deployment. Meanwhile, the WebApp (frontend design) was built using Angular, resulting in an attractive, 100% responsive, and user-friendly web application.

## ✨ Core Features

- *Authentication & Session:* Email/password login; token and role response; frontend cookie management; token-invalidating logout.
- *Users:* CRUD operations for administrators, teachers, and students with specific validations.
- *Events:* Creation, listing, editing, and deletion including date/time, target audience, responsible person, capacity, and description.
- *Metrics:* Charts displaying totals grouped by user role.
- *Navigation:* Authentication and dashboard layouts; public and private route protection.

## 📋 Prerequisites

- *Node.js:* Version 18 or higher (includes npm)
- *Angular CLI:* Version 16.2.11 (via npx)
- *Python:* 3.12
- *MySQL:* 5.7 / 8.0

## 🛠 Technologies

### Frontend
- Angular 16
- Angular Material & CDK
- ngx-cookie-service
- ng2-charts / chart.js / chartjs-plugin-datalabels
- ngx-mask
- ngx-material-timepicker

### Backend
- Django 5
- Django REST Framework (DRF)
- django-cors-headers
- django-filter
- pymysql
- rest_framework.authtoken

## 📂 Project Structure

- *Frontend (Angular):* dev-sistema-escolar-webapp_fdrd
- *Backend (Django):* dev_sistema_escolar_api_fdrd

---

## 🚀 Getting Started

> *Nota:* Both the frontend and backend must be run separately (in different terminal windows). Navigate to the respective folder to run each local server(localhost).
> * *Backend:* Puerto 8000
> * *Frontend:* Puerto 4200

## 1. Backend (Django)

*Environment Setup:*

# Create the virtual environment
python -m venv .venv

# Activate the virtual environment 
.\.venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Create migrations:
python manage.py makemigrations

# Apply migrations to the database:
python manage.py migrate

# Finally, run the server:
python manage.py runserver
URL: http://127.0.0.1:8000/

###Database Configuration.
# Create the database in MySQL: 
CREATE DATABASE dev_sistema_escolar_db CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;

#Client configuration (my.cnf / settings):
host=127.0.0.1
port=3306
database=dev_sistema_escolar_db
user=root
password=
default-character-set=utf8mb4

###Main Endpoints
dev_sistema_escolar_api/dev_sistema_escolar_api/urls.py:13-48
Django Admin: GET /admin-django/

API Version: GET /version/

####Admins:
  * Create: POST /admin/
  * Delete: DELETE /admin/<id>/
  * List: GET /lista-admins/
  * Total Users: GET /total-usuarios/

####Students (Alumnos):
  * Create: POST /alumnos/
  * Delete: DELETE /alumnos/<id>/
  * List: GET /lista-alumnos/
  
####Teachers (Maestros):
  * Create: POST /maestros/
  * Delete: DELETE /maestros/<id>/
  * List: GET /lista-maestros/
  
####Auth:
  * Login: POST /login/
  * Logout: POST /logout/
  
####Events:
  * Create: POST /eventos/
  * Delete: DELETE /eventos/<id>/
  * List: GET /lista-eventos/

##2.Frontend (Angular)

###*Version Management and Dependencies*
bash
# Select Node version with NVM
nvm ls
nvm use 22.14.0

# Install project dependencies
npm install

###*Execution*
bash
# Run the development server
ng serve
URL de la WebApp: http://localhost:4200/

##🛣 Frontend Routes
Defined in: src/app/app-routing.module.ts

####Public:
-login
-registro-usuarios
-registro-usuarios/:rol/:id

####Dashboard:
-home
-administrador
-alumnos
-maestros
-graficas
-eventos
-registro-eventos
-registro-eventos/:id

##⚠ Important Notes
-Ensure the backend is running at http://127.0.0.1:8000 for the WebApp to communicate correctly with ng serve
-Use Authorization: Bearer <token> in protected requests.
-For production, update environment.prod.ts and configure ALLOWED_HOSTS / CORS in the API.
