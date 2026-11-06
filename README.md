# Job Portal

A full-stack job portal built with React and Express. Candidates can browse and apply for jobs, while recruiters can publish listings and manage applications.

**Live backend:** [job-portal-server-alpha-bice.vercel.app](https://job-portal-server-alpha-bice.vercel.app)

## Features

- Browse and search visible job listings.
- Sign in as a candidate with Clerk, apply for jobs, track applications, and upload a resume.
- Register and sign in as a company, post jobs, manage listing visibility, and review applicants.
- Store application data in MongoDB and uploaded files in Cloudinary.
- Receive user lifecycle updates through Clerk webhooks.

## Tech stack

- **Frontend:** React 19, Vite, React Router, Tailwind CSS, Clerk, Axios
- **Backend:** Node.js, Express 5, MongoDB/Mongoose
- **File uploads:** Cloudinary and Multer
- **Monitoring:** Sentry

## Repository structure

```text
.
├── client/   # React/Vite frontend
└── server/   # Express API
```

## Prerequisites

- Node.js (an LTS release recommended) and npm
- MongoDB connection string
- Clerk application credentials
- Cloudinary account credentials

## Local development

The frontend and backend are separate npm projects. Run each in its own terminal.

### 1. Configure environment variables

Create `client/.env`:

```dotenv
VITE_BACKEND_URL=http://localhost:5000
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
```

Create `server/.env`:

```dotenv
PORT=5000
MONGODB_URI=your_mongodb_connection_string
CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_SECRET_KEY=your_cloudinary_api_secret
CLERK_WEBHOOK_SECRET=your_clerk_webhook_signing_secret
```

Configure Clerk to send user lifecycle events to the backend's `/webhooks` endpoint. Keep real credentials private; do not commit `.env` files or publish secrets.

### 2. Install dependencies

```bash
cd server
npm install
```

In another terminal:

```bash
cd client
npm install
```

### 3. Start the development servers

From `server/`:

```bash
npm run server
```

From `client/`:

```bash
npm run dev
```

Vite prints the local frontend URL when it starts. The API defaults to `http://localhost:5000`; its root route responds with `API WORKING`.

## Production build

Build the frontend from `client/`:

```bash
npm run build
```

To preview the production build locally:

```bash
npm run preview
```

Start the API from `server/` with:

```bash
npm start
```

## API overview

The Express API exposes route groups for:

- `/api/jobs` — job listings and job details
- `/api/users` — candidate profile, applications, and resume
- `/api/company` — company accounts, job postings, and applicant management
- `/webhooks` — Clerk user lifecycle webhook events

The client expects the API base URL in `VITE_BACKEND_URL`.

## License

No repository license is currently specified. Contact the repository owner before reusing this project.
