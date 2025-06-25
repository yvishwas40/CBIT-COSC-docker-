# Dockerized Flask App

This project demonstrates how to containerize a simple Flask application using Docker.

## Getting Started

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your machine
- (Optional) [Git](https://git-scm.com/) for cloning the repository

### Clone the Repository

```bash
git clone https://github.com/yvishwas40/CBIT-COSC-docker-.git-f
cd CBIT-COSC-docker-
```

### Build the Docker Image

```bash
docker build -t flask-docker-app .
```

### Run the Docker Container

```bash
docker run -d -p 5000:5000 --name flask-docker-app flask-docker-app
```

The app will be available at [http://localhost:5000](http://localhost:5000).

### Stopping & Removing the Container

```bash
docker stop flask-docker-app
docker rm flask-docker-app
```

## Application Code

The Flask app is in `app.py`:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return '<h1>Hello from COSC!</h1>'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000, debug=True)
```

## Dockerfile

A sample `Dockerfile` is included:

```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
```

