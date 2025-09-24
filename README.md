# Shared GitHub Actions Workflow for Fenghe AI Projects

This repository contains a reusable GitHub Actions workflow that simplifies Docker image building and pushing to Azure Container Registry (ACR) for multiple projects. By centralizing this workflow, you can manage and update the build process in one place without modifying each individual project.

## Usage

To use this shared workflow in your project, create a workflow file (e.g., `.github/workflows/acr-build.yml`) with the following content:

```yaml
name: Docker Image Build and Release

on:
  push:

jobs:
  docker:
    uses: FinAI-Project/actions/.github/workflows/acr-build.yml@main
    with:
      image_name: compass/aqs-agent
    secrets: inherit
```

This approach allows you to:

- Maintain a single source of truth for your Docker build process
- Easily update the workflow logic across all projects by modifying only this repository
- Reduce duplication in individual project configurations

## Parameters

| Parameter     | Required | Type   | Description |
| ------------- | -------- | ------ | ----------- |
| image_name    | Yes      | string | The name of the Docker image to build and push |
| build_context | No       | string | The path to the Docker build context directory (default: current directory) |
