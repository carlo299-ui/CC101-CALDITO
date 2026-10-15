# Docker Compose Guide

## 1. What Does the `services:` Block Do?

The `services:` block in a Docker Compose YAML file defines the containers that make up an application. In this project, it defines two services: `database`, which uses MariaDB, and `app`, which uses Nextcloud. Docker Compose uses these definitions to configure and run the application components together.

## 2. How Does Nextcloud Find the Database?

The Nextcloud application uses the environment variable `MYSQL_HOST=database` to locate the database service. The name `database` matches the service name defined in the Compose file. Docker Compose provides network connectivity and service-name resolution so the Nextcloud container can communicate with MariaDB.

## 3. Docker Run vs. Docker Compose

The `docker run` command is commonly used to create and start an individual container with options specified directly in the command. In contrast, `docker-compose up -d` reads the `docker-compose.yml` file and starts the services defined in it in the background. This makes it easier to deploy a multi-container application consistently using one configuration file.

## 4. Infrastructure as Code (IaC)

Infrastructure as Code means defining infrastructure configuration in files instead of relying only on manual setup. Docker Compose applies this idea by describing the application's services, images, ports, and environment variables in a YAML file. The configuration can be saved, reviewed, shared, and reused.

## Conclusion

Docker Compose helps organize the deployment of Nextcloud and MariaDB as a connected application. Keeping the configuration in a file makes the deployment easier to understand, repeat, and maintain.
