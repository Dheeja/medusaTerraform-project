# Use Node.js as the base image (ensure the version matches your app's Node version)
FROM node:16-alpine

# Install necessary system dependencies (if required by npm packages)
RUN apk add --no-cache python3 make g++

# Set working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json for installing dependencies
COPY package.json ./

# Ensure safe permissions to avoid permission-related issues during npm install
RUN npm config set unsafe-perm true

# Install dependencies for the Medusa app
RUN npm install --legacy-peer-deps

# Copy the rest of the application code
COPY . .

# Expose the port your Medusa app is running on (this is set to 80 as per the ECS task definition)
EXPOSE 80

# Build your Medusa app (if needed) - optional, depends on your specific Medusa setup
# RUN npm run build  # Uncomment if you have a build process

# Start the Medusa application (make sure to replace with your specific start command)
CMD ["npm", "run", "start"]


# notec