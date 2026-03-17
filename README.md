# Code Assignment Platform

A full-stack coding assignment platform with multi-language code compilation, file management, and room-based collaboration for teachers and students.

## Features

- **Code Editor**: Monaco editor with syntax highlighting for multiple languages (JavaScript, Python, C, C++, Java, Go, Rust)
- **Real-time Compilation**: Powered by Judge0 API
- **Room System**: Teachers create rooms, students join with room names
- **File Management**: Upload and download code files
- **PDF Generation**: Export assignments with code and execution results
- **Authentication**: JWT-based user authentication
- **Dark Theme**: Modern dark mode UI with Tailwind CSS

## Tech Stack

**Frontend**: React 18, React Router v6, Monaco Editor, Tailwind CSS, Bootstrap

**Backend**: Node.js, Express, MongoDB, Mongoose, JWT, Multer, Judge0 API, Puppeteer

## Prerequisites

- Node.js 18 or higher
- MongoDB Atlas account (free tier works)
- Judge0 API key from [Sulu.sh](https://sulu.sh)

## Setup

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd Hack_vortex_2024
```

### Step 2: Install Dependencies

Open two terminals:

**Terminal 1 (Backend):**
```bash
cd backend
npm install
```

**Terminal 2 (Frontend):**
```bash
cd frontend
npm install
```

### Step 3: Configure Environment Variables

**Backend** - Create `backend/.env` (copy from `backend/.env.example`):

```env
PORT=3000
MONGO_CONN=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/<database>?retryWrites=true&w=majority&appName=<appname>
JWT_SECRET=your-super-secret-jwt-key-minimum-32-characters-long
JUDGE0_API_URL_BATCH=https://judge0-ce.p.sulu.sh/submissions/batch
JUDGE0_API_URL_SINGLE=https://judge0-ce.p.sulu.sh/submissions
JUDGE0_API_KEY=your-judge0-api-key-here
FRONTEND_URL=http://localhost:3001
NODE_ENV=development
```

**Frontend** - Create `frontend/.env` (copy from `frontend/.env.example`):

```env
REACT_APP_API_URL=http://localhost:3000/api
REACT_APP_JUDGE0_API_URL=https://judge0-ce.p.sulu.sh
```

### Step 4: Run the Application

**Terminal 1 (Backend):**
```bash
cd backend
npm start
```

Backend runs on: `http://localhost:3000`

**Terminal 2 (Frontend):**
```bash
cd frontend
npm start
```

Frontend runs on: `http://localhost:3001`

## Project Structure

```
Hack_vortex_2024/
├── backend/
│   ├── Controllers/      # Request handlers
│   ├── Middlewares/      # Auth and validation middleware
│   ├── Models/           # MongoDB schemas
│   ├── Routes/           # API routes
│   ├── config/           # Configuration files
│   ├── uploads/          # Uploaded files storage
│   ├── index.js          # Server entry point
│   ├── .env.example      # Environment template
│   └── package.json
├── frontend/
│   ├── src/
│   │   ├── components/   # React components
│   │   ├── services/     # API service functions
│   │   ├── context/      # React Context for state
│   │   └── App.js        # Main app component
│   ├── public/
│   ├── .env.example      # Environment template
│   └── package.json
└── README.md
```

## API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth/signup | Register new user |
| POST | /api/auth/login | User login |

### Rooms
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/rooms/create | Create room (teacher only) |
| POST | /api/rooms/join | Join room (student only) |
| GET | /api/rooms/teacher/rooms | Get teacher's rooms |
| GET | /api/rooms/student/rooms | Get student's rooms |

### Assignments
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/assignments/submit | Submit assignment |
| POST | /api/assignments/compile | Compile and generate PDF |
| POST | /api/assignments/run | Run code |

### Files
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/files/upload | Upload files (max 5, 10MB each) |
| GET | /api/files/list | List uploaded files |
| GET | /api/files/:filename | Read file content |
| DELETE | /api/files/:filename | Delete file |

## User Roles

- **Teacher**: Can create rooms, view student submissions
- **Student**: Can join rooms, submit assignments, compile code

## Troubleshooting

**Backend 500 Error:**
- Verify MongoDB connection string in `.env`
- Ensure `JWT_SECRET` is set
- Check backend console for specific errors

**Frontend Not Connecting:**
- Confirm backend is running on port 3000
- Check `REACT_APP_API_URL` in frontend `.env`

**File Upload Issues:**
- Ensure `backend/uploads/` directory exists
- Check file size (max 10MB per file)

## License

MIT License
