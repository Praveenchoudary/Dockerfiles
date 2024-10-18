# Stage 1: Build Stage
FROM node:18 AS build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the application code
COPY . .

# Stage 2: Final Stage
FROM node:18-slim

# Set the working directory for the final image
WORKDIR /app

# Copy installed dependencies and application code from the build stage
COPY --from=build /app .

# Expose the application port
EXPOSE 3000

# Command to run the application
CMD ["npm", "start"]
