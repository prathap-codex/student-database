# Student Management System

A simple full-stack application to manage students with Add, Edit, and Delete functionality.

## Tech Stack

- **Frontend**: React (Vite)
- **Backend**: Node.js (Express)
- **Database**: MongoDB Atlas

## Setup Instructions

### 1. MongoDB Atlas Setup

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and create a free account
2. Create a new cluster (free tier)
3. Create a database called `studentDB`
4. Create a collection called `students`
5. Set up database access:
   - Click "Database Access" → "Add New Database User"
   - Create username and password (save these!)
6. Set up network access:
   - Click "Network Access" → "Add IP Address"
   - Add your current IP address or select "Allow Access from Anywhere" (0.0.0.0/0)
7. Get connection string:
   - Click "Connect" → "Connect your application"
   - Copy the connection string

### 2. Backend Setup

1. Navigate to backend folder:
   ```bash
   cd backend
   ```

2. Copy the example env file and update it with your MongoDB connection string:
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` and replace:
   - `<username>` with your MongoDB username
   - `<password>` with your MongoDB password
   - `cluster.mongodb.net` with your actual cluster address

3. Start the backend server:
   ```bash
   npm start
   ```

The backend will run on `http://localhost:5000`

**Note**: You must set up MongoDB Atlas first before running the backend. Without a valid MongoDB connection string, the backend will fail to start.

### 3. Frontend Setup

1. Navigate to frontend folder (in a new terminal):
   ```bash
   cd frontend
   ```

2. (Optional) Create `.env` file for API URL:
   ```bash
   cp .env.example .env
   ```
   The default API URL is `http://localhost:5000`. After deployment, update this to your backend URL.

3. Start the frontend:
   ```bash
   npm run dev
   ```

The frontend will run on `http://localhost:5173` (or another port if 5173 is in use)

## Features

- ✅ Add new students
- ✅ View all students in a table
- ✅ Edit student information
- ✅ Delete students
- ✅ Status tracking (active, completed, inactive)

## API Endpoints

- `GET /api/students` - Get all students
- `POST /api/students` - Add new student
- `PUT /api/students/:id` - Update student
- `DELETE /api/students/:id` - Delete student

## Deployment

### Frontend (Vercel)

1. Push code to GitHub
2. Go to [Vercel](https://vercel.com)
3. Click "Add New Project"
4. Import your GitHub repository
5. Select the `frontend` folder as root directory
6. Click Deploy

### Backend (Render)

1. Go to [Render](https://render.com)
2. Click "New +" → "Web Service"
3. Connect your GitHub repository
4. Select the `backend` folder
5. Add environment variable: `MONGODB_URI` (your MongoDB connection string)
6. Click Deploy Web Service

After deployment:
1. Copy your Render backend URL (e.g., `https://your-backend.onrender.com`)
2. In Vercel, go to your project settings → Environment Variables
3. Add `VITE_API_URL` with your backend URL
4. Redeploy the frontend

This will update the API URL in your frontend automatically.
