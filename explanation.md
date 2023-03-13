1. CREATION OF DOCKER USING DOCKER FILE

# Use an official Node runtime as a parent image for the project
FROM node:latest

# Set the working directory to /app
WORKDIR /app

# Install MongoDB
RUN apt-get update && \
    apt-get install -y mongodb && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir -p /data/db && \
    chown -R mongodb:mongodb /data/db

# Start MongoDB service
CMD ["sudo", "service", "mongod", "start"]

# Copy the Client folder to the container
COPY client /myapp/client
COPY backend /myapp/backend

# Navigate to the Client folder
WORKDIR /app/client

# Install client dependencies
RUN npm install

# Start client app
CMD ["npm", "start"]

# Open a new terminal and run the same commands in the backend folder
RUN mkdir -p /app/backend
COPY ./Backend /app/backend

WORKDIR /app/backend

# Install backend dependencies
RUN npm install

# Start backend app
CMD ["npm", "start"]


