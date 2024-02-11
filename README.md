# Docker Python CLI App

Python simple CLI app in Docker container.

## Run the Application

1. Build the Docker image:
   ```sh
   docker build -t goodbuy-app .
   ```
2. Run the Docker container:
   ```sh
    docker run goodbuy-app
    ```

[Docker Python CLI Tutorial](https://chat.openai.com/share/23e98a9b-65f4-4b5d-b148-5de591d426b2)

Certainly! Creating a simple Dockerized Python CLI application involves a few steps. Below, I'll guide you through creating the Python app `goodbuy.py` and setting up a Docker container using a Python Alpine image for a lightweight deployment. Here's how you can do it:

### 1. Create Your Python Application

First, let's create the Python CLI application you mentioned, `goodbuy.py`. This script will be very basic, but you can customize it as needed later.

**`goodbuy.py`**:
```python
#!/usr/bin/env python3

def main():
    print("Goodbye! Have a great day!")

if __name__ == "__main__":
    main()
```

This script simply prints a farewell message when executed.

### 2. Write the Dockerfile

Next, you will create a `Dockerfile` that specifies how to build the Docker image for your application. Using the Python Alpine image is a great choice for keeping the image size small.

**`Dockerfile`**:
```dockerfile
# Use an official Python runtime as a parent image
FROM python:3.9-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Make the script executable
RUN chmod +x goodbuy.py

# Define the command to run your script
CMD [ "python", "./goodbuy.py" ]
```

This `Dockerfile` does the following:
- Starts with the Python 3.9 image based on Alpine Linux for a minimal footprint.
- Sets the working directory inside the container to `/usr/src/app`.
- Copies everything from your project directory (where the `Dockerfile` is located) into the container.
- Makes your `goodbuy.py` script executable.
- Specifies the command to run your script when the container starts.

### 3. Build and Run Your Docker Container

With your `goodbuy.py` and `Dockerfile` ready, you can now build and run your Docker container. First, ensure Docker is installed and running on your system.

Open a terminal and navigate to the directory containing your `Dockerfile` and `goodbuy.py` script. Then, execute the following commands:

```sh
# Build your Docker image
docker build -t goodbuy-app .

# Run your Docker container
docker run goodbuy-app
```

The `docker build` command builds the Docker image from your `Dockerfile`, tagging it (`-t`) with the name `goodbuy-app`. The `docker run` command then starts a container based on this image. When the container runs, it should execute your Python script and print the farewell message.

This setup provides a basic foundation for a Dockerized Python CLI application. You can expand your Python script with more functionality and adjust the `Dockerfile` as needed for additional dependencies or configuration.