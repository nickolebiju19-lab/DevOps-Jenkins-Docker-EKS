# CI/CD Deployment of a Java Web Application on Amazon EKS

A hands-on DevOps project demonstrating how to build, containerize, and deploy a Java web application using Jenkins, Maven, Docker, Docker Hub, Kubernetes, and Amazon EKS.

## Project Overview

This project automates the delivery workflow of a Java web application, from source-code checkout to deployment on a Kubernetes cluster hosted on AWS.

The pipeline builds the application using Maven, packages it into a Docker image, publishes the image to Docker Hub, and deploys it to Amazon EKS using Kubernetes resources.

## Architecture

**GitHub → Jenkins → Maven → Docker → Docker Hub → Amazon EKS → Kubernetes Service → Browser**

## Technologies Used

- **Version Control:** Git, GitHub
- **CI/CD:** Jenkins
- **Build Tool:** Apache Maven
- **Containerization:** Docker
- **Container Registry:** Docker Hub
- **Cloud Platform:** Amazon Web Services (AWS)
- **Container Orchestration:** Kubernetes, Amazon EKS
- **Application Server:** Apache Tomcat
- **Infrastructure:** Amazon EC2 worker nodes
- **Configuration:** YAML

## Workflow

1. **Source Code Checkout:** Jenkins retrieves the application source code from GitHub.
2. **Build:** Maven resolves dependencies, compiles the Java application, and packages it into a WAR artifact.
3. **Docker Image Creation:** Docker packages the application with the required runtime configuration.
4. **Image Publishing:** The container image is pushed to Docker Hub.
5. **Kubernetes Deployment:** Amazon EKS runs the container using Kubernetes Deployment resources.
6. **Application Exposure:** A Kubernetes LoadBalancer Service exposes the application for browser access.
7. **Verification:** The deployment is validated by checking Kubernetes node and Pod status and accessing the application through the load balancer.

## Kubernetes Resources

- **Deployment:** `mavenwebappdeployment`
- **Service:** `mavenwebappsvc`
- **Container Image:** `nickoledocker/maven-web-app`

The Deployment manages the application Pod, while the LoadBalancer Service provides an external access endpoint.

## Challenges and Troubleshooting

During implementation, I worked through several practical infrastructure and deployment issues:

- Resolved Kubernetes Pod scheduling constraints by changing the worker-node instance size.
- Troubleshot an AWS On-Demand vCPU quota error during worker-node provisioning.
- Corrected Docker Hub authentication using a Personal Access Token.
- Fixed Kubernetes manifest formatting and container image configuration.
- Verified worker-node readiness, Pod health, load balancer provisioning, and application accessibility.

These troubleshooting steps helped strengthen my understanding of container orchestration, AWS resource limits, registry authentication, and deployment verification.

## Key Learnings

- Designing a CI/CD workflow for a Java application.
- Integrating Jenkins, Maven, Docker, and Docker Hub.
- Deploying containerized applications to Amazon EKS.
- Working with Kubernetes Deployments, Pods, and Services.
- Troubleshooting cloud infrastructure and container deployment issues.
- Verifying application availability through an AWS load balancer.

## Repository Contents

This repository contains the project files and configuration used for the implementation. Refer to the actual repository structure for the available Jenkins pipeline, Dockerfile, Kubernetes manifests, and application source code.

## Security Notes

- Do not commit AWS credentials, Jenkins secrets, Docker Hub tokens, or sensitive kubeconfig files.
- Use Jenkins credentials or an appropriate secrets-management mechanism for authentication.
- Review repository history before making the project public.

## Author

**Nickole Biju**  
Aspiring DevOps Engineer

GitHub: https://github.com/nickolebiju19-lab  
Docker Hub: https://hub.docker.com/r/nickoledocker/maven-web-app

