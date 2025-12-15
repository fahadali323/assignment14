# 📐 FastAPI Calculator Application

A full-stack **FastAPI** application that provides:
- User authentication (registration & login)
- Secure JWT-based authorization
- CRUD operations for calculator records
- PostgreSQL database integration
- Redis-backed token blacklist (async)
- Automated testing (unit, integration, E2E)
- Dockerized deployment
- Playwright end-to-end tests

---

## Screenshots
1. GitHub Actions Workflow: Screenshot showing a successful run of the GitHub Actions workflow.
![alt text](./images/image.png)

2. Docker Hub Deployment: Screenshot demonstrating the Docker image has been successfully pushed to Docker Hub.
![alt text](./images/image-1.png)

3. Application Functionality: Screenshots of the front-end performing BREAD
![alt text](./images/image-2.png)
![alt text](./images/image-3.png)
![alt text](./images/image-4.png)
![alt text](./images/image-5.png)
![alt text](./images/image-6.png)
Deletion: 
 ![alt text](./images/image-7.png)
 ![alt text](./images/image-8.png)
Edit:
 ![alt text](./images/image-9.png)
 ![alt text](./images/image-10.png)
 ![alt text](./images/image-11.png)

## 🧱 Tech Stack

- **Backend:** FastAPI
- **Database:** PostgreSQL
- **ORM:** SQLAlchemy
- **Auth:** JWT (python-jose, passlib)
- **Cache / Blacklist:** Redis (async)
- **Testing:** pytest, Playwright
- **Containerization:** Docker & Docker Compose
- **Python:** 3.10 / 3.12 compatible

---

## 📁 Project Structure

```
app/
├── auth/               # Authentication, JWT, Redis blacklist
├── core/               # App configuration & settings
├── database.py         # Database engine & session
├── database_init.py    # Initial DB setup
├── main.py             # FastAPI app & routes
├── models/             # SQLAlchemy models
├── operations/         # Calculator logic
├── schemas/            # Pydantic schemas
tests/
├── unit/               # Unit tests
├── integration/        # Integration tests
├── e2e/                # End-to-end tests
Dockerfile
docker-compose.yml
requirements.txt
README.md
```

---

## 🚀 Setup & Installation

### ✅ Prerequisites

Ensure the following are installed:

- Python 3.10+
- Docker & Docker Compose
- PostgreSQL
- Redis
- Node.js (required for Playwright browsers)

---

## 🐍 Local Setup (Without Docker)

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/fastapi-calculator.git
cd fastapi-calculator
```

---

### 2️⃣ Create and activate a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

---

### 3️⃣ Install dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

### 4️⃣ Install Playwright browsers

```bash
playwright install chromium
```

---

### 5️⃣ Configure environment variables

Create a `.env` file in the project root:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/fastapi_db
REDIS_URL=redis://localhost:6379/0
SECRET_KEY=your_secret_key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

---

### 6️⃣ Start PostgreSQL & Redis

```bash
sudo service postgresql start
redis-server
```

---

### 7️⃣ Run the application

```bash
uvicorn app.main:app --reload
```

---

## 🐳 Docker Setup (Recommended)

### 1️⃣ Build and start containers

```bash
docker compose up --build
```

---

### 2️⃣ Stop containers

```bash
docker compose down
```

---

## 🌐 Application URLs

Once the application is running:

| Page | URL |
|---|---|
| Health Check | http://localhost:8000/health |
| Swagger UI | http://localhost:8000/docs |
| ReDoc | http://localhost:8000/redoc |

---

## 🔐 Authentication Flow

### 🔸 Register User

```
POST /auth/register
```

### 🔸 Login

```
POST /auth/login
```

Successful login returns a JWT token:

```json
{
  "access_token": "<token>",
  "token_type": "bearer"
}
```

Use this token via the **Authorize** button in Swagger UI.

---

## 🧮 Calculator Endpoints

| Action | Endpoint |
|---|---|
| Create Calculation | POST `/calculations` |
| List Calculations | GET `/calculations` |
| Get Calculation | GET `/calculations/{id}` |
| Update Calculation | PUT `/calculations/{id}` |
| Delete Calculation | DELETE `/calculations/{id}` |

---

## 🧪 Running Tests

### ▶️ Run all tests

```bash
pytest
```

---

### ▶️ Run tests with coverage

```bash
pytest --cov=app --cov-report=term-missing
```

---

### ▶️ Run Playwright E2E tests

```bash
pytest tests/e2e
```

---

## 🎭 Playwright Testing

Playwright is used for end-to-end browser testing.

Features include:
- Headless browser execution
- UI interaction testing
- Screenshot & video capture
- CI/CD compatibility

---

## 🗄️ Database Initialization

Database tables are automatically created on application startup:

```python
Base.metadata.create_all(bind=engine)
```

If tables are missing:

```bash
docker compose restart
```

---

## 🛠️ Common Issues

### ❌ Tables missing after running pytest
- Pytest may drop test tables
- Restart containers or re-run DB initialization

### ❌ Redis connection error
- Ensure Redis is running on port 6379

### ❌ Authentication returns 500
- Check Redis availability
- Verify environment variables

---

## 📌 Future Improvements

- Alembic database migrations
- Role-based access control
- Rate limiting
- Frontend UI
- CI/CD pipeline integration

---

## 👨‍💻 Author

**Fahad Ali**  
Computer Science  
FastAPI • SQLAlchemy • Docker • Testing
