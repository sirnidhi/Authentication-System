# Authentication System Workflow

## Development Workflow

### 1. Setup & Installation
```bash
git clone https://github.com/sirnidhi/Authentication-System.git
cd Authentication-System
npm install
```

### 2. Environment Configuration
```bash
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret
```

### 3. Start Development Server
```bash
npm run dev  # Development with nodemon
npm start    # Production
```

## API Testing Workflow

### Step 1: User Registration
```bash
POST /api/auth/signup
{
  "username": "testuser",
  "email": "test@example.com",
  "password": "password123",
  "role": "user"
}
```

### Step 2: User Login
```bash
POST /api/auth/login
{
  "email": "test@example.com",
  "password": "password123"
}
# Save the returned JWT token
```

### Step 3: Access Protected Routes
```bash
GET /api/users/profile
Headers: Authorization: Bearer <JWT_TOKEN>
```

### Step 4: Admin Operations (Admin Role Required)
```bash
GET /api/admin/users
Headers: Authorization: Bearer <ADMIN_JWT_TOKEN>
```

## Database Schema

### User Model
```javascript
{
  username: String (required, unique),
  email: String (required, unique),
  password: String (required, hashed),
  role: String (enum: ['user', 'admin']),
  createdAt: Date,
  updatedAt: Date
}
```

## Security Features
- Password hashing with bcrypt (12 salt rounds)
- JWT token authentication
- Role-based authorization
- Protected routes middleware
- Input validation

## Project Structure
```
Authentication-System/
├── config/
│   └── database.js
├── controllers/
│   ├── authController.js
│   └── userController.js
├── middleware/
│   └── auth.js
├── models/
│   └── User.js
├── routes/
│   ├── admin.js
│   ├── auth.js
│   └── users.js
├── server.js
├── package.json
└── .env.example
```