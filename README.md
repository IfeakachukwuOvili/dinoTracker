# dinoTracker

A full-stack savings and expense tracking app that allows users to create accounts, manage savings plans, track expenses, and securely delete their data. Built for hackathon speed but with robust user and data management.

---

## Table of Contents

- [Features](#features)
- [Architecture Overview](#architecture-overview)
- [Frontend](#frontend)
- [Backend](#backend)
- [Setup & Installation](#setup--installation)
- [API Endpoints](#api-endpoints)
- [Account & Data Management](#account--data-management)
- [Tech Stack](#tech-stack)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- User sign up, login, and logout with unique email enforcement
- Multiple user accounts supported
- Add, edit, and manage multiple savings plans per user
- Track expenses per user
- Profile modal for editing user info, theme switching, and account deletion
- Confirmation popup for sensitive actions (like account deletion)
- Full data cleanup: deleting an account removes all related plans and expenses

---

## Architecture Overview

- **Frontend:** React app (Vite), communicates with backend via RESTful API.
- **Backend:** Node.js/Express server with MongoDB (Mongoose).
- **Data Models:** User, Plan, Expense (all linked by user email).

---

## Frontend

Located in `/Frontend`. Main components:

- **LoginPage.jsx:** Handles user authentication.
- **SignUp.jsx:** Handles user registration with validation.
- **AddPlan.jsx:** Lets users create and manage multiple savings plans.
- **ProfileModal.jsx:** Edit profile, switch theme, and delete account (with confirmation).
- **ConfirmPopup.jsx:** Reusable confirmation dialog for critical actions.

**State Management:**  
Uses React hooks and localStorage for session persistence.

**User Flow:**
1. User signs up or logs in.
2. User can add/edit savings plans and expenses.
3. User can access the profile modal to edit info, switch theme, or delete their account.
4. Deleting an account removes all user data (plans & expenses) from the backend and logs the user out.

---

## Backend

Located in `/Backend`. Main files:

- **index.js:** Main Express server file. Defines all REST API endpoints.
- **models/User.js:** Mongoose schema for user accounts.
- **models/Plan.js:** Mongoose schema for savings plans.
- **models/Expense.js:** Mongoose schema for expenses.

**Key API Endpoints:**
- `POST /api/users` — Create user
- `GET /api/users` — List users
- `GET /api/users/:id` — Get user by ID
- `PUT /api/users/:id` — Update user
- `DELETE /api/users/:id` — Delete user and all related plans/expenses

- `POST /api/plans` — Create savings plan
- `GET /api/plans?userEmail=...` — Get all plans for a user

- `POST /api/expenses` — Create expense
- `GET /api/expenses?userEmail=...` — Get all expenses for a user

**Data Cleanup Logic:**  
When a user is deleted, all plans and expenses associated with that user's email are also deleted.

---

## Setup & Installation

### Prerequisites

- Node.js & npm
- MongoDB (local or Atlas)

### Backend

```bash
cd Backend
npm install
npm run dev
# or
node index.js
```

### Frontend

```bash
cd Frontend
npm install
npm run dev
```

### Environment

- Backend runs on `http://localhost:5000`
- Frontend runs on `http://localhost:5173` (or as set by Vite)

---

## API Endpoints

| Method | Endpoint                  | Description                          |
|--------|---------------------------|--------------------------------------|
| POST   | /api/users                | Create a new user                    |
| GET    | /api/users                | List all users                       |
| GET    | /api/users/:id            | Get user by ID                       |
| PUT    | /api/users/:id            | Update user                          |
| DELETE | /api/users/:id            | Delete user + all plans & expenses   |
| POST   | /api/plans                | Create a new plan                    |
| GET    | /api/plans?userEmail=...  | Get all plans for a user             |
| POST   | /api/expenses             | Create a new expense                 |
| GET    | /api/expenses?userEmail=... | Get all expenses for a user         |

---

## Account & Data Management

- **Multiple Accounts:** Users can sign up with unique emails. Each user has their own plans and expenses.
- **Delete Account:** From the profile modal, users can delete their account. This triggers a confirmation popup. Upon confirmation, the backend deletes the user and all related plans/expenses, and the frontend logs the user out.
- **Session Handling:** User sessions are managed with localStorage.

---

## Tech Stack

- **Frontend:** React (Vite), Inline CSS, Framer Motion
- **Backend:** Node.js, Express, MongoDB (Mongoose)
- **Other:** CORS, dotenv

---

## Contributing

Feel free to fork and submit pull requests! For major changes, open an issue first to discuss what you’d like to change.

---

## License

MIT

---

Let me know if you want to add deployment instructions, screenshots, or any other custom sections!
#   d i n o T r a c k e r  
 