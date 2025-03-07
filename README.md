# 📌 Nura_backend: Flask + PostgreSQL Local Development Setup

This guide walks you through setting up and running the Flask app with a local PostgreSQL database.

---

## 🔧 Prerequisites
Make sure you have the following installed:
- **Python 3.8+**: [Download Python](https://www.python.org/downloads/)
- **PostgreSQL**: [Download PostgreSQL](https://www.postgresql.org/download/)

---

## 🚀 Setup Instructions

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/ryanschwartz88/nura_backend.git
cd nura_backend
```

### 2️⃣ Set Up Virtual Environment
```bash
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Set Up PostgreSQL Database
**Start PostgreSQL and create the database:**
```bash
sudo -i -u postgres psql
```
Inside the PostgreSQL shell, run:
```sql
CREATE DATABASE myapp_db;
CREATE USER myapp_user WITH PASSWORD 'password';
ALTER ROLE myapp_user SET client_encoding TO 'utf8';
ALTER ROLE myapp_user SET default_transaction_isolation TO 'read committed';
ALTER ROLE myapp_user SET timezone TO 'UTC';
GRANT ALL PRIVILEGES ON DATABASE myapp_db TO myapp_user;
\q
```

### 5️⃣ Configure Environment Variables
Create a `.env` file in the project root and add:
```ini
DATABASE_URL=postgresql://myapp_user:password@localhost/myapp_db
FLASK_ENV=development
SECRET_KEY=your_secret_key
```

### 6️⃣ Run Database Migrations
```bash
flask db init
flask db migrate -m "Initial migration"
flask db upgrade
```

### 7️⃣ Start the Flask Server
```bash
flask run --host=0.0.0.0 --port=5000
```
Your API should now be running at **http://localhost:5000** 🎉

---

## 🛠 Common Commands

### 🔄 Apply Database Migrations
```bash
flask db migrate -m "New changes"
flask db upgrade
```

### 📦 Install New Dependencies
```bash
pip install <package>
pip freeze > requirements.txt
```

### 🛑 Stop the Virtual Environment
```bash
deactivate
```

---

## 🌍 Deployment Notes
 When ready for **production deployment**, update `DATABASE_URL` to point to a **cloud database** (like AWS RDS or Aurora). If deploying everything on an **EC2 instance**, no changes are needed—just make sure PostgreSQL is installed on the server.

---

## ❓ Need Help?
If you run into issues, check the logs or reach out to the team! 🚀

