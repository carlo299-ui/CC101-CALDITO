# OPERATIONAL MANUAL
## MariaDB and Nextcloud Cloud Deployment Using Docker on Ubuntu Server

### 1. Project Overview

This project implements a cloud storage system using Nextcloud and MariaDB deployed on an Ubuntu Server virtual machine. Docker is used to run both applications in separate containers.

Nextcloud provides a web-based platform where users can upload, download, store, and manage files. MariaDB serves as the database management system that stores Nextcloud's application information and user-related records.

The purpose of this project is to demonstrate containerization, database integration, persistent storage, and backup automation in a cloud computing environment.

### 2. System Requirements

The following software and tools are required:

- Ubuntu Server
- Oracle VirtualBox
- Docker
- Docker Compose
- Nextcloud
- MariaDB
- Web browser
- Internet connection
- Bash scripting
- Cron for scheduled backups

### 3. System Architecture

The system follows a simple multi-container architecture:

1. The user accesses Nextcloud through a web browser.
2. The Ubuntu Server virtual machine hosts the Docker environment.
3. Docker runs the Nextcloud and MariaDB containers.
4. Nextcloud communicates with MariaDB through an internal Docker network.
5. Persistent volumes store application files and database information.
6. A backup script is used to create backups of important data.

### 4. Installation and Configuration

**Step 1: Update Ubuntu Server**

Open the Ubuntu terminal and execute:

```bash
sudo apt update
sudo apt upgrade -y
```

**Step 2: Install Docker and Docker Compose**

Install the required packages:

```bash
sudo apt install docker.io docker-compose-v2 -y
```

Start and enable Docker:

```bash
sudo systemctl enable --now docker
```

Verify the installation:

```bash
sudo docker --version
sudo docker compose version
```

**Step 3: Prepare the Project Directory**

Create a project directory:

```bash
mkdir -p ~/ccm101-enterprise-architect
cd ~/ccm101-enterprise-architect
```

Make sure the Docker Compose configuration file is inside this directory.

**Step 4: Configure the Containers**

The `docker-compose.yml` file defines the Nextcloud and MariaDB services, their environment variables, network connection, ports, and persistent volumes.

Make sure that:

- Nextcloud is configured to connect to MariaDB.
- Both containers use compatible database credentials.
- MariaDB has persistent database storage.
- Nextcloud has persistent file and application storage.
- Both services are connected through the appropriate Docker network.

**Step 5: Start the Application**

Run the following command inside the project directory:

```bash
sudo docker compose up -d
```

Check the running containers:

```bash
sudo docker ps
```

Check the service status:

```bash
sudo docker compose ps
```

**Step 6: Access Nextcloud**

Get the Ubuntu Server IP address:

```bash
hostname -I
```

Open a web browser and enter:

```text
http://YOUR-UBUNTU-IP:PORT
```

Replace `YOUR-UBUNTU-IP` with your Ubuntu Server IP address and `PORT` with the configured Nextcloud host port.

Complete the initial Nextcloud setup by creating an administrator account and connecting it to the configured MariaDB database.

### 5. System Operations and Maintenance

**Start the system:**

```bash
sudo docker compose up -d
```

**Stop the system:**

```bash
sudo docker compose stop
```

**Restart the system:**

```bash
sudo docker compose restart
```

**View running containers:**

```bash
sudo docker ps
```

**View application logs:**

```bash
sudo docker compose logs
```

**View Nextcloud logs:**

```bash
sudo docker compose logs nextcloud
```

**View MariaDB logs:**

```bash
sudo docker compose logs mariadb
```

Note: The commands above assume the service names in your Compose file are `nextcloud` and `mariadb`. Replace them if your actual service names are different.

### 6. Data Persistence and Backup

Persistent Docker volumes help ensure that important files and database information remain available even when containers are stopped or recreated.

The project also uses a Bash automation script to create database backups.

To execute the backup script:

```bash
chmod +x automation-script.sh
./automation-script.sh
```

If the script requires administrator privileges:

```bash
sudo ./automation-script.sh
```

Check the backup directory to verify that backup files have been created.

**Scheduled Backup Using Cron**

To schedule an automatic backup every day at 2:00 AM:

```bash
crontab -e
```

Add the following line, replacing the directory with your actual project path:

```bash
0 2 * * * cd /home/USERNAME/ccm101-enterprise-architect && /bin/bash automation-script.sh
```

Replace `USERNAME` with your Ubuntu username.

Save and exit the editor. The backup script should now run automatically every day at 2:00 AM.

### 7. Security Configuration

The following security practices should be observed:

- Use strong passwords for Nextcloud and MariaDB.
- Avoid exposing the MariaDB port publicly.
- Allow only necessary incoming network connections.
- Configure the Ubuntu firewall using UFW.
- Keep Ubuntu, Docker, and application images updated.
- Protect backup files from unauthorized access.
- Do not publish database passwords or private credentials on GitHub.

Example firewall commands:

```bash
sudo ufw allow 22/tcp
sudo ufw allow YOUR-NEXTCLOUD-PORT/tcp
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
```

Replace `YOUR-NEXTCLOUD-PORT` with the actual host port configured for Nextcloud. Only allow SSH if remote SSH access is needed.

### 8. Troubleshooting

| Problem | Possible Solution |
|---|---|
| Docker is not running | Execute `sudo systemctl start docker`. |
| Nextcloud cannot connect to MariaDB | Check database credentials, service names, and Docker network configuration. |
| Website cannot be accessed | Check the Ubuntu IP address, configured port, and firewall rules. |
| Container is not running | Use `sudo docker compose ps` and check application logs. |
| Backup script fails | Check the database service name, backup directory, and script permissions. |
| Data disappears | Verify that persistent Docker volumes are correctly configured. |

### 9. Backup and Recovery

Database backups should be created regularly to protect important information.

To restore a database backup, first make sure the MariaDB service is running. Then use the appropriate MariaDB restore command based on the actual database service name, database name, and backup filename.

Example:

```bash
sudo docker compose exec -T mariadb \
  mariadb -u root -p DATABASE_NAME < backup.sql
```

Replace `mariadb`, `DATABASE_NAME`, and `backup.sql` with the correct values.

Before restoring, create another backup of the current database because restoration may overwrite existing information.

Nextcloud files and database records should both be backed up to ensure a consistent recovery.

### 10. Conclusion

The MariaDB and Nextcloud deployment demonstrates how cloud computing technologies can be used to create a functional cloud storage environment. Through Ubuntu Server and Docker, the project separates application services into containers while allowing them to communicate through an internal network.

Persistent storage protects important data, while Bash scripting and Cron help automate backup operations. Overall, this project demonstrates container management, database integration, cloud storage, basic security configuration, and system maintenance.
