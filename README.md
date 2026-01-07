# JWT Auth API (.NET)

A minimal ASP.NET Core Web API that implements user registration, login, and role-based authorization using JWT tokens and BCrypt password hashing. It exposes protected endpoints to demonstrate authentication and authorization in a realistic microservice-style setup. [file:160][file:162]

## Features

- Register new users with hashed passwords (BCrypt)
- Log in and receive a signed JWT access token
- Role-based access control (e.g., `Admin` vs `User`)
- Protected `/me` endpoint that reads user info from JWT claims
- Protected `/admin-only` endpoint restricted to `Admin` role users [file:160]

## Tech stack

- ASP.NET Core minimal APIs (.NET 8)
- JWT Bearer Authentication (`Microsoft.AspNetCore.Authentication.JwtBearer`)
- `System.IdentityModel.Tokens.Jwt` for token creation and validation
- `BCrypt.Net-Next` for password hashing [file:160][file:162]

## Quick start

1. **Clone the repo**

```bash
git clone <your-repo-url>
cd AuthApi
dotnet restore

2. Run the API

dotnet run

3. Register a user

POST /register
Content-Type: application/json

{
  "username": "testuser",
  "password": "Test123!",
  "role": "Admin"
}

4. Log in

POST /login
Content-Type: application/json

{
  "username": "testuser",
  "password": "Test123!"
}

5. Call protected endpoints

GET /me
Authorization: Bearer <token>

GET /admin-only
Authorization: Bearer <token>

Configuration

JWT options are configured in appsettings.json under the Jwt section:

json

"Jwt": {
  "Key": "a-VERY-long-secret-key-change-me",
  "Issuer": "AuthApi",
  "Audience": "AuthApiClients",
  "ExpiresMinutes": 60
}

Change these values for your environment before deploying. [file:162]

undefined


