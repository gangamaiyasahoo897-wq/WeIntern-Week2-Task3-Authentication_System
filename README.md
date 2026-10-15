# Task 3 — Authentication System (standalone)

This is an independent Task 3 project. It has its own server, frontend, database name, and dependencies; it does not depend on Task 2.

## Features
- Registration with username, email and minimum 8-character password
- bcrypt password hashing (12 rounds)
- Login validates credentials and returns a JWT with a two-hour expiry
- Protected `/api/auth/me` and `/api/protected` endpoints
- Logout clears the client token; because JWT is stateless, a copied token can remain valid until expiry
- Input validation and clear error messages

## Run on Windows
1. Install Node.js 18+ and MongoDB Community Server; start MongoDB.
2. Open this folder in VS Code.
3. Copy `.env.example` to `.env`; replace `JWT_SECRET` with a long random private value. Never upload `.env` to GitHub.
4. Run `npm install`, then `npm start`.
5. Open `http://localhost:5000`, register a demo account, sign in, verify the protected dashboard, then log out.

## Endpoints
- `GET /api/health` — health check
- `POST /api/auth/register` — register
- `POST /api/auth/login` — login and receive JWT
- `GET /api/auth/me` — current account (Bearer token required)
- `POST /api/auth/logout` — logout acknowledgement (Bearer token required)
- `GET /api/protected` — protected route (Bearer token required)

Security note: this is an educational demo. The token is stored in localStorage for simplicity. For production, use HTTPS, Secure/HttpOnly/SameSite cookies, rate limiting, appropriate CSRF protection and a server-side revocation/session strategy.
