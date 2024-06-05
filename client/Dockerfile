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

# Build the app
RUN npm run build

# Use a smaller base image to reduce the final image size
FROM nginx:1.17-alpine

# Copy the build output to replace the default nginx contents.
COPY --from=0 /app/build /usr/share/nginx/html

# Expose port 80 for the app to be accessible outside the Docker container
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]