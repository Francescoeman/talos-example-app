# talos-example-app
Hosts source code for an example app. Also has a workflow that builds and pushes the image.

This repository contains a GitHub Actions workflow that builds and pushes a Docker image to Amazon Elastic Container Registry (ECR). The workflow is triggered manually from the repository's Actions page and uses the sonnen/talos-workflows/.github/workflows/ecr-image.yaml@v0.8.0 action to perform the build and push operation.

## docker-ecr-image workflow

This workflow is triggered by a workflow dispatch event, meaning it can be manually initiated from the GitHub repository's Actions page.

 **Jobs:**

* `build`:The workflow consists of a single job named "build". This job is responsible for building and pushing a Docker image to Amazon Elastic Container Registry (ECR).

 **Job Configuration:**

* `uses`:  Specifies the external action to be used for the job. In this case, it uses the action sonnen/talos-workflows/.github/workflows/ecr-image.yaml@v0.8.0

* `aws_role_arn`: Provides the ARN of the IAM role that grants the workflow access to ECR, please change it accordingly.

* `ecr_repository`: Defines the name of the ECR repository where the Docker image will be pushed, please change it accordigly.

  **Overall Workflow Flow:**

1. The workflow is triggered manually from the GitHub repository's Actions page.

2. The "build" job is executed.

3. The external action sonnen/talos-workflows/.github/workflows/ecr-image.yaml@v0.8.0 is invoked.

4. The action uses the provided inputs, including the AWS region, IAM role ARN, ECR repository name, Dockerfile name, and secrets, to build and push the Docker image to ECR.

5. The workflow completes successfully if the image is successfully pushed to ECR.