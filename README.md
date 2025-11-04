# User Authentication & Authorization System

## Features
- ✅ User Signup & Login APIs
- ✅ JWT-based authentication
- ✅ Password encryption with bcrypt (salt rounds: 12)
- ✅ Role-based access control (admin/user)

## Installation

```bash
npm install
```

## Environment Setup
Create `.env` file with:
```
PORT=3000
MONGODB_URI=mongodb://localhost:27017/auth_system
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRES_IN=7d
```

## Start Server
```bash
npm start
# or for development
npm run dev
```

## API Endpoints

### Authentication
- `POST /api/auth/signup` - User registration
- `POST /api/auth/login` - User login

### User Routes (Protected)
- `GET /api/users/profile` - Get authenticated user's profile information
- `PUT /api/users/profile` - Update user profile

### Admin Routes (Admin Only)
- `GET /api/admin/users` - Retrieve list of all registered users (admin access required)
- `DELETE /api/admin/users/:id` - Remove a user from the system by ID (admin access required)

## API Usage Examples

### Signup
```bash
curl -X POST http://localhost:3000/api/auth/signup \
  -H "Content-Type: application/json" \
  -d '{"username":"john","email":"john@example.com","password":"password123","role":"user"}'
```

### Login
```bash
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"john@example.com","password":"password123"}'
```

### Get Profile (Protected)
```bash
curl -X GET http://localhost:3000/api/users/profile \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

### Admin - Get All Users
```bash
curl -X GET http://localhost:3000/api/admin/users \
  -H "Authorization: Bearer ADMIN_JWT_TOKEN"
```