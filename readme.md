# Creating Docker from Scratch and Deploying Sample Web App

This repository provides a simple guide on creating a Docker image from scratch and deploying a sample Flask web application using Docker.

## Prerequisites
- Docker must be installed and running on your machine. You can download Docker (https://www.docker.com/get-started) from the official website.

## Building a Dockerfile for a Sample Flask Application

To start, we will create a simple web app with only a home route that returns "Hello Sumit Sir!".

1. Setting up the Flask Application:
   - Open your favorite code editor and create a new directory for the project.
   - In this directory, create a new file named app.py and add the provided Python code.

2. Building the Dockerfile:
   - In the same directory as app.py, create a new file named Dockerfile (with no extension).
   - Open the Dockerfile and add the following instructions or commands for Docker to build our image:

   ```
   # Specify the base Image
   FROM python:3.11-slim

   # Working Directory Set up
   WORKDIR /app

   # Dependencies Installation
   RUN pip install flask==2.3

   # Copying Application Files to Container
   COPY . /app

   # Set Environment Variable
   ENV FLASK_APP=app.py

   # Default command when container starts
   CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
   ```

3. Building the Docker Image:
   - Open your terminal or command prompt and navigate to the project directory containing the Dockerfile.
   - Run the following command to build the Docker image:
     ```
     docker build -t sample-web-app .
     ```

4. Running the Docker Container:
   - After the image is successfully built, run the following command to start the Docker container:
     ```
     docker run -p 5000:5000 sample-web-app
     ```
     The -p 5000:5000 option maps the host's port 5000 to the container's port 5000.

5. Accessing the Web App:
   - Open your web browser and visit http://localhost:5000 to see the sample Flask web application running.
