# 🎓 Mini LMS — Learning Management System

A full-stack Learning Management System built with **Django + Django REST Framework + JWT Auth**.

## 📁 Project Structure

```
mini_lms_project/
├── README.md
├── requirements.txt
├── .env.example
├── .gitignore
└── backend/
    ├── manage.py
    ├── backend/               ← Django project settings
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── accounts/              ← Auth & user management
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── models.py
    │   ├── serializers.py
    │   ├── views.py
    │   └── urls.py
    ├── courses/               ← Courses, lessons, assignments, submissions
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── models.py
    │   ├── serializers.py
    │   ├── views.py
    │   ├── permissions.py
    │   └── urls.py
    └── frontend/              ← HTML/CSS/JS frontend
        ├── views.py
        ├── urls.py
        ├── templates/
        │   ├── index.html
        │   ├── courses.html
        │   └── assignments.html
        └── static/
            ├── css/
            │   └── style.css
            └── js/
                ├── auth.js
                ├── courses.js
                └── assignments.js
```

## ⚙️ Setup & Installation

### 1. Clone & create virtual environment
```bash
git clone <repo-url>
cd mini_lms_project
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure environment
```bash
cp .env.example .env
# Edit .env with your settings
```

### 4. Run migrations & seed data
```bash
cd backend
python manage.py migrate
python manage.py seed_data        # Creates demo users & courses
```

### 5. Start the server
```bash
python manage.py runserver
```

Open → http://localhost:8000

## 👤 Demo Accounts

| Role       | Username    | Password         |
|------------|-------------|------------------|
| 👑 Admin   | admin       | Admin@2025!      |
| 📚 Instructor | prof_smith | Teach#Smith99  |
| 📚 Instructor | prof_jones | Jones@Prof2025 |
| 🎒 Student | alice       | Alice#Pass1      |
| 🎒 Student | bob         | Bob#Pass1        |
| 🎒 Student | charlie     | Charlie#Pass1    |
| 🎒 Student | diana       | Diana#Pass1      |
| 🎒 Student | eve         | Eve#Pass1        |

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/accounts/register/` | Register new user |
| POST | `/api/accounts/login/` | Login & get JWT token |
| GET | `/api/accounts/me/` | Current user info |
| GET/POST | `/api/courses/` | List / Create courses |
| GET | `/api/courses/<id>/` | Course detail |
| DELETE | `/api/courses/<id>/` | Delete course |
| POST | `/api/courses/<id>/enroll/` | Enroll in course |
| DELETE | `/api/courses/<id>/unenroll/` | Unenroll |
| GET/POST | `/api/courses/<id>/lessons/` | List / Add lessons |
| GET/POST | `/api/courses/assignments/` | List / Create assignments |
| GET | `/api/courses/assignments/<id>/submissions/` | View submissions |
| POST | `/api/courses/assignments/<id>/grade/<student_id>/` | Grade submission |
| POST | `/api/courses/submit/` | Submit assignment |
| GET | `/api/courses/stats/` | Dashboard stats |
| GET | `/api/accounts/users/` | All users (admin only) |

## 🔐 Security Features

- JWT Authentication (access + refresh tokens)
- Role-based permissions (Admin / Instructor / Student)
- Password hashing (Django's PBKDF2)
- Rate limiting on login attempts
- Input validation & sanitization
- CORS configuration

## 🚀 Future Improvements
- File upload for assignments
- Email notifications
- Grading analytics dashboard
- Payment integration
- Deployment to Railway / Render / AWS
