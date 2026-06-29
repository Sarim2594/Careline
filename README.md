# CareLine E-Clinic Management System

CareLine is a comprehensive, role-based e-clinic management system designed to streamline the operations of medical clinics. Built with a modern tech stack (React, Node.js/Express, PostgreSQL) and containerized with Docker, CareLine provides a secure and scalable solution for managing clinic staff, patients, and communications.

## 🌟 Features

- **Role-Based Access Control (RBAC):** Distinct dashboards and permissions for various roles:
  - **Superadmin:** Oversees system-wide settings, regions, and high-level management.
  - **Admin:** Manages specific clinic operations, staff, and local settings.
  - **Doctor:** Accesses patient diagnoses, and manages appointments.
  - **Receptionist:** Handles patient intake, scheduling, and general inquiries.
- **Clinic & Region Management:** Organize and manage multiple clinic branches across different regions.
- **Bulletins & Notifications:** Integrated communication system to keep staff informed via internal bulletins and real-time notifications.
- **Email Integration:** Send diagnoses and important updates directly to patients via email (powered by Nodemailer).
- **Secure Authentication:** Robust user authentication and password hashing using bcrypt.

## 🛠️ Technology Stack

- **Frontend:** React.js, React Router, Axios
- **Backend:** Node.js, Express.js
- **Database:** PostgreSQL (with `node-pg-migrate` for schema migrations)
- **Containerization:** Docker & Docker Compose

## 🚀 Quick Start (Local Development)

### 1. Database Configuration
Create or edit the `backend/.env` file:
```env
DB_HOST=localhost
DB_PORT=5432
DB_NAME=careline
DB_USER=postgres
DB_PASSWORD=your_password_here
APP_PORT=5000
```

### 2. Initialize the Database
Install backend dependencies and run the database initialization (this resets, migrates, and seeds the database):
```bash
cd backend
npm install
npm run db:init
```

### 3. Start the Backend Server
```bash
cd backend
npm run dev
```
The API will be available at **http://localhost:5000**.

### 4. Start the Frontend Application
```bash
cd frontend
npm install
npm start
```
The React app will be available at **http://localhost:3000**.

## 🐳 Docker Deployment

CareLine is fully containerized, making deployment straightforward on any VPS or local machine with Docker installed.

### Prerequisites
- Docker and Docker Compose installed.

### Deployment Steps
1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd careline-management-system
   ```

2. **Build and start the containers:**
   ```bash
   docker-compose up -d --build
   ```

3. **Initialize the schema and demo data:**
   ```bash
   docker-compose run --rm backend npm run db:init
   ```

4. **Access the Application:**
   - **Frontend:** `http://localhost` (or your VPS IP on port 80)
   - **Backend API:** `http://localhost:5000`
   - **Database:** Internal port 5432

### Managing Docker Containers
- **View logs:** `docker-compose logs -f`
- **Check status:** `docker-compose ps`
- **Stop application:** `docker-compose down`
- **Update application:** `git pull` then `docker-compose up -d --build`

## 🔑 Demo Credentials

Use the following credentials to explore the different role-based views (seeded automatically via `npm run db:init`):

| Role | Username | Password |
|------|----------|----------|
| **Superadmin** | `muhammad.yasir` | `super123` |
| **Admin** | `sarim.khan` | `admin123` |
| **Doctor** | `ahmed.ali` | `doc123` |
| **Receptionist** | `kamran.akmal` | `recep123` |

## 📧 Note on Email Configuration
The `/api/receptionist/email-diagnosis` endpoint uses Nodemailer. To enable real email delivery, configure your SMTP server credentials within `backend/routes/receptionist.js`.
