# Two-Tier Flask App with MySQL — Manual Docker Networking

A two-tier web application (Flask app tier + MySQL database tier), containerized and connected entirely using Docker CLI commands and custom Docker networking — no docker-compose. Deployed on an AWS EC2 instance.

## 📌 Problem Statement

A two-tier application needs its app and database layers to communicate reliably while staying isolated from each other by default. This project sets up that communication manually with Docker CLI and a custom bridge network, to understand what tools like docker-compose automate under the hood.

## 🏗️ Architecture

- **App tier:** Flask application (cloned from GitHub), built into a custom Docker image
- **Database tier:** Official MySQL Docker image, pulled and run as a container
- **Docker network:** A custom bridge network connecting the two containers, allowing the Flask app to reach MySQL by container name
- **Host:** AWS EC2 instance (Docker installed via SSH)

## 🧰 Tech Stack

Docker · Docker Networking (CLI) · Flask · MySQL · AWS EC2

## ✅ Key Steps Performed

- Launched an EC2 instance and SSH'd in
- Installed Docker on the instance
- Pulled the official MySQL image (`docker pull mysql`)
- Cloned the Flask app from GitHub and built its Docker image
- Created a custom Docker network (`docker network create ...`)
- Ran both containers attached to that network, so the Flask app connects to MySQL using the container name as hostname
- Verified the app could reach and query the database over the custom network

## 📚 Key Learnings

- How Docker networking works at the CLI level — bridge networks, container-to-container DNS resolution by container name
- What docker-compose automates (network creation, service naming) versus doing it manually
- Two-tier application structure: separating app logic from data persistence
- Running and managing multi-container setups without an orchestration tool

**Yash**
Aspiring Cloud/IT Support Engineer | AWS Solutions Architect Associate (in progress)
