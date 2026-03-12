🐳 Dockerized Flask Microblog (DevOps Practice)

->This repository contains a **Dockerized version** of a Flask Microblog  application.
->The purpose of this project is to practice **Docker and Docker Compose** by containerizing an existing application and making it reproducible and portable.

 ⚠️ This project focuses on **DevOps work (Dockerization)**, not application development.

---

## 🚀 Tech Stack

- **Backend:** Python (Flask)
- **Database:** SQLite
- **Containerization:** Docker, Docker Compose
- **Port:** 5000

---

## 📂 Project Objective

The main goals of this project were:

- Understand how to analyze  an existing codebase
- Write a **Dockerfile** for a Flask application
- Use **Docker Compose** to manage configuration
- Correctly handle **SQLite database persistence**
- Follow DevOps best practices (ports, volumes, env vars)

## 🛠 What I Did (DevOps Work)

### Dockerfile
- Used a lightweight Python base image
- Installed dependencies using `requirements.txt`
- Copied application source code into the container
- Exposed port `5000`
- Started the app using `flask run --host=0.0.0.0`

### docker-compose.yml
- Built the image using Dockerfile
- Mapped container port `5000` to host port `5000`
- Used environment variables for Flask configuration
- Persisted SQLite data using Docker volumes
- Enabled automatic restart for container stability

## 🧠 Important SQLite Learning (Real DevOps Fix)

Initially, the application did **not work correctly** because the SQLite database
was mounted as a **file instead of a directory**.

### ❌ Wrong Approach (Not Working)
...yaml
volumes:
  - sqlite_data:/app/app.db
✅ Correct Approach (Working)
volumes:
  - sqlite_data:/app/data
DATABASE_URL: sqlite:////app/data/app.db

Why This Works:
-Docker volumes are designed for directories, not single files
-SQLite creates and manages its own database file
-Mounting a folder allows SQLite to safely create and use the database
-Explicitly setting DATABASE_URL ensures Flask knows the exact DB location


▶️ How to Run the Project:-
   1️⃣ Clone the repository:
        git clone <your-repository-url>
        cd <your-repo-folder>
        
   2️⃣ Build and run containers:
         docker-compose up --build
   
   3️⃣ Open in browser:
         http://localhost:5000

📦 Data Persistence:
   
    The application uses SQLite, which is file-based
    A Docker volume is used to ensure data is not lost when containers restart

📚 What I Learned:

     -How DevOps engineers containerize existing applications
     
     -Writing clean and efficient Dockerfiles
     
     -Using Docker Compose for configuration management
     
     -Port mapping and container networking
      
     -Handling SQLite correctly inside Docker
     
     -Debugging real-world container issues

     
🔗 Original Project (Credit):-
     
        This project is based on an open-source Flask application.
     
     Original Repository: https://github.com/miguelgrinberg/microblog

All application logic belongs to the original author.

My contribution is Dockerization and DevOps-related configuration only.

You can compare this repository with the original one to see the DevOps changes.

👤 Author:

Dockerized and documented by a DevOps learner for practice, learning, and portfolio use.

⭐ If you find this project helpful, feel free to star the repository!
