# RecruitEdge API Gateway

The API Gateway serves as the single entry point for all frontend and client requests in the RecruitEdge recruitment management platform.

## Port Map
| Service | Port | Description |
| :--- | :--- | :--- |
| **API Gateway** | `8080` | Entry point for Web / Mobile / React frontend |
| **Backend Main** | `8081` | Core business services (Auth, Jobs, Candidates, Interviews, Gemini AI) |

## Route Mapping
All client requests hitting `http://localhost:8080` are forwarded to downstream microservices / backend:

- `/api/auth/**` &rarr; `http://localhost:8081` (Authentication, Google OAuth, JWT refresh)
- `/api/user/**` &rarr; `http://localhost:8081` (User management and profiles)
- `/api/job/**` &rarr; `http://localhost:8081` (Job postings, browse, search)
- `/api/candidate/**` &rarr; `http://localhost:8081` (Candidate applications and profiles)
- `/api/interview/**` &rarr; `http://localhost:8081` (Interview scheduling and reviews)
- `/api/aiinterview/**` &rarr; `http://localhost:8081` (AI Mock Interview & Gemini Question Generation)

## Running Locally

1. Start **Backend Main** (Port 8081):
   ```bash
   cd backend/main
   ./mvnw spring-boot:run
   ```

2. Start **API Gateway** (Port 8080):
   ```bash
   cd backend/api-gateway
   ./mvnw spring-boot:run
   ```

3. Start **Frontend**:
   ```bash
   cd frontend
   npm run dev
   ```
