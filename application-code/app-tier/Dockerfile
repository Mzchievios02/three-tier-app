# Use an official Node base image
FROM node:16-alpine

# Set working directory
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of your application code
COPY . .

# Expose port
EXPOSE 4000

# Start the application
CMD ["npm", "start"]
