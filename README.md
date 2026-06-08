# NodeJS Blog Site Assignment

A server-rendered blog application built with Node.js, Express, EJS, MongoDB, and Mongoose. Public visitors can read paginated blog posts and search posts. Admin users can log in, create posts, edit posts, and delete posts from a protected dashboard.

This was built as a school assignment to practice Express apps, EJS layouts, MongoDB models, authentication, and admin CRUD workflows.

## Features

- Public blog home page with pagination
- Individual post pages
- Search by post title or body
- Admin login form
- JWT stored in an HTTP-only cookie for admin access
- Protected dashboard route
- Create, edit, and delete posts
- MongoDB session store with `connect-mongo`
- Password hashing with bcrypt
- Method override support for PUT and DELETE from forms
- EJS layouts and partials
- Static CSS and client-side JavaScript assets

## Tech Stack

- Node.js
- Express
- EJS
- express-ejs-layouts
- MongoDB
- Mongoose
- connect-mongo
- express-session
- cookie-parser
- bcrypt
- jsonwebtoken
- method-override
- dotenv
- nodemon

## Project Structure

```text
app.js
public/
  css/
  js/
server/
  config/
    db.js
  helpers/
  models/
    Post.js
    User.js
  routes/
    main.js
    admin.js
views/
  layouts/
  partials/
  admin/
```

## Environment Variables

Create `.env` in the project root:

```env
MONGO_URI=your_mongodb_connection_string
SESSION_SECRET=your_session_secret
JWT_SECRET=your_jwt_secret
```

The code also checks `JWTSECRET` as a fallback, but `JWT_SECRET` is clearer.

## How To Run

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Or start normally:

```bash
npm start
```

Open:

```text
http://localhost:4000
```

## Public Routes

```text
GET  /              Blog home page with pagination
GET  /?page=2       Next page of posts
GET  /post/:id      Single post page
POST /search        Search posts
```

## Admin Routes

```text
GET    /admin             Admin login page
POST   /admin             Log in
GET    /dashboard         Protected dashboard
POST   /register          Register an admin user
GET    /add-post          New post form
POST   /add-post          Create post
GET    /edit-post/:id     Edit post form
PUT    /edit-post/:id     Update post
DELETE /delete-post/:id   Delete post
GET    /logout            Log out
```

## How It Works

1. Public routes read posts from MongoDB and render EJS templates.
2. Search strips special characters and uses a case-insensitive MongoDB regex search.
3. Admin login compares the submitted password against the hashed password in MongoDB.
4. A signed JWT is stored in an HTTP-only cookie.
5. Protected admin routes verify the token before allowing dashboard and post changes.
6. Method override lets HTML forms submit update and delete actions.

## Notes

- There is no public registration page; the `/register` route exists as a POST route for creating an admin user.
- A working MongoDB connection is required for posts, users, and sessions.
- This is a coursework project and would need additional validation, CSRF protection, and deployment hardening for production.

## What I Practiced

- Building server-rendered Express apps
- Organizing routes, models, views, layouts, and partials
- Creating admin CRUD workflows
- Hashing and verifying passwords
- Using JWT cookies for protected routes
- Connecting sessions and app data to MongoDB
