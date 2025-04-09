# Library Management System

A full-stack MERN (MongoDB, Express, React, Node.js) application for managing a library system with book management, student management, and book issuance tracking.

## Features

- **User Authentication**: Register, login with JWT authentication
- **Role-Based Access Control**: Different access levels for students, admins, and super-admins
- **Book Management**: Add, update, delete, and search books
- **Student Management**: Manage student records
- **Book Issuance System**: Issue books, track returns, and manage late returns
- **Late Reminder System**: Send SMS reminders for overdue books using Twilio
- **Responsive UI**: Mobile-friendly interface using React Bootstrap

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or MongoDB Atlas)
- npm or yarn

## Installation

### Clone the repository

```bash
git clone <repository-url>
cd library-management-system
```

### Backend Setup

1. Navigate to the server directory:

```bash
cd server
```

2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the server directory with the following variables:

```
MONGODB_URI=mongodb://localhost:27017/book
JWT_SECRET=your_jwt_secret
PORT=5000
TWILIO_ACCOUNT_SID=your_twilio_sid  # Optional
TWILIO_AUTH_TOKEN=your_twilio_token  # Optional
TWILIO_PHONE_NUMBER=your_twilio_phone  # Optional
```

4. Seed the database with initial data:

```bash
npm run seed
```

5. Start the backend server:

```bash
npm run dev
```

### Frontend Setup

1. Open a new terminal and navigate to the client directory:

```bash
cd client
```

2. Install dependencies:

```bash
npm install
```

3. Start the frontend development server:

```bash
npm start
```

## Default Users

After running the seed script, you can use the following default users:

- **Super Admin**
  - Email: superadmin@library.com
  - Password: superadmin123

- **Admin**
  - Email: admin@library.com
  - Password: admin123

- **Student**
  - Email: john@example.com
  - Password: john123

## API Endpoints

### Authentication
- `POST /api/users/register` - Register a new user
- `POST /api/users/login` - Login user

### Books
- `GET /api/books` - Get all books
- `GET /api/books/:id` - Get book by ID
- `GET /api/books/search` - Search books by title, author, subject, or semester
- `POST /api/books` - Add new book (admin only)
- `PUT /api/books/:id` - Update book (admin only)
- `DELETE /api/books/:id` - Delete book (admin only)

### Users
- `GET /api/users/me` - Get current user
- `GET /api/users` - Get all users (admin only)
- `GET /api/users/students` - Get all students (admin only)
- `PUT /api/users/:id` - Update user
- `DELETE /api/users/:id` - Delete user (super-admin only)

### Book Issues
- `POST /api/issues` - Issue book to student (admin only)
- `PUT /api/issues/:issueId/return` - Return book (admin only)
- `GET /api/issues` - Get all issued books (admin only)
- `GET /api/issues/student/:studentId` - Get books issued to a student
- `GET /api/issues/overdue` - Get overdue books (admin only)
- `POST /api/issues/reminders` - Send reminders for overdue books (admin only)

## Technologies Used

### Backend
- Node.js & Express.js
- MongoDB with Mongoose
- JWT for authentication
- Bcrypt for password hashing
- Twilio API for SMS notifications

### Frontend
- React
- React Router for routing
- React Bootstrap for UI components
- Axios for API requests
- JWT for authentication 