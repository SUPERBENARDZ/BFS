# Full-Stack Authentication System

A complete full-stack authentication system built with FastAPI (Python), React (TypeScript), and PostgreSQL with JWT authentication, refresh token rotation, and Docker deployment.

## 🚀 Features

- **Backend**: FastAPI with SQLAlchemy ORM
- **Frontend**: React + TypeScript + TailwindCSS
- **Database**: PostgreSQL with automatic migrations
- **Authentication**: JWT with access/refresh tokens
- **Security**: Password hashing with bcrypt
- **Deployment**: Docker Compose ready
- **UI**: Beautiful, responsive design
- **Token Management**: Automatic refresh token rotation
- **Protected Routes**: Role-based access control

## 📁 Project Structure

```
.
├── backend/
│   ├── src/
│   │   ├── main.py          # FastAPI application
│   │   ├── auth.py          # Authentication logic
│   │   ├── models.py        # Database models
│   │   ├── database.py      # Database configuration
│   │   ├── schemas.py       # Pydantic schemas
│   │   └── config.py        # Configuration settings
│   ├── requirements.txt     # Python dependencies
│   └── Dockerfile          # Backend Docker configuration
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Login.tsx    # Login page
│   │   │   ├── Register.tsx # Registration page
│   │   │   └── Dashboard.tsx# Protected dashboard
│   │   ├── components/
│   │   │   ├── Input.tsx    # Input component
│   │   │   └── Button.tsx   # Button component
│   │   ├── api/
│   │   │   └── auth.ts      # API service
│   │   ├── App.tsx          # Main App component
│   │   └── main.tsx         # Entry point
│   ├── package.json         # Node dependencies
│   ├── tailwind.config.js   # Tailwind configuration
│   └── Dockerfile          # Frontend Docker configuration
├── docker-compose.yml       # Docker Compose configuration
├── database_schema.sql      # Database schema
└── README.md               # This file
```

## 🛠 Quick Start

### Prerequisites

- Docker and Docker Compose installed
- Git (to clone the repository)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd fullstack-auth-system
   ```

2. **Start the application**
   ```bash
   docker compose up --build
   ```

3. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:8000
   - API Documentation: http://localhost:8000/docs
   - pgAdmin: http://localhost:5050 (Optional)

## 📖 Usage

### Registration
1. Navigate to http://localhost:3000/register
2. Fill in your email, username, and password
3. Click "Create account"

### Login
1. Navigate to http://localhost:3000/login
2. Enter your email and password
3. Click "Sign in"

### Dashboard
After successful login, you'll be redirected to the dashboard where you can:
- View your profile information
- See account status
- Sign out

## 🔧 Configuration

### Environment Variables

Create a `.env` file based on `.env.example`:

```bash
cp .env.example .env
```

Key configuration options:
- `SECRET_KEY`: Change this for production
- `DATABASE_URL`: PostgreSQL connection string
- `FRONTEND_URL`: Frontend URL for CORS
- `ACCESS_TOKEN_EXPIRE_MINUTES`: Access token lifetime
- `REFRESH_TOKEN_EXPIRE_DAYS`: Refresh token lifetime

### Database

The database is automatically created and initialized when you run `docker compose up`. The schema is defined in `database_schema.sql`.

## 🔐 Security Features

- **Password Hashing**: Uses bcrypt for secure password storage
- **JWT Authentication**: Stateless authentication with JWT tokens
- **Refresh Token Rotation**: Automatic refresh token rotation for enhanced security
- **Token Expiration**: Configurable token expiration times
- **CORS Protection**: Proper CORS configuration
- **Input Validation**: Server-side validation for all inputs
- **SQL Injection Protection**: SQLAlchemy ORM prevents SQL injection

## 📚 API Endpoints

### Authentication
- `POST /register` - Register a new user
- `POST /login` - Authenticate user and return tokens
- `POST /refresh` - Refresh access token
- `POST /logout` - Logout user (revoke tokens)
- `GET /me` - Get current user information (protected)

### Documentation
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## 🐳 Docker Services

### Services
- **db**: PostgreSQL database (port 5432)
- **backend**: FastAPI application (port 8000)
- **frontend**: React application (port 3000)
- **pgadmin**: Database management UI (port 5050)

### Volumes
- `postgres_data`: Persistent database storage
- `pgadmin_data`: pgAdmin configuration

## 🧪 Development

### Running without Docker

For development, you can run services separately:

**Backend:**
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

**Frontend:**
```bash
cd frontend
npm install
npm start
```

**Database:**
```bash
# Start PostgreSQL locally
# Create database: auth_db
# Run: psql -d auth_db -f database_schema.sql
```

## 🚨 Production Deployment

1. **Update environment variables**
   - Change `SECRET_KEY` to a secure random string
   - Update database credentials
   - Configure production URLs

2. **SSL/TLS Setup**
   - Configure SSL certificates
   - Update CORS settings for HTTPS

3. **Database Security**
   - Use strong database passwords
   - Configure database firewall rules
   - Enable database backups

4. **Deploy**
   ```bash
   docker compose -f docker-compose.prod.yml up -d
   ```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📝 License

This project is licensed under the MIT License.

## 🆘 Troubleshooting

### Common Issues

1. **Port already in use**
   - Change ports in `docker-compose.yml`
   - Stop other services using the same ports

2. **Database connection failed**
   - Ensure PostgreSQL service is running
   - Check database credentials
   - Verify network connectivity

3. **Frontend not loading**
   - Check if backend is running
   - Verify API URL configuration
   - Check browser console for errors

4. **Build failures**
   - Clear Docker cache: `docker system prune -a`
   - Rebuild: `docker compose up --build --force-recreate`

### Logs

View logs for specific services:
```bash
docker compose logs backend
docker compose logs frontend
docker compose logs db
```

## 📞 Support

For issues and questions:
- Create an issue on GitHub
- Check the troubleshooting section
- Review the API documentation

---

Built with ❤️ using FastAPI, React, and PostgreSQL