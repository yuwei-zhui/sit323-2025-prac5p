# SIT323 5.1P - Containerisation of a Simple Web Application Using Docker

This project is part of the SIT323 Cloud Native Application Development course. I learnt how to containerise a web application using Docker. The steps include creating a Dockerfile, building a Docker image, configuring Docker Compose, and pushing the final image to a registry.

## 📂 Repository

The code is hosted on GitHub:  
[https://github.com/yuwei-zhui/sit323-2025-prac5p](https://github.com/yuwei-zhui/sit323-2025-pracp5)

## 🛠️ Project Setup

### Step 1: Create and Initialize the GitHub Repository
- Create a new GitHub repository.
- Clone the repository locally.
- Navigate to my project directory.

### Step 2: Install Docker Desktop
- Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop).
- Verify installation by running:
  ```bash
  docker --version
  ```

### Step 3: Clone the Sample Web Application
- Clone my sample web application:
  ```bash
  git clone https://github.com/yuwei-zhui/sit323-2025-prac4c.git
  cd sit323-2025-prac4c
  ```

### Step 4: Create a Dockerfile
- In the root directory of my project, create a file named `Dockerfile`.
- Example content for a Node.js application:
  ```dockerfile
  # Use an official Node runtime as a parent image
  FROM node:14

  # Set the working directory in the container
  WORKDIR /app

  # Copy package.json and package-lock.json
  COPY package*.json ./

  # Install app dependencies
  RUN npm install

  # Bundle app source code
  COPY . .

  # Expose the port the app runs on
  EXPOSE 3323

  # Define the command to run my app
  CMD ["npm", "start"]
  ```

### Step 5: Build the Docker Image
- Build my Docker image with:
  ```bash
  docker build -t calculator:latest .
  ```

### Step 6: Create a Docker Compose File
- Create a `docker-compose.yml` file in my project directory.
- Example content:
  ```yaml
  services:
    web:
      build: .
      ports:
        - "3323:3323"
      environment:
        - NODE_ENV=production
  ```

### Step 7: Start the Docker Compose Environment
- Launch my application using Docker Compose:
  ```bash
  docker-compose up
  ```

### Step 8: Test the Application
- Open my browser and navigate to `http://localhost:3323` to ensure the application is running correctly.
- Alternatively, use tools like Postman to send requests and verify responses.

### Step 9: Push the Docker Image to a Registry
- Tag my Docker image:
  ```bash
  docker tag calculator:latest zhuiyuwei/calculator:latest
  ```
- Push the tagged image:
  ```bash
  docker push zhuiyuwei/calculator:latest
  ```

### Step 10: Push the Code to the GitHub Repository
- Commit my changes and push them to my repository:
  ```bash
  git add .
  git commit -m "Dockerised the web application and added Docker configuration files"
  git push origin main
  ```

## 💻 Usage

1. **Start the Docker Environment:**  
   Run `docker-compose up` to launch the application.

2. **Test the Application:**  
   Open the browser to interact with the application at the specified URL and port.

## 📕 Conclusion

This project demonstrates the containerisation process of a web application using Docker. It covers essential steps including creating Dockerfiles, building images, configuring Docker Compose, and deploying to a Docker registry. The process exemplifies best practices in cloud native development and containerisation.
