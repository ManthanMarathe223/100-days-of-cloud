# ECR – Docker Image Push

## What I did
- Created a private ECR repository `devops-ecr`
- Built a Docker image from an existing Dockerfile
- Tagged the image as `latest`
- Pushed the image to Amazon ECR

## What I learned
- ECR is used to store private Docker images
- Docker images must be authenticated before pushing to ECR
- Images are identified using repository URI and tags

## One-line takeaway
> ECR acts as a secure Docker image registry in AWS.

---

# ECR Image Push – Command Explanation

## Authenticate Docker to ECR
`aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <ECR-REPO-URI>`

- aws ecr get-login-password
  → Fetches a temporary authentication token for ECR.
- docker login
  → Logs Docker into the ECR registry securely.
- --password-stdin
  → Passes the password securely via standard input.

---

## Build Docker Image
  - Creates an image using docker files

`docker build -t devops-ecr:latest .`

- docker build
  → Builds a Docker image from a Dockerfile.
- -t devops-ecr:latest
  → Tags the image with name and version.
- .
  → Uses the Dockerfile in the current directory.

---

## Tag Image for ECR
  - Links local docker image to ECR 
`docker tag devops-ecr:latest <ECR-REPO-URI>:latest`

- docker tag
  → Creates an alias for the image so it matches the ECR repository name.
- <ECR-REPO-URI>:latest
  → Full path where the image will be pushed.

---

## Push Image to ECR
`docker push <ECR-REPO-URI>:latest`

- docker push
  → Uploads the Docker image to the ECR repository.
- :latest
  → Specifies the image tag to push.
