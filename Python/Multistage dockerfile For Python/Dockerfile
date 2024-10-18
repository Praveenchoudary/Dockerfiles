# Stage 1: Build Stage
FROM python:3.9-slim AS build-stage

# Set working directory inside the container
WORKDIR /app

# Copy the requirements file to the container
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the source code to the container
COPY . .

# Stage 2: Final Stage (Slimmer Image)
FROM python:3.9-alpine AS final-stage

# Set working directory in the final image
WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=build-stage /app /app

# Expose port 5000 for the Flask app
EXPOSE 5000

# Define the command to run the application
CMD ["python", "app.py"]
