# Use an official Node.js runtime as the base image
FROM node:14 as build

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install the application dependencies
RUN npm install

# Bundle the app source inside the Docker image
COPY . .

# Build the app
RUN npm run build

# Start a new stage from scratch
FROM node:14

# Set the working directory in the container to /app
WORKDIR /app

# Install serve
RUN npm install -g serve

# Copy the build folder from build stage into the new stage
COPY --from=build /app/build .

# Expose port 5000 for the app to be accessible outside the Docker container
EXPOSE 12093

# Start serve
CMD ["serve", "-s", ".", "-l", "5000"]