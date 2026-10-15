# Research: Multi-Tier Architecture

## What Is a Two-Tier Architecture?

A two-tier architecture is an application design that separates an application into two main parts: the web/application tier and the database tier. Each tier has a different responsibility, and they communicate to provide the complete application service.

## 1. The Web/Application Tier

The web/application tier handles user requests and provides the application's interface. In this laboratory, Nextcloud runs in a Docker container and serves the web interface that users access through their browsers. It also communicates with the database to manage application information.

## 2. The Database Tier

The database tier stores persistent application data, including user account information and file metadata. In this laboratory, MariaDB runs in a separate Docker container and provides database services to Nextcloud.

## 3. Why Separate the Tiers?

Separating the web application and database into different containers makes the system easier to manage and troubleshoot. Each service can be updated or configured independently, and separating their responsibilities improves organization and supports future scaling.

## Conclusion

Docker Compose helps connect the Nextcloud and MariaDB containers so they can work together as one application. This approach makes deployment more organized and repeatable.
