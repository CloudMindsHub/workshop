+++
title = "Integrating Docker Swarm with AWS Services"
date = 2024
weight = 1
chapter = false
+++

# Integrating Docker Swarm with AWS Services

#### Overview
In this workshop, I will present the process of deploying and working with **Docker**, a powerful tool for managing and operating containers. To effectively orchestrate and manage containers, I used **Docker Swarm** – a built-in solution provided by Docker. Additionally, I leveraged several services on **AWS** to optimize the deployment and management of the system on the cloud platform, which helps enhance the flexibility and scalability of the application.

#### Architecture

![Architecture](/images/1-Introduce/Architecture-img.png?width=50pc)

#### Implementation process:
Clone GitHub Repository → EC2 Instance → Connect RDS → Dockerfile → Push image → ECR → Pull image → Docker Compose → Deploy Service → Docker Swarm Cluster.

#### Main content

1. [Introduce](1-introduce/)
2. [Preparation](2-preparation/)
3. [RDS (Database)](3-rds/)
4. [Elastic Container Registry (ECR)](4-ecr/)
5. [Docker Swarm](5-dockerswarm/)
6. [Docker Compose](6-dockercompose/)
7. [Troubleshooting](7-troubleshooting/)
8. [Clear Resources](8-clearresources/)
<!-- need to remove parenthesis for path in Hugo 0.88.1 for Windows-->
