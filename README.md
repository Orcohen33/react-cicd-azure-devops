# React CICD in Azure DevOps

This repository contains a CI/CD pipeline configuration for a React application using Azure DevOps. The pipeline builds the React application, creates a Docker image, pushes the image to Azure Container Registry (ACR), and deploys the containerized application to an Azure App Service.

## Pipeline Overview

The Azure DevOps pipeline is defined in the `azure-pipelines.yml` file, which consists of the following stages:

1. **Build Stage**:
  - Deploys the Azure Container Registry resource using an ARM template (`acr-temp-new.json`).
  - Builds a Docker image for the React application using the `Dockerfile`.
  - Pushes the Docker image to the Azure Container Registry.

2. **Deploy Stage**:
  - Deploys the Azure App Service resource using an ARM template (`app-svc-temp.json`).
  - Deploys the Docker image from the Azure Container Registry to the Azure App Service.

## Prerequisites

Before running the pipeline, ensure that you have the following:

- An Azure subscription
- An Azure Container Registry resource
- An Azure App Service resource (or the pipeline will create one)
- A Docker image for the React application

## Configuration

The pipeline is configured with the following variables:

- `buildConfiguration`: Build configuration (e.g., "Release").
- `location`: Azure region for resource deployment (e.g., "westeurope").
- `acrHostName`: Hostname of the Azure Container Registry.
- `acrName`: Name of the Azure Container Registry.
- `rgName`: Name of the Azure Resource Group.
- `containerName`: Name of the Docker container.
- `appName`: Name of the Azure App Service.
- `vmImageName`: Name of the Azure VM image for the build agent (e.g., "ubuntu-latest").
- `dockerfilePath`: Path to the Dockerfile.
- `tag`: Docker image tag (set to the Build ID).
- `appSvcPlanName`: Name of the Azure App Service Plan.

Make sure to update these variables according to your environment and requirements.

## Usage

1. Configure the Azure DevOps pipeline by adding the `azure-pipelines.yml` file to your repository.
2. Update the pipeline variables and Azure Resource Manager (ARM) templates (`acr-temp-new.json` and `app-svc-temp.json`) as needed.
3. Commit and push your changes to the repository's `main` branch to trigger the pipeline.
4. Monitor the pipeline execution in the Azure DevOps portal.

Upon successful completion, the React application will be deployed to the Azure App Service as a Docker container.

## Contributing

Contributions to this project are welcome. If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.
