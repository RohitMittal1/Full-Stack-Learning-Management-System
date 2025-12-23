# Learning Management System (LMS)

A full-stack Learning Management System built with **React** (Frontend) and **Node.js + Express** (Backend), featuring role-based access control, course management, and shopping cart functionality.

## 🚀 Features

### User Roles
- **Admin**: Manage users, view all courses, assign roles
- **Instructor**: Create, update, and delete courses
- **Student**: Browse courses, add to cart, purchase courses

### Core Functionality
- 🔐 JWT-based authentication with secure cookies
- 🛒 Shopping cart system
- 📚 Course curriculum with chapters and video links
- 👥 Role-based access control (RBAC)
- 🖼️ Image upload for course thumbnails
- 📊 User dashboard based on roles
- 🔍 Course search and filtering

## 🛠️ Tech Stack

### Frontend
- React 19.1.0
- React Router DOM 7.7.1
- Axios for API calls
- Tailwind CSS 4.1.11
- Vite 7.0.4
- Lucide React (icons)
- Recharts (analytics)

### Backend
- Node.js with Express 5.1.0
- MongoDB with Mongoose 8.17.0
- JWT authentication
- Bcrypt for password hashing
- Multer for file uploads
- Cookie Parser
- CORS

## 📁 Project Structure

```
├── Backend-main/
│   ├── controllers/      # Route controllers
│   ├── middlewares/      # Auth, role check, upload
│   ├── models/           # MongoDB schemas
│   ├── routes/           # API routes
│   ├── scripts/          # Utility scripts (createAdmin)
│   ├── utils/            # Helper functions
│   ├── public/images/    # Uploaded course images
│   └── index.js          # Entry point
│
├── frontend-main/
│   ├── src/
│   │   ├── components/   # Reusable components
│   │   ├── pages/        # Page components
│   │   ├── context/      # React context (Auth)
│   │   ├── utils/        # API utilities
│   │   └── App.jsx       # Main app component
│   └── package.json
```

## 🔧 Installation & Setup

### Prerequisites
- Node.js (v16 or higher)
- MongoDB Atlas account or local MongoDB
- npm or yarn

### Backend Setup

1. Navigate to backend directory:
```bash
cd Backend-main
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (use `.env.example` as template):
```env
MONGO_URL=mongodb+srv://username:password@cluster.mongodb.net/database
CLIENT_URL=http://localhost:5173
PORT=3001
NODE_ENV=development
JWT_SECRET=your_strong_random_secret_here
```

4. Create an admin user:
```bash
node scripts/createAdmin.js
```

5. Start the backend server:
```bash
npm run dev
```

Backend will run on `http://localhost:3001`

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend-main
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file:
```env
VITE_API_URL=http://localhost:3001/api
VITE_YOUTUBE_API_KEY=your_youtube_api_key
```

4. Start the frontend:
```bash
npm run dev
```

Frontend will run on `http://localhost:5173`

## 🔑 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Courses
- `GET /api/allCourses` - Get all courses
- `GET /api/courses/:id` - Get course by ID
- `POST /api/courses` - Create course (Instructor only)
- `PUT /api/courses/:id` - Update course (Instructor only)
- `DELETE /api/courses/:id` - Delete course (Instructor only)
- `GET /api/my-courses` - Get instructor's courses

### Protected Routes
- `GET /api/protected/users` - Get all users (Admin only)
- `GET /api/protected/students` - Get all students
- `GET /api/protected/instructors` - Get all instructors
- `PUT /api/protected/users/role` - Update user role (Admin only)
- `DELETE /api/protected/users/:id` - Delete user (Admin only)
- `GET /api/protected/cart` - Get user's cart
- `POST /api/protected/cart` - Add to cart
- `DELETE /api/protected/cart/:courseId` - Remove from cart
- `POST /api/protected/user/:id/purchase` - Purchase courses

## 👤 Default Admin Credentials

After running `createAdmin.js`:
- **Email**: admin@learnify.com
- **Password**: admin123

⚠️ **Change these credentials in production!**

## 🔒 Security Features

✅ Environment variable validation  
✅ Password hashing with bcrypt  
✅ JWT-based authentication  
✅ Role-based access control  
✅ HTTP-only cookies  
✅ CORS configuration  
✅ Input validation  
✅ File type validation for uploads  
✅ Global error handler  

See [SECURITY.md](Backend-main/SECURITY.md) for detailed security guidelines.

## 📝 Environment Variables

### Backend (.env)
| Variable | Description | Example |
|----------|-------------|---------|
| `MONGO_URL` | MongoDB connection string | `mongodb+srv://...` |
| `CLIENT_URL` | Frontend URL | `http://localhost:5173` |
| `PORT` | Server port | `3001` |
| `JWT_SECRET` | JWT signing secret | `random_32_char_string` |
| `NODE_ENV` | Environment | `development` or `production` |

### Frontend (.env)
| Variable | Description | Example |
|----------|-------------|---------|
| `VITE_API_URL` | Backend API URL | `http://localhost:3001/api` |
| `VITE_YOUTUBE_API_KEY` | YouTube API key | `AIza...` |

## 🚧 Known Issues & TODO

- [ ] Add refresh token mechanism
- [ ] Implement rate limiting
- [ ] Add pagination to course lists
- [ ] Add search and filtering functionality
- [ ] Implement password reset
- [ ] Add email notifications
- [ ] Add course reviews and ratings
- [ ] Implement payment gateway integration
- [ ] Add unit and integration tests
- [ ] Add API documentation (Swagger)

## 📄 License

This project is licensed under the ISC License.

## 👥 Contributors

- Rohit Mittal - [GitHub Profile](https://github.com/RohitMittal1)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request



---

**⚠️ Important**: Before deploying to production, please read [SECURITY.md](Backend-main/SECURITY.md) and rotate all secrets!
