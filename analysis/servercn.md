# ServerCN

## Overview
Backend component registry for Node.js & TypeScript. 
"shadcn/ui for backend" - copy-friendly, understandable building blocks.

## Components Available
- Authentication (JWT, Refresh Tokens, Argon2)
- Database (Mongoose/MongoDB)
- Input Validation (Zod)
- Error Handling
- Logging (Winston, Pino)
- File Upload (Cloudinary)
- Rate Limiter
- OAuth (GitHub, Google)
- Health Check

## Usage
```bash
npx servercn init          # Initialize project
npx servercn add auth      # Add auth component
npx servercn add logger    # Add logging
npx servercn list          # List all components
```

## Project Structure
```
src/
├── config/        # Environment
├── controllers/   # Request handlers
├── middlewares/   # Auth, Error handling
├── models/        # Database schemas
├── routes/        # API routes
├── services/      # Business logic
├── utils/         # Helpers
└── app.ts         # Entry point
```

## Relevance for Autoschei
- **MEDIUM**: Pattern for component registry
- Could inspire Go version for Autoschei modules
- Copy-paste friendly components = good DX

## Links
- https://github.com/akkaldhami/servercn
