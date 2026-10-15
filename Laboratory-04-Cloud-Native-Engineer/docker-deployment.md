# Docker Deployment and Container Lifecycle

## 1. Check Docker

### Command
```bash
docker --version
```
**Explanation:** Displays the installed Docker version.

```bash
docker info
```
**Explanation:** Displays information about the Docker environment and daemon.

## 2. Download the Nginx Image

```bash
docker pull nginx
```
**Explanation:** Downloads the official Nginx image from Docker Hub.

## 3. Run the Nginx Container

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```
**Explanation:** Starts an Nginx container in the background and maps host port 8080 to container port 80.

```bash
curl http://localhost:8080
```
**Explanation:** Sends an HTTP request to check whether the Nginx web server responds.

## 4. Manage the Container Lifecycle

```bash
docker ps
```
**Explanation:** Lists currently running containers.

```bash
docker stop my-nginx
```
**Explanation:** Stops the Nginx container.

```bash
docker ps -a
```
**Explanation:** Lists all containers, including stopped containers.

```bash
docker rm my-nginx
```
**Explanation:** Removes the stopped Nginx container.

## 5. Screenshots

- `screenshots/docker-version.png`
- `screenshots/nginx-running.png`
- `screenshots/container-lifecycle.png`

These screenshots will be added after I execute the commands in KillerCoda.
