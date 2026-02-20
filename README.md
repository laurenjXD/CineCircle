# CineCircle - Collaborative Movie Rating & Discussion System

A modern, full-stack web application for rating movies, writing reviews, and engaging in community discussions.

## 🎬 Features

- User Authentication with JWT
- Movie CRUD Operations (Admin)
- 5-Star Rating System
- Reviews & Threaded Discussions
- Responsive Dark Mode UI
- Kubernetes Deployment with Auto-Scaling

## 🏗️ Tech Stack

**Frontend:** React 18, Tailwind CSS, Framer Motion, React Router
**Backend:** Node.js, Express.js, MySQL, Sequelize ORM
**DevOps:** Docker, Kubernetes, HPA

## 🚀 Quick Start

### Using Docker Compose (Recommended)

```bash
docker-compose up --build
```

Access: http://localhost:3000

### Manual Setup

**Backend:**
```bash
cd backend
npm install
cp .env.example .env
npm run dev
```

**Frontend:**
```bash
cd frontend
npm install
npm run dev
```

### Kubernetes Deployment

```bash
# Build images
docker build -t cinecircle-backend:latest ./backend
docker build -t cinecircle-frontend:latest ./frontend

# Deploy
kubectl apply -f kubernetes/namespace.yaml
kubectl apply -f kubernetes/mysql-pv.yaml
kubectl apply -f kubernetes/mysql-deployment.yaml
kubectl apply -f kubernetes/backend-deployment.yaml
kubectl apply -f kubernetes/frontend-deployment.yaml

# Check status
kubectl get all -n cinecircle
```

## 📊 API Endpoints

### Auth
- POST /api/auth/register
- POST /api/auth/login
- GET /api/auth/profile

### Movies
- GET /api/movies (filters: genre, year, search, sort)
- GET /api/movies/:id
- POST /api/movies (admin)
- PUT /api/movies/:id (admin)
- DELETE /api/movies/:id (admin)

### Ratings
- POST /api/ratings
- GET /api/ratings/movie/:movieId

### Reviews
- POST /api/reviews
- GET /api/reviews/movie/:movieId
- PUT /api/reviews/:reviewId
- DELETE /api/reviews/:reviewId

### Comments
- POST /api/comments
- GET /api/comments/review/:reviewId

## 🔧 Kubernetes Demonstrations

**Self-Healing:**
```bash
kubectl delete pod <pod-name> -n cinecircle
kubectl get pods -n cinecircle --watch
```

**Scaling:**
```bash
kubectl scale deployment backend --replicas=5 -n cinecircle
kubectl get hpa -n cinecircle
```

**Rolling Update:**
```bash
kubectl set image deployment/backend backend=cinecircle-backend:v2 -n cinecircle
kubectl rollout status deployment/backend -n cinecircle
```

**Rollback:**
```bash
kubectl rollout undo deployment/backend -n cinecircle
```

## 📦 Project Structure

```
cinecircle/
├── backend/          # Node.js API
├── frontend/         # React application
├── kubernetes/       # K8s manifests
└── docker-compose.yml
```

## 🎨 UI Features

- Beautiful dark cinema theme
- Responsive design
- Smooth animations
- Card-based layouts
- Interactive star ratings
- Threaded comment system

## 📝 Default Credentials

Create admin user via registration, then update role in database:
```sql
UPDATE users SET role='admin' WHERE email='your@email.com';
```

## 🤝 Author

**Lauren** - Full-stack Developer

## 📄 License

MIT License

---

**Educational Project** - Demonstrates full-stack development with Kubernetes orchestration.
