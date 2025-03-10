+++
title = "Introduce"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++



#### Scene

The company has a web application consisting of two containers:

- **Web container**: Runs the main web application.
- **Database container**: Contains the MySQL database.

The company decided to use Docker Swarm to deploy these containers on three small EC2 instances on AWS. Swarm helps them:

- **Automatically load balance** between the servers to avoid overloading a specific node.
- **Automatically restart** the containers in case of failure.
  
Docker Swarm is an ideal solution for small companies or projects that do not require complex orchestration, where Kubernetes or ECS may become excessive and difficult to manage. Docker Swarm provides sufficient features to automate and manage containers effectively, while also being easy to use and well-integrated with Docker.

#### What is Docker?

**Docker** is an open-source platform that allows you to automate the deployment, management, and running of applications within containers. Docker simplifies the development and deployment process by ensuring that your application runs consistently in any environment.

#### Docker Compose?

**Docker Compose** is a tool that helps define and run multi-container Docker applications. Instead of having to run individual Docker commands for each container, Docker Compose allows you to manage all the related containers in an application using a single configuration file.

#### Why use Docker Swarm?

**Docker Swarm**  is a container orchestration tool integrated into Docker. It allows you to deploy and manage containers on one or more servers (nodes) as a cluster. Docker Swarm makes it easy to control how containers are deployed, balance loads, and manage resources within the cluster.

It is a suitable choice for medium and small projects where simplicity and ease of deployment are top priorities.

Although Docker Swarm is not integrated with AWS management services like ECS or EKS, you can still set up and manage a Docker Swarm cluster on a few AWS resources such as EC2 instances.

This particularly helps those who are already familiar with Docker to manage containers more easily than with ECS, even when using it on AWS.

![Architecture](/images/1-Introduce/Introduce-img.jpeg?width=50pc)