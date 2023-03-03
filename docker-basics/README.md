# Beginner's Guide to Docker Containers with Nginx

Docker is a powerful tool that allows you to create, deploy, and run applications inside containers. In this guide, we will explore Docker containers and how to use the Nginx Docker container.

## What is Docker?

Docker is a platform for building, shipping, and running applications in containers. A container is a lightweight and portable executable package that contains everything needed to run an application, including the code, libraries, and system tools.

## What is Nginx?

Nginx is a popular web server that can also be used as a reverse proxy, load balancer, and HTTP cache. It is known for its high performance, stability, and low resource usage.

## How to Use the Nginx Docker Container

Using the Nginx Docker container is simple and straightforward. Here are the steps:

1. Install Docker on your system. You can download Docker from the official website: [https://www.docker.com/](https://www.docker.com/).

2. Open a terminal or command prompt and run the following command to download the Nginx Docker image:

```
docker pull nginx
```

This command will download the latest version of the Nginx Docker image from Docker Hub.

3. Run the following command to start a new Nginx Docker container:

```
docker run --name mynginx -p 8080:80 -d nginx
```

This command will start a new Docker container with the name "mynginx" and map port 8080 on your host machine to port 80 in the Docker container. The "-d" option runs the container in the background as a daemon.

4. Verify that the Nginx container is running by accessing the Nginx welcome page in your web browser. Open a web browser and go to the following URL:

```
http://localhost:8080
```

If everything is working correctly, you should see the Nginx welcome page.

5. To stop the Nginx Docker container, run the following command:

```
docker stop mynginx
```

This command will stop the "mynginx" container.

## Customizing the Nginx Container

The Nginx Docker container comes with a default landing page. You can customize this landing page by creating your own HTML file and replacing the default file in the container. There are different ways to achieve this, and here are three common methods:

### Method 1: Using a Mounted Volume

With this method, you mount a local directory as a volume in the Nginx Docker container. This allows you to modify the HTML file on your local machine, and the changes will be reflected in the container.

Here are the steps:

1. Create a new directory on your local machine and create an HTML file with your custom landing page content.

```
mkdir mynginx
cd mynginx
echo "<h1>Welcome to my custom landing page!</h1>" > index.html
```

2. Run the following command to start a new Nginx Docker container and mount the local directory as a volume:

```
docker run --name mynginx -p 8080:80 -v $(pwd):/usr/share/nginx/html -d nginx
```

This command will start a new Docker container with the name "mynginx," map port 8080 on your host machine to port 80 in the Docker container, and mount the current directory as a volume in the container. The "-d" option runs the container in the background as a daemon.

3. Verify that the new landing page is working by accessing the Nginx welcome page in your web browser. Open a web browser and go to the following URL:

```
http://localhost:8080
```

If everything is working correctly, you should see your custom landing page.

4. To stop the Nginx Docker container, run the following command:

```
docker stop mynginx
```

This command will stop the "mynginx" container.

### Method 21: Building a Custom Docker Image

With this method, you create a custom Docker image by writing a Dockerfile that copies your HTML file into the container. This method requires you to build the custom image every time you make a change.

Here are the steps:

1. Create a new directory and create an HTML file with your custom landing page content.

```
mkdir mynginx
cd mynginx
echo "<h1>Welcome to my custom landing page!</h1>" > index.html
```

2. Create a Dockerfile with the following contents:

```
FROM nginx
COPY index.html /usr/share/nginx/html/
```

This Dockerfile is based on the official Nginx Docker image and copies your HTML file into the container.

3. Run the following command to build the custom Docker image:

```
docker build -t mynginx .
```

This command will build the Docker image with the tag "mynginx" using the Dockerfile in the current directory.

4. Run the following command to start a new Nginx Docker container using the custom image:

```
docker run --name mynginx -p 8080:80 -d mynginx
```

This command will start a new Docker container with the name "mynginx," map port 8080 on your host machine to port 80 in the Docker container, and use the custom image. The "-d" option runs the container in the background as a daemon.

5. Verify that the new landing page is working by accessing the Nginx welcome page in your web browser. Open a web browser and go to the following URL:

```
http://localhost:8080
```

If everything is working correctly, you should see your custom landing page.

6. To stop the Nginx Docker container, run the following command:

```
docker stop mynginx
```

This command will stop the "mynginx" container.

## Bonus Tip: Using Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. With Docker Compose, you can define your application's services, networks, and volumes in a single YAML file, making it easy to start and stop your entire application.

Here is an example Docker Compose file for an Nginx container with a custom landing page:

```
version: "3"

services:
  web:
    build: .
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
```

This Docker Compose file defines a service named "web" that builds the Docker image from the current directory, maps port 8080 on your host machine to port 80 in the container, and mounts the "html" directory as a volume.

To use this Docker Compose file, create a new directory with the following files:

```
- docker-compose.yml
- Dockerfile
- html/index.html
```

The "Dockerfile" should be the same as in the "Building a Custom Docker Image" section, and the "html/index.html" should contain your custom landing page content.

Then run the following command to start the Nginx container with Docker Compose:

```
docker-compose up -d
```

This command will start the "web" service defined in the Docker Compose file, build the Docker image, and start the container in the background.

To stop the container, run the following command:

```
docker-compose down
```

This command will stop and remove the container.

Using Docker Compose can simplify your Docker workflow and make it easier to manage your containers.

## Conclusion

In this guide, we have learned how to use the Nginx Docker container and how to customize the landing page using different methods. We have also learned how to use Docker Compose to define and run multi-container Docker applications. Docker containers are a powerful tool that can help you develop, test, and deploy your applications more efficiently. Give it a try and see how it can help you in your development workflow!
