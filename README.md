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

### Step 1: Push to GitHub

1. Create a new repository on GitHub
2. Add the remote URL:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git branch -M main
   git push -u origin main
   ```

### Step 2: Deploy Backend to Render

1. Go to [Render](https://render.com) and create an account
2. Click "New +" → "Web Service"
3. Connect your GitHub repository
4. Configure:
   - **Root Directory**: `backend`
   - **Build Command**: `npm install`
   - **Start Command**: `node server.js`
5. Add Environment Variable:
   - Key: `MONGODB_URI`
   - Value: Your MongoDB Atlas connection string
6. Click "Deploy Web Service"
7. Wait for deployment and copy the backend URL (e.g., `https://your-backend.onrender.com`)

### Step 3: Deploy Frontend to Vercel

1. Go to [Vercel](https://vercel.com) and create an account
2. Click "Add New Project"
3. Import your GitHub repository
4. Configure:
   - **Framework Preset**: Vite
   - **Root Directory**: `frontend`
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
5. Add Environment Variable:
   - Key: `VITE_API_URL`
   - Value: Your Render backend URL (from Step 2)
6. Click "Deploy"
7. Wait for deployment and copy the frontend URL

### Step 4: Test the Deployed App

1. Open your Vercel frontend URL
2. Test adding, editing, and deleting students
3. Verify data persists in MongoDB Atlas

**Note**: The first time you access the Render backend, it may take 30-60 seconds to wake up (cold start).
