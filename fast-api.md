### Overview

    FastAPI: A popular Python framework for building APIs. It supports typing, has built-in Swagger documentation for testing APIs, and is easy to use.
    
    AWS Cloud9: An online IDE that's great for deploying microservices to AWS. It provides an environment to write, run, and debug your code.

    AWS App Runner: A service to deploy and host containerized web applications or APIs easily, with support for continuous delivery.

# Key Steps to Deploy a FastAPI Microservice with AWS App Runner

### 1. Set Up Your FastAPI Project

Install FastAPI and Uvicorn (a server for running FastAPI).

Write your API code. For example: python-code

```
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, Duke!"}

@app.get("/add")
def add(a: int, b: int):
    return {"result": a + b}

# Run the app on port 8080
# Command to run: python main.py

```

### 2. Local Development

-> Use AWS Cloud9 or any environment.

-> Create a Python virtual environment:

```
python3 -m venv venv
source venv/bin/activate
pip install fastapi uvicorn
```

-> Run the service locally:
```
python main.py
```
-> Test using curl or a browser:

```
curl http://localhost:8080
curl "http://localhost:8080/add?a=2&b=3"

```

### 3. Prepare for Deployment

-> Add a `requirements.txt` file:

````
fastapi
uvicorn
````

-> Include a ```Makefile```for automation (optional).

### 4. Deploy with AWS App Runner

    Step 1: Go to AWS App Runner in the AWS Management Console.

    Step 2: Choose Create a service and select Source code repository.

    Step 3: Connect your GitHub repo (e.g., noahgift/fastapi) to App Runner.

    Step 4: Use the following build commands:

          - Install dependencies: pip install -r requirements.txt

          - Run the app: python main.py
    
    Step 5: Choose Manual deployment or Automatic deployment for continuous delivery.

    Step 6: Click Create and Deploy.

### 5. Testing in App Runner


-> App Runner provides a fully hosted URL (e.g.,`https://<your-service>.awsapprunner.com`).

-> Use the `/docs` route to access Swagger UI for interactive testing.

     - Example: Add two numbers using /add?a=2&b=3.

-> Check the API responses and the curl commands from Swagger.

# Why Use This Setup?

`FastAPI:` Simple, fast, and has built-in documentation.

`AWS Cloud9:` Convenient for development in the AWS ecosystem.

`AWS App Runner:`Automated deployment with built-in scalability and secure HTTPS URLs.

By following these steps, you can deploy a simple yet powerful FastAPI microservice and make it production-ready using AWS App Runner.
