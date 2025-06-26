# Deployment Guide for Excel Analysis Platform

## Environment Configuration

The application is set up to work in both local development and production environments. The environment variables are configured to automatically detect the environment and use the appropriate URLs.

### Local Development

#### Frontend (React)

The frontend is configured to use the local backend API when running in development mode:

```
REACT_APP_API_URL=http://localhost:5000/api
```

#### Backend (Node.js/Express)

The backend is configured to use the following URLs in development mode:

```
CLIENT_URL=http://localhost:3000
API_URL=http://localhost:5000
```

### Production Environment

#### Frontend (React)

The frontend is configured to use the production backend API when running in production mode:

```
REACT_APP_API_URL=https://xl-analysis.onrender.com/api
```

#### Backend (Node.js/Express)

The backend is configured to use the following URLs in production mode:

```
PROD_CLIENT_URL=https://xl-analysis.vercel.app
PROD_API_URL=https://xl-analysis.onrender.com
```

## Running the Application

### Local Development

1. Start the backend server:

```bash
cd server
npm install
npm start
```

2. Start the frontend development server:

```bash
cd client
npm install
npm start
```

### Production Deployment

#### Frontend (Vercel)

The frontend is deployed on Vercel at: https://xl-analysis.vercel.app/

To deploy updates to the frontend:

1. Push your changes to your GitHub repository
2. Vercel will automatically deploy the changes

#### Backend (Render)

The backend is deployed on Render at: https://xl-analysis.onrender.com

To deploy updates to the backend:

1. Push your changes to your GitHub repository
2. Render will automatically deploy the changes

## Environment Variables

### Frontend (.env.production)

```
REACT_APP_GEMINI_API_KEY=your-gemini-api-key
REACT_APP_API_URL=https://xl-analysis.onrender.com/api
```

### Backend (.env)

```
PORT=5000
MONGODB_URI=your-mongodb-uri
JWT_SECRET=your-jwt-secret
CLIENT_URL=http://localhost:3000
API_URL=http://localhost:5000
SESSION_SECRET=your-session-secret
PROD_CLIENT_URL=https://xl-analysis.vercel.app
PROD_API_URL=https://xl-analysis.onrender.com
```

## Troubleshooting

### CORS Issues

If you encounter CORS issues, make sure the `CLIENT_URL` and `PROD_CLIENT_URL` environment variables are correctly set in your backend environment.

### Authentication Issues

If OAuth authentication is not working, check that the callback URLs in your OAuth providers (Google, GitHub) are correctly set to:

- Local: `http://localhost:5000/api/auth/google/callback` and `http://localhost:5000/api/auth/github/callback`
- Production: `https://xl-analysis.onrender.com/api/auth/google/callback` and `https://xl-analysis.onrender.com/api/auth/github/callback`