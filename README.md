# 6b-me

## Setup

1. Install dependencies:

```bash
pnpm install
```

2. Create a `.env` file:

```env
PORT=3000
MONGO_URI=your_mongo_connection_string
JWT_SECRET=your_super_secret_key
JWT_EXPIRES_IN=1d
SOLARWINDS_TOKEN=optional
```

3. Run server:

```bash
pnpm dev
```

## Auth APIs

- `POST /users/register` → Register a user
- `POST /users/login` → Login and receive JWT token
- `GET /users/me` → Protected route (requires `Authorization: Bearer <token>`)

### Register payload

```json
{
  "fullName": "Jane Doe",
  "email": "jane@example.com",
  "password": "strongPassword123"
}
```

### Register validation

- `fullName` is required (`"Full name is required"`).
- `email` is required (`"Email is required"`).
- `email` must be valid format (`"Please provide a valid email address"`).
- `password` is required (`"Password is required"`).
- `password` must be at least 6 characters (`"Password must be at least 6 characters long"`).

### Login payload

```json
{
  "email": "jane@example.com",
  "password": "strongPassword123"
}
```

`accountNumber` has been removed from the user model and auth API payloads/responses.
