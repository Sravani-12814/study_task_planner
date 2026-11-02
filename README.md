# Study Task Planner — MERN CRUD

A student-friendly task list for coursework, study reminders, and project next steps. Create, browse, search, edit, and delete tasks. The project follows the supplied sample's stack and folder layout: React + Vite in `client`, Node + Express + Mongoose in `server`, and MongoDB for persistence.

## Requirements

- Windows 10/11
- Node.js 20.19+ or 22.12+ (includes npm)
- MongoDB Community Server running locally, or your own MongoDB Atlas URI
- Visual Studio Code

## Run in VS Code on Windows

1. Install Node.js and MongoDB Community Server if needed. Start the MongoDB Windows service before running the app. This project does not install or start MongoDB.
2. Extract the ZIP. In VS Code, choose **File → Open Folder** and select `study-task-planner-mern`.
3. In a VS Code terminal at the project root, install packages for all three workspaces:

   ```powershell
   npm install
   npm --prefix server install
   npm --prefix client install
   ```

4. Copy `server/.env.example` to `server/.env`. It points to local MongoDB at `mongodb://127.0.0.1:27017/study_tasks`. No credentials are included or needed for a default local MongoDB setup.
5. For Atlas, create your own cluster and database user, allow your computer's IP in Atlas Network Access, then put your private URI in `server/.env` as `MONGO_URI`. Do not commit or share `.env`.
6. From the project root, run `npm run dev`.
7. Open the Vite address shown in the terminal, normally `http://localhost:5173`.

MongoDB must be reachable for tasks to load and save. Check API/database status at `http://localhost:5000/api/health`.

## Commands

- `npm run dev` — start the API and Vite frontend
- `npm run build` — make an optimized frontend build in `client/dist`
- `npm start` — start the API

## API routes

Base path: `/api/items`

- `GET /` — list tasks; accepts `?search=...`
- `GET /:id` — get one task
- `POST /` — create a task
- `PUT /:id` — update a task
- `DELETE /:id` — delete a task

Each task stores `name` (task name) and `description` (task details), plus timestamps. Names must be 2–80 characters and details 3–500 characters. The API returns clear JSON errors for invalid IDs, missing records, validation failures, unavailable database connections, and unexpected errors.
