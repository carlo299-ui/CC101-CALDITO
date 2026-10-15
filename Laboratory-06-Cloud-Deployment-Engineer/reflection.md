# Reflection

This laboratory activity helped me understand how Docker Compose simplifies the deployment of multi-container applications. Instead of starting and configuring each container separately, I can define the services in a `docker-compose.yml` file and use one command to start the application stack. This makes the deployment process more organized, consistent, and easier to repeat.

YAML indentation is important because it defines the structure and relationships between configuration elements. If I use incorrect indentation or a Tab instead of spaces, the file may produce a parsing error or an incorrect configuration. This taught me to check the formatting carefully before deploying my application.

Environment variables, such as `MYSQL_PASSWORD`, allow configuration values to be passed to containers. They help the application and database use matching settings without placing those values directly into application code. However, sensitive credentials should be protected and should not be exposed in public repositories.

Deploying Nextcloud with MariaDB helped me see how different services work together to provide a complete application. Nextcloud handles the web interface, while MariaDB stores the application's database information. Docker Compose connects these services so they can communicate with each other.

Since Mission 1, my understanding of cloud computing has grown from learning basic concepts to exploring practical deployment tasks. I am becoming more familiar with containers, networking, configuration files, and infrastructure management. I have also learned that planning and documenting infrastructure are important skills for cloud engineers.

Overall, this mission helped me appreciate Infrastructure as Code because it allows infrastructure to be described in a reusable configuration file. With more practice, I hope to become more confident in deploying, troubleshooting, and managing cloud applications independently.
