# 1. Identify the different components of your application and break them down into microservices. 
This could include a backend API, frontend application, database (Which on  this case in Mongo db) etc.

# 2. Creation of docker using docker file and push to docker hub
# Docker image used:
FROM node:16.18.1-alpine

# Create app directory
WORKDIR /usr/src/app/backend

# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the current directory . in the project to the working directory /usr/src/app/backend in the image.
COPY . .

# dd metadata to the image to describe that the container is listening on port 5000
EXPOSE 5000
CMD [ "npm", "start" ]

# 3. Create a Docker Compose file and define each microservice as a service.
This includes its image, ports, volumes, environment variables, and any dependencies. You can also define custom networks for your services and specify which services should be connected to which network.

# 4. Build and run your Docker Compose file with the docker-compose up command. 
This will create and start all of your services as containers, running in the background.

# 5. Test your application.
This can be done by accessing it through the exposed ports or endpoints. Make sure to test communication between your microservices and ensure they are all functioning correctly.

# IP3 Assignment

I have managed to create an automation using ansible using the following steps:

# 6 Creating a Vagrant File
This file will contain the configuration for your virtual machine. The virtual machine of our chice is UBUNTU.

# 7 Create a new playbook file
This file defines the tasks you want to run on the virtual machine which on this case we will run the following tasks: 
i.   Install Git (For cloning this repo to our ubuntu VM).
ii.  Install Docker 
iii. Install Docker-compose for running the docker-compose file
iv.  Run git clone command
v.   Run docker compose command
