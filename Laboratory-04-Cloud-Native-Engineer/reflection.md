# Checkpoint 7 – Mission Reflection

Working with Docker has helped me understand how containerization makes application development and deployment easier and more efficient.

First, the boot time and setup process of a Docker container are much faster than installing an operating system on a Virtual Machine (VM). A VM requires a complete operating system and more system resources, while a Docker container shares the host operating system's kernel. Because of this, containers can start in seconds and are generally lightweight.

Second, port mapping using `-p 8080:80` is necessary when running a web server inside a container. It connects port 8080 on the host machine to port 80 inside the container. This allows users to access the web server through their browser using `localhost:8080`. Without port mapping, the service may not be accessible directly from the host.

Third, when using the `docker rm` command, the container is removed, and any data stored only in its writable layer is lost. However, data stored in Docker volumes or bind mounts remains available even after the container is deleted. This shows why persistent storage is important for protecting important files and application data.

Fourth, I think containerization improves collaboration between software developers and IT operations teams, also known as DevOps. Developers can package applications with their dependencies, making them easier to test and deploy consistently across different environments. This reduces compatibility problems and helps teams work together more efficiently.

Finally, my GitHub portfolio is evolving as I continue learning new technologies and completing practical projects. Each checkpoint helps me improve my technical skills, problem-solving abilities, and documentation. By uploading my work to GitHub, I can track my progress and demonstrate what I have learned. I also understand the importance of writing clear documentation and organizing my repositories properly. Overall, this mission has strengthened my understanding of Docker and encouraged me to continue developing my skills in containerization and software deployment.
