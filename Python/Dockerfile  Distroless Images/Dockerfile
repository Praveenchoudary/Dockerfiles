# Stage 1: Build Stage
FROM python:3.9-slim AS build-stage

# Set the working directory
WORKDIR /app

# Copy requirements file and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code into the container
COPY . .

# Stage 2: Final Stage with Distroless Image
FROM gcr.io/distroless/python3

# Set the working directory for the final image
WORKDIR /app

# Copy the installed packages and application code from the build stage
COPY --from=build-stage /app /app

# Expose port for the application
EXPOSE 5000

# Command to run the application
CMD ["app.py"]
