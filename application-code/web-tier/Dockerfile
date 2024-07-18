# Stage 1: Build Node.js application
FROM node:16-alpine AS build-stage

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install npm dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Build the Node.js application (if necessary)
RUN npm run build

# Stage 2: Setup Nginx to serve Node.js application
FROM nginx:alpine

# Copy the built application code from the previous stage
COPY --from=build-stage /usr/src/app/build /usr/share/nginx/html

# Copy custom nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80 (default HTTP port)
EXPOSE 80

# Command to start Nginx
CMD ["nginx", "-g", "daemon off;"]
