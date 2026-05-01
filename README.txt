====================================================
  TEAM TASK MANAGER - README
====================================================

OVERVIEW
--------
A production-ready full-stack Team Task Manager built with
React + TypeScript + Tailwind CSS.  All data is persisted in
localStorage so no backend or database setup is needed to run
locally.

TECH STACK
----------
  Frontend : React 18 + TypeScript + Vite
  Styling  : Tailwind CSS
  Routing  : React Router v6
  Icons    : Lucide React
  Storage  : Browser localStorage (zero-config, fully offline)

FEATURES
--------
  Authentication
    - Signup & Login with email / password
    - Password hashing (client-side)
    - JWT-style session stored in localStorage
    - Protected routes (redirects to /login when unauthenticated)

  Role-Based Access Control
    Admin
      - Create / edit / delete projects
      - Add team members to projects
      - Create / edit / delete tasks, assign to members
      - View all tasks across all projects
    Member
      - View only projects they are members of
      - View only tasks assigned to them
      - Update task status (To Do → In Progress → Completed)

  Projects
    - Title, description, team members
    - Progress bar (% tasks completed)
    - Create / edit / delete (admin only)

  Tasks
    - Title, description, assigned user, status, deadline
    - Statuses: To Do | In Progress | Completed
    - Overdue detection (deadline passed + not completed)
    - Kanban board view per project
    - Filterable list view on the Tasks page

  Dashboard
    - Total / Completed / Pending / Overdue task counters
    - Recent tasks feed
    - Project progress list

FOLDER STRUCTURE
----------------
  src/
    types/index.ts          – TypeScript interfaces
    lib/store.ts            – localStorage CRUD layer
    context/
      AuthContext.tsx       – auth state & actions
      DataContext.tsx       – projects / tasks / users state
    components/
      Layout.tsx            – sidebar + top bar shell
      Badge.tsx             – status / role / overdue badges
      ProjectModal.tsx      – create / edit project form
      TaskModal.tsx         – create / edit task form
      ConfirmModal.tsx      – delete confirmation dialog
    pages/
      LoginPage.tsx
      SignupPage.tsx
      DashboardPage.tsx
      ProjectsPage.tsx
      ProjectDetailPage.tsx
      TasksPage.tsx
    App.tsx                 – routing root
    main.tsx                – React entry point

DEMO CREDENTIALS (pre-seeded on first load)
-------------------------------------------
  Admin  : admin@demo.com  / admin123
  Member : bob@demo.com    / member123
  Member : carol@demo.com  / member123

SETUP & RUN (VSCode / Local)
-----------------------------
  Prerequisites: Node.js >= 18

  1.  Open the project folder in VSCode
  2.  Open a terminal (Ctrl+` ) and run:

        npm install
        npm run dev

  3.  Visit http://localhost:5173 in your browser
  4.  Log in with the demo credentials above

  Build for production:
        npm run build
        npm run preview   # serves dist/ locally

DEPLOYMENT GUIDE (Vercel - Frontend only, no backend needed)
------------------------------------------------------------
  Because the app uses localStorage, only the frontend needs hosting.

  Vercel (recommended, free)
  --------------------------
  1.  Push the project to a GitHub repository.
  2.  Go to https://vercel.com and sign in with GitHub.
  3.  Click "Add New Project" → select your repository.
  4.  Framework preset: Vite
  5.  Build command   : npm run build
      Output directory: dist
  6.  Click "Deploy".  Your live URL appears in ~60 seconds.

  Railway (if you want Node backend too)
  ---------------------------------------
  To add a real Node/Express + MongoDB backend later:
  1.  Add a /server folder with Express + Mongoose.
  2.  On Railway, create two services: Web (Node) and MongoDB plugin.
  3.  Set environment variables:
        MONGO_URI=<railway mongo url>
        JWT_SECRET=<random 64-char string>
        PORT=5000
  4.  For the frontend, create a second Railway service pointing to
      the /dist folder (or deploy frontend on Vercel separately).

ENVIRONMENT VARIABLES
---------------------
  No .env file is required for the localStorage version.
  If you add a real backend, create .env:

    VITE_API_URL=https://your-backend.railway.app

GITHUB REPO STRUCTURE
---------------------
  /
  ├── src/
  ├── index.html
  ├── package.json
  ├── tailwind.config.js
  ├── vite.config.ts
  ├── tsconfig*.json
  └── README.txt

====================================================
