# 1. Identify the different components of your application and break them down into microservices. This could include a backend API, frontend application, database (Which on  this case in Mongo db) etc.


# 2. CREATION OF DOCKER USING DOCKER FILE AND PUSH TO DOCKER HUB
# Docker image used
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

# 3. Create a Docker Compose file and define each microservice as a service, including its image, ports, volumes, environment variables, and any dependencies. You can also define custom networks for your services and specify which services should be connected to which network.

# 4. Build and run your Docker Compose file with the docker-compose up command. This will create and start all of your services as containers, running in the background.

# 5. Test your application by accessing it through the exposed ports or endpoints. Make sure to test communication between your microservices and ensure they are all functioning correctly.