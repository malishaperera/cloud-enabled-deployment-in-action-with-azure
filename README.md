# ☁️ Cloud Enabled Deployment in Action with Microsoft Azure

##  This repository contains four projects:

| Service                | Technology               | Database / Storage               | Port | Description                                              |
| ---------------------- | ------------------------ | -------------------------------- | ---- | -------------------------------------------------------- |
| 🏫 **Course Service**  | Spring Boot              | Azure MySQL                      | 8081 | Manages courses, auto-generates tables via JPA           |
| 🎓 **Student Service** | Spring Boot              | MongoDB (Docker)     | 8082 | Manages student records with CRUD operations             |
| 🗂️ **Media Service**  | Spring Boot              | Local Disk / Optional Azure Blob | 8083 | Handles file uploads/downloads with flexible storage     |
| 💻 **Frontend App**    | React + TypeScript + MUI | N/A                              | 5173 | Displays Courses, Students, Media sections interactively |

---
## 🎥 Demo Video

📌 Watch the demonstration on Google Drive: [Demo Video](https://drive.google.com/file/d/1wzfeZz06WHzsnBNMc5WXRdqbXg3CXsn5/view)

[//]: # ([![Watch the video]&#40;https://drive.google.com/file/d/1wzfeZz06WHzsnBNMc5WXRdqbXg3CXsn5/view&#41;)
## 🚀 Backend Services Details

---
### 1️⃣ Course Service (Azure MySQL)
- Entity: Course(id, name, duration)

    - Endpoints:
      -  GET `/courses` → list all courses
      -  GET `/courses/{id}` → fetch course by ID
      -  POST `/courses` → add new course
      -  DELETE `/courses/{id}` → remove course
      
- Database: Azure MySQL Flexible Server

- Notes: JPA auto-creates the `course` table
- Active Spring Profile: `azure`
--- 
### 2️⃣ Student Service (MongoDB Docker)

- Document: Student(registrationNumber, fullName, address, contact, email)

  - Endpoints:

    - GET /students → list all students

    - GET /students/{id} → fetch student by ID
  
    - POST /students → add new student
  
    - DELETE /students/{id} → remove student

- Database: MongoDB running in Docker
- Run MongoDB in Docker
    ```bash
   docker run -d \
  --name mongo-dev \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=mongo \
  -p 16000:27017 \
  -v mongo-data:/data/db \
  mongo:7.0.23

    ```

---
### 3️⃣ Media Service

- Resource: files

  - Endpoints:
    - POST /files → upload files

    - GET /files → list all files

    - GET /files/{id} → download file

    - DELETE /files/{id} → remove file

- Storage: Local disk (./data/media) or optional Azure Blob

- Notes: Configurable via environment variable MEDIA_STORAGE_DIR
- Server port: 8083

---
### 💻 Frontend (frontend-app)

- **Framework:** React + TypeScript + MUI + Axios + Vite
- **Sections:** Courses, Students, Media

  #### 🚀 Scripts
  ```bash
  # Install dependencies
  npm install
  
  # Run Vite development server
  npm run dev
  
  # Build production app
  npm run build
  
  # Preview built app
  npm run preview
  ```
---
### 🛠️ Build & Run
#### 📌 Backend
```bash
# Build all backend services (skip tests)
mvn -q -e -DskipTests package
```
#### 💻Frontend
```bash
# Navigate to frontend-app
cd frontend-app
npm install
npm run dev
```
---
### 🔧 Key Notes

- Ensure Azure MySQL credentials are correct in application-azure.properties.

- Ensure MongoDB Docker container is running for student-service.


- Media Service can be extended to Azure Blob Storage for production.

- Active profile in Spring Boot: azure

---

### 📜 License

#### This project is licensed under the MIT License – see the [LICENSE](https://github.com/malishaperera/cloud-enabled-deployment-in-action-with-azure/blob/main/LICENSE) file for details.

