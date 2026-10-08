# Student Management System

A simple full-stack application to manage students with Add, Edit, and Delete functionality. Uses local MongoDB by default for easy development.

## Tech Stack

- **Frontend**: React (Vite)
- **Backend**: Node.js (Express)
- **Database**: MongoDB (Local or Atlas Cloud)

## Setup Instructions

### Option 1: Local MongoDB (Recommended for Development)

#### Step 1: Install and Start MongoDB

1. Install MongoDB Community Server from [mongodb.com](https://www.mongodb.com/try/download/community)
2. Start MongoDB service:
   - **Windows**: Run MongoDB as service or use `mongod` command
   - **Mac**: `brew services start mongodb-community`
   - **Linux**: `sudo systemctl start mongod`

3. Verify MongoDB is running:
   ```bash
   mongosh
   # or
   mongo
   ```

#### Step 2: Backend Setup

1. Navigate to backend folder:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the backend server (it will use local MongoDB by default):
   ```bash
   npm start
   ```

The backend will run on `http://localhost:5000` and connect to `mongodb://localhost:27017/studentDB`

### Option 2: MongoDB Atlas (Cloud Database)

If you want to use cloud MongoDB instead:

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and create a free account
2. Create a new cluster (free tier)
3. Create a database called `studentDB`
4. Set up database access and network access
5. Get connection string
6. In `backend/.env`, add:
   ```
   MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/studentDB?retryWrites=true&w=majority
   ```

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

**Important**: For cloud deployment, you need MongoDB Atlas (cloud database) - local MongoDB won't work.

1. First, set up MongoDB Atlas (see Option 2 above)
2. Go to [Render](https://render.com) and create an account
3. Click "New +" → "Web Service"
4. Connect your GitHub repository
5. Configure:
   - **Root Directory**: `backend`
   - **Build Command**: `npm install`
   - **Start Command**: `node server.js`
6. Add Environment Variable:
   - Key: `MONGODB_URI`
   - Value: Your MongoDB Atlas connection string
7. Click "Deploy Web Service"
8. Wait for deployment and copy the backend URL (e.g., `https://your-backend.onrender.com`)

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
