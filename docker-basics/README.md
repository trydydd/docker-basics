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

## Conclusion

Docker containers provide a convenient and efficient way to deploy and run applications. By using the Nginx Docker container, you can quickly set up a high-performance web server and reverse proxy. Give it a try and see how easy it is to use!