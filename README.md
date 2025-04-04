# Trendy Threads Shopping Hub

Welcome to the **Trendy Threads Shopping Hub** project! This repository contains a Dockerized Node.js web application designed to provide a seamless shopping experience. The application is containerized using Docker, ensuring consistent deployment across various environments. It also integrates health checks to monitor the application's condition and sets up automatic restarts in the event of failure. Additionally, the Docker image is uploaded to a container registry for easier deployment and scaling.

## Table of Contents

- [Objective](#objective)
- [Prerequisites](#prerequisites)
- [Tools Required](#tools-required)
- [Setting Up the Project](#setting-up-the-project)
- [Creating the Server (`server.js`)](#creating-the-server-serverjs)
- [Creating the Static Website (`index.html`)](#creating-the-static-website-indexhtml)
- [Running the Project](#running-the-project)
- [Cloning the Web Application](#cloning-the-web-application)
- [Creating a Dockerfile](#creating-a-dockerfile)
- [Building the Docker Image](#building-the-docker-image)
- [Creating a Docker Compose File](#creating-a-docker-compose-file)
- [Starting the Docker Compose Environment](#starting-the-docker-compose-environment)
- [Testing the Application](#testing-the-application)
- [Pushing the Docker Image to Docker Hub](#pushing-the-docker-image-to-docker-hub)
- [Implementing Container Health Checks](#implementing-container-health-checks)
- [Contributing](#contributing)
- [License](#license)

## Objective

The goal of this project is to containerize a Node.js web application with Docker, ensuring consistent deployment across several environments. In addition, the project integrates health checks to monitor the application's condition and sets up automatic restarts in the event of failure. Finally, the Docker image is uploaded to a container registry for easier deployment and scaling.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- [Visual Studio Code (VS Code)](https://code.visualstudio.com/)
- [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/get-started/)

## Tools Required

- **Node.js**: JavaScript runtime built on Chrome's V8 JavaScript engine.
- **Git**: Version control system to track changes in source code.
- **Visual Studio Code**: Source-code editor developed by Microsoft.
- **Docker**: Platform to develop, ship, and run applications inside containers.

## Setting Up the Project

1. **Initialize a New Node.js Project**:

   Open the terminal and run:

   ```bash
   npm init
This command creates a package.json file to manage dependencies.

Install Express.js:

Install Express.js to help set up the server:

bash
Copy
Edit
npm install express
Creating the Server (server.js)
Create a server.js file responsible for:

Serving static website files (HTML, CSS, Images, JavaScript).

Handling routes.

Providing error handling.

Key Components:

Import Modules: Import express and path modules. The express module is used to create and manage the web server, and the path module constructs file paths correctly, ensuring compatibility across different operating systems.

Initialize Express Application: The app variable initializes an instance of an Express application, which is used to define server behavior, routes, and middleware.

Set Port: The PORT variable determines which port the server will listen on. process.env.PORT allows the server to use an environment-defined port if deployed on a hosting service.

Serve Static Files: The express.static() middleware makes all files inside the public directory available to users. This means that images, CSS files, and JavaScript files inside public can be accessed directly without needing explicit routes.

Handle 404 Errors: If a user requests a URL that does not exist, this middleware function is triggered. The response status is set to 404, indicating a "Not Found" error. The message 'Page not found' is sent to inform the user that the requested page does not exist.

Error Handling Middleware: The err.stack is logged to the console to help developers diagnose issues. A 500 response status is sent to indicate a general server error. This prevents the server from crashing due to unexpected issues.

Start the Server: The app.listen() method starts the server, making it listen for incoming requests on the specified PORT.

Creating the Static Website (index.html)
Develop the index.html file as the main interface for the Trendy Threads Shopping Hub, an online shopping platform showcasing different fashion and home decor categories. It is structured using HTML5 and styled with the Materialize CSS framework, ensuring a responsive and visually appealing design.

Key Components:

HTML5 Structure: Standard HTML boilerplate, including metadata such as character encoding, viewport settings for mobile responsiveness, and the page title.

Materialize CSS Integration: Links to the Materialize CSS framework to provide built-in styles and components for an enhanced user experience.

Navigation Bar: A responsive navigation bar with links to different sections of the website.

Main Content: Sections showcasing various product categories, each with images and descriptions.

Footer: Contains additional links and information about the website.

Running the Project
Start the server using:

bash
Copy
Edit
node server.js
Cloning the Web Application
To clone this web application, run:

bash
Copy
Edit
git clone https://github.com/your-username/trendy-threads.git
cd trendy-threads
Replace your-username with your GitHub username.

Creating a Dockerfile
Create a file named Dockerfile (without any file extension) in the root directory of your application and add the following content:

Dockerfile
Copy
Edit
# Use an official Node.js runtime as a parent image
FROM node:18-alpine

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the application files
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the application
CMD ["node", "server.js"]
Explanation:

FROM node:18-alpine: Uses the official Node.js image based on Alpine Linux, which is lightweight and secure.

WORKDIR /app: Sets the working directory inside the container to /app.

COPY package*.json ./: Copies package.json and package-lock.json to the container.

RUN npm install --production: Installs only production dependencies to keep the image lean.

COPY . .: Copies the rest of the application files to the container.

EXPOSE 3000: Documents that the container listens on port 3000.
