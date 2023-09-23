Creating Docker from scratch and Deploying sample web app

1. Building a Dockerfile for a Sample Flask Application
This will be a simple web app with only home route that will return Hello Sumit Sir .
Let's start by setting up the Flask application. Open your favorite code editor and create a new directory for your project. In this directory, create a new file named app.py and add the following Python code:
app.py file Now, let's build the Dockerfile.
In the same directory as your app.py,  create a new file named Dockerfile (with no extension). This is  where we will write the instructions or command for Docker to build our image.
#1. Specify the base Image
FROM python:3.11-slim
#2. Working Directory Set up
WORKDIR /app 
#3. Dependencies Installation
RUN pip install flask==2.3
#4. Copying Application Files to Container
COPY . /app
#5. Set Environment Variable
ENV FLASK_APP=app.py
#6. Default command when container start
CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
our Dockerfile is ready. It should look like this:
Docker File2. Building and Running Docker Image
In terminal navigate to directory where your Dockerfile is located. Now, run the following command to create an image named venky-web:v1 (where venky-web is the name of the image and we can name any name and v1 is associated tag):
docker build . -t venky-web:v1
In the command , the dot (.) after the build command indicates context of current directory. We're using the -t flag to tag the image with the name venky-web and version v1.
To make sure image has been created successfully run the following command:
docker image ls
the output will look like -
