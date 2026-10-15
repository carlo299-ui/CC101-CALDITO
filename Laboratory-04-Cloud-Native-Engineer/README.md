# Laboratory 04: The Cloud-Native Engineer

## Mission Overview
This activity explores the differences between Virtual Machines (VMs) and containers. It also demonstrates how Docker can be used to deploy and manage an Nginx web server.

## Objectives
- Compare Virtual Machines and containers.
- Check the Docker installation and status.
- Download and run an Nginx container.
- Test the web server using an HTTP request.
- Stop and remove a container.
- Document the commands using Markdown.

## Docker Commands Executed
```bash
docker --version
docker info
docker pull nginx
docker run -d --name my-nginx -p 8080:80 nginx
curl http://localhost:8080
docker ps
docker stop my-nginx
docker ps -a
docker rm my-nginx
```

## Skills Learned
- Basic Docker commands.
- Downloading and running container images.
- Port mapping and web server testing.
- Managing the container lifecycle.
- Creating Markdown documentation.

## Challenges Encountered
I will document the actual challenges I encounter while completing the activity and explain how I solve them.

## Screenshots
The screenshots showing the Docker version, running Nginx server, and container lifecycle will be added to the screenshots folder.
