# Token Trail

**A web-based code similarity detection system for academic integrity.**

Token Trail is an instructor-facing platform designed to help academic staff efficiently review programming assignment submissions for suspicious similarity. Built with a custom tokenization and similarity-scoring engine, it supports Java, C, and C++ submissions without relying on third-party plagiarism APIs.

---

## 🎯 Project Overview

Token Trail addresses a critical need in academic environments: detecting potential code plagiarism while respecting student privacy and providing instructors with intuitive tools for investigation. The system features a **student-facing submission portal** and a **full-featured instructor dashboard** for course/assignment management and similarity analysis.

### Key Constraints (Academic Integrity Verified)
- ✅ **Custom Analysis Engine**: No external plagiarism APIs (MOSS, Turnitin, etc.)
- ✅ **Multi-Language Support**: Java, C, C++
- ✅ **Homogeneous Assignments**: One language per assignment set
- ✅ **Anonymous Submissions**: Students submit via assignment key only (no student accounts)
- ✅ **Instructor Authentication**: Secure JWT-based access control

---

## ✨ Features

### 👥 Student (Public Portal)
- Validate a 10-digit assignment key
- Upload assignment as ZIP submission
- Receive confirmation with submission ID

### 🏫 Instructor (Authenticated Portal)
- Sign up / log in with email & password
- Create courses and assignments
- Generate & manage assignment keys (regenerate/expire)
- Manage exclusion codes and submission admin actions
- View submissions and trigger similarity analysis runs
- *(UI stubs prepared for ranked similarity reports and side-by-side code comparison)*

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18 + Vite + Tailwind CSS + Lucide React icons |
| **Frontend Testing** | Vitest + React Testing Library |
| **Backend API** | FastAPI (Python) |
| **Analysis Engine** | Python worker process (async tokenization, winnowing, scoring) |
| **Database** | MongoDB |
| **Authentication** | JWT (JSON Web Tokens) |
| **File Storage** | Local disk (`/uploads`) in dev; S3/MinIO ready |
| **Containerization** | Docker + Docker Compose |

---

## 📂 Monorepo Structure

```
token-trail/
├── frontend/           # React UI (student upload + instructor portal)
│   ├── src/
│   ├── tests/          # Vitest + React Testing Library tests
│   ├── package.json
│   ├── vite.config.js
│   └── tailwind.config.js
├── backend/            # FastAPI server + analysis engine + worker
├── docs/               # SRS, architecture, API documentation
├── docker/             # Dockerfile configurations
├── docker-compose.yml
└── .env.example
```

---

## 🚀 Getting Started

### Prerequisites
- Docker & Docker Compose
- Git

### Quick Start

1. **Clone and configure:**
   ```bash
   git clone https://github.com/nsnow099/token-trail.git
   cd token-trail
   cp .env.example .env
   ```

2. **Run the full stack:**
   ```bash
   docker compose up --build
   ```

3. **Access the application:**
   - **Frontend**: http://localhost:5173
   - **Backend API Docs**: http://localhost:8000/docs
   - **MongoDB**: localhost:27017

4. **Run frontend tests:**
   ```bash
   cd frontend
   npm install
   npm test
   ```

For detailed setup instructions, troubleshooting, and prerequisites, see [docs/SETUP.md](docs/SETUP.md).

---

## 👤 Contributions

### Frontend & UI/UX (nsnow099)
- **UI/UX Design**: Designed and implemented intuitive interfaces for both student submission portal and instructor dashboard
- **Frontend Architecture**: Built responsive React application with Vite, routing, and state management
- **Component Library**: Created reusable React components with Tailwind CSS styling
- **Testing Strategy**: Established comprehensive frontend test suite using Vitest and React Testing Library
- **Student Portal**: End-to-end student submission flow with key validation and file upload
- **Instructor Dashboard**: Course/assignment management, key generation, and submission viewing interfaces
- **Accessibility**: Implemented accessible form controls, error messaging, and navigation patterns

### Backend (Ikechukwu-Okogwu)
- FastAPI server & authentication
- Analysis engine worker process
- Database schema & MongoDB integration

---

## 📝 License & Attribution

This project is a fork of [Ikechukwu-Okogwu/token-trail](https://github.com/Ikechukwu-Okogwu/token-trail). See [CONTRIBUTORS.md](CONTRIBUTORS.md) for detailed attribution.

---

## 📚 Documentation

- [Setup Guide](docs/SETUP.md) — Installation, prerequisites, troubleshooting
- [Architecture](docs/ARCHITECTURE.md) — System design & data flow
- [API Documentation](http://localhost:8000/docs) — OpenAPI spec (when running locally)
- [Portfolio Notes](PORTFOLIO.md) — My specific contributions and learnings

---

## 🔄 Current Status

**Project Phase**: Core features implemented; UI stubs prepared for future similarity report & code comparison views.

**Next Steps**:
- Implement ranked similarity report UI
- Build side-by-side code comparison view
- Enhance analysis performance for large assignment sets
- Add support for additional languages (Python, JavaScript)

---

## 🤝 Contributing

Contributions welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

**Created**: May 2026 | **Status**: Actively Maintained
