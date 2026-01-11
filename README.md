# RSO Infrastructure

This repository contains runtime/deployment configuration for deploying the RSO project's microservices to a Kubernetes cluster.

## Responsibilities
* Deploying backend microservices
* Managing microservice configuration
* Exposing services using an ingress controller


## Deployed services
* ship-service - Ship management microservice
* component-service - Component management microservice
* auth-service - Authorization microservice
* postgres - database backend
* frontend - The frontend web app.


## Ingress routing
Ingress routing exposes the frontend at the root path, while API requests are routed to backend services.

| Service           | Routing path prefix |
|-------------------|---------------------|
| ship-service      | /api/ships          |
| component-service | /api/components     |
| auth-service      | /api/auth           |
| frontend          | /                   |


## Helm
Helm is used to manage microservice deployment. It injects environment specific values and manages upgrades.
Each microservice has its own Helm chart with configurable values, secrets and deployment template.

## CI/CD
This repository's deployment actions are triggered by application repositories via GitHub Actions. 
When an update is pushed to a microservice's repository its action builds a new docker image and pushes it to the container registry. The microservice's action then triggers its matching infrastructure deployment action in which Helm upgrade deploys the new image.  

## Configuration management
Sensitive information like passwords and secrets are provided using Kubernetes Secrets, GitHub Actions secrets or are Helm values injected at the time of deployment.

## Frontend
The frontend is deployed as a containerized workload in Kubernetes and managed via Helm, the same as backend microservices.