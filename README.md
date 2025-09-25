# ELEVATELAB_Day3ofDay45

Terraform with Docker - Local Container Provisioning
Objective

The goal of this task is to provision a local Docker container using Terraform.
Tools Used

Terraform

Docker

Steps
1. Setup Terraform

Install Terraform on your machine.

Make sure Docker is installed and running locally.

2. Write Terraform Code (main.tf)

Use the Docker provider.

Define the Docker image you want (e.g., nginx:latest).

Create a container resource.

#main.tf

    terraform {
        required_providers {
          docker = {
            source  = "kreuzwerker/docker"
            version = "~> 3.0.2"
          }
        }
      }
      
    provider "docker" {}
    
    resource "docker_image" "nginx" {
      name         = "nginx:latest"
      keep_locally = false
    }
    
    resource "docker_container" "nginx" {
      name  = "my-nginx-container"
      image = docker_image.nginx.image_id
    
      ports {
        internal = 80
        external = 900
      }
    }

3. Initialize Terraform

Run:

terraform init


This downloads the required provider plugins.

4. Plan Infrastructure

Check what Terraform will do without applying changes:

terraform plan

5. Apply Changes

Create the container:

terraform apply


6. Verify Infrastructure

Check the container is running using Docker:

docker ps


Check Terraform state:

terraform state list

7. Destroy Infrastructure

Clean up everything created by Terraform:

terraform destroy

Outcome

After completing this task,

I Understand how to provision resources using Terraform.

and Learned how Terraform interacts with Docker.

