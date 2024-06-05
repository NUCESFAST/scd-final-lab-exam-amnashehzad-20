# Use an official Node.js runtime as the base image
FROM node:14

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install the application dependencies
RUN npm install



# Bundle the app source inside the Docker image
COPY . .

# Expose port 4001 for the app to be accessible outside the Docker container
EXPOSE 12092

# Define the command to run the app
CMD [ "node", "index.js" ]