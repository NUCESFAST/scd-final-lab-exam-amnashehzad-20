# Use an official Node.js runtime as the base image
FROM node:14

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install the application dependencies
RUN npm install

# install serve
RUN npm install -g serve

# Copy the rest of the application code to the working directory
COPY . .

# Build the application
RUN npm run build

# command to run the application
CMD ["serve", "-s", "build"]