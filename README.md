# 🪙 Finsey

**Finsey** is a comprehensive, backend-driven personal finance management system built with **Django 5** and **Django Rest Framework (DRF)**. It is designed to help users take control of their financial life by tracking accounts, transactions, savings goals, and important documents.

## 🚀 Features

### 💸 Transaction Management
-   **Income & Expense Tracking**: Record and categorize your financial flows.
-   **Planned Transactions**: Schedule future expenses and recurring payments.
-   **Advanced Filtering**: filter transactions by date, category, or type.
-   **Categories**: Organize your spending with customizable income and expense categories.

### 🎯 Savings & Goals
-   **Goal Setting**: Create specific savings goals (e.g., "Emergency Fund", "Vacation") with target amounts and dates.
-   **Progress Tracking**: Record inflows and outflows towards your goals.
-   **Auto-Completion**: Goals automatically update their completion status based on your saved amount.

### 📂 Document Storage
-   **Financial Documents**: Securely upload and store important files (e.g., invoices, contracts).
-   **Organization**: Tag documents with titles and notes for easy retrieval.

### 🔐 Security & Accounts
-   **Secure Authentication**: JWT (JSON Web Token) based authentication for secure API access.
-   **Multi-Account Support**: Manage multiple financial accounts under one user profile.

### ⚙️ Technical Highlights
-   **Async Processing**: Uses **Celery** and **Redis** for background tasks (e.g., notifications, scheduled updates).
-   **Containerization**: Fully Dockerized for consistent development and deployment environments.
-   **Database**: robust data storage with **PostgreSQL**.

---

## 🛠️ Tech Stack

-   **Backend Framework**: Python 3.12, Django 5.1, Django Rest Framework 3.15
-   **Database**: PostgreSQL 13
-   **Task Queue**: Celery 5.4 + Redis 6.2
-   **Dependency Management**: Poetry
-   **Containerization**: Docker & Docker Compose
-   **Testing**: Pytest

---

## 🏁 Getting Started

### Prerequisites

-   [Docker](https://www.docker.com/get-started) and [Docker Compose](https://docs.docker.com/compose/install/) installed on your machine.
-   [Make](https://www.gnu.org/software/make/) (optional, for using helper commands).

### 1. Clone the Repository

```bash
git clone https://github.com/agawojdecka/Finsey.git
cd Finsey
```

### 2. Run with Docker (Recommended)

Build and start the services:

```bash
docker-compose up -d --build
```

```bash
docker-compose run api python manage.py migrate
```

The API will be available at `http://localhost:8000`.

-   **Admin Panel**: `http://localhost:8000/admin/`
-   **API Root**: `http://localhost:8000/`

### 3. Local Development (Without Docker)

If you prefer to run the Django app locally while keeping services (DB, Redis) in Docker:

1.  **Install Dependencies**:
    ```bash
    poetry install
    ```
2.  **Start Infrastructure** (DB & Redis only):
    ```bash
    docker-compose up -d db redis
    ```
3.  **Run Migrations**:
    ```bash
    poetry run python manage.py migrate
    ```
4.  **Run Server**:
    ```bash
    poetry run python manage.py runserver
    ```

---

## 🧪 Development Commands

The project includes a `Makefile` for common development tasks:

-   **Format Code** (Black & Isort):
    ```bash
    make format
    ```
-   **Lint Code** (Flake8 & Mypy):
    ```bash
    make lint
    ```
-   **Run Tests**:
    ```bash
    poetry run pytest
    ```

---

## 📡 API Overview

| Module | URL Prefix | Description |
| :--- | :--- | :--- |
| **Auth** | `/api/login-jwt/` | Login and obtain JWT tokens. |
| **Transactions** | `/transactions/` | Manage income, expenses, and planned transactions. |
| **Savings** | `/savings/` | Manage savings entries and goals. |
| **Accounts** | `/accounts/` | Manage generic financial accounts. |
| **Documents** | `/documents/` | Upload and retrieve financial documents. |
| **Users** | `/users/` | User profile management. |
