* a portable image
* eg from the Docker docs
---
#### Dockerfile
```
# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

#### requirements.txt
```
Flask
Redis
```
#### app.py
``` python
from flask import Flask
from redis import Redis, RedisError
import os
import socket

# Connect to Redis
redis = Redis(host="redis", db=0, socket_connect_timeout=2, socket_timeout=2)

app = Flask(__name__)

@app.route("/")
def hello():
    try:
        visits = redis.incr("counter")
    except RedisError:
        visits = "<i>cannot connect to Redis, counter disabled</i>"

    html = "<h3>Hello {name}!</h3>" \
           "<b>Hostname:</b> {hostname}<br/>" \
           "<b>Visits:</b> {visits}"
    return html.format(name=os.getenv("NAME", "world"), hostname=socket.gethostname(), visits=visits)

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=80)
```

* Build the image from the Dockerfile
```
docker build -t nameImage
```

* Start a container mapping the **machine's port 4000** to the **container's port 80**
```
docker run -p 4000:80 nameImage
```
* Start the container in the detached mode/background
```
docker run -d -p 4000:80 nameImage
```

### docker-compose.yml
```yml
version: "3"
services:
  web:
    # replace username/repo:tag with your name and image details
    image: username/repo:tag
    deploy:
      replicas: 5
      resources:
        limits:
          cpus: "0.1"
          memory: 50M
      restart_policy:
        condition: on-failure
    ports:
      - "4000:80"
    networks:
      - webnet
networks:
  webnet:
```
##### Explanation
* pull the image from the repo specified
* create 5 instances of that image
    * limit each to at most 10% CPU
    * limit each to at most 50MB RAM
* if one of them fails, restart it
* map the port 4000 of the host machine to port 80 or the container
* containers share port 80 using a load-balanced network("webnet")
* set default settings for the "webnet" network


---