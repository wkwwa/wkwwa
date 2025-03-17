<div id="header" align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNG9taW9uNDFkbTAxMm8xaGZ3ZzIxN2N0YWppN3IxM3JhZWRqMHZnOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/d9mkbc1QkvBnHthaQp/giphy.gif" width="200"/>
</div>

- 👋 Hi, I’m @wkwwa
- 👀 I’m interested in DevOps
- 🌱 I’m currently learning Go

# Projects
First of all: 
* Starterkit. Software installation. https://github.com/wkwwa/wkwwa/blob/main/starterkit.md

## DevOps:

* DevOps project demonstrating a full application build-delivery cycle using CI/CD and toolset: Docker, Gitlab CI/CD, Terraform, k8s, Helm, ArgoCD and monitoring with Prometheus, Grafana. App: Vue.js, HTML - frontend, Go - backend.
  * CI https://github.com/wkwwa/store-ci
  * CD Staging https://github.com/wkwwa/store-cd
  * CD Production https://github.com/wkwwa/argocd-app

  <details><summary>Workflow Example:</summary>

    1. Developer works on a feature branch.
    1. Developer commits and pushes changes to GitLab.
    1. GitLab CI/CD pipeline runs: builds, tests, and pushes the Docker image.
    1. GitLab CI/CD deploys to staging using Helm.
    1. Automated tests run on staging.
    1. If tests pass, GitLab CI/CD updates the production deployment configuration in the Nexus repository (e.g., Helm chart values).
    1. Argo CD detects the change in Git and automatically deploys the updated application to production.
    1. Prometheus and Grafana monitor the application in production.

  Continuous Integration (CI):

    GitLab CI/CD https://github.com/wkwwa/store-ci/blob/main/.gitlab-ci.yml

    1. Build Stage: Triggered on pushes to feature branches. Builds the application Docker image, runs unit tests, and pushes the image to the GitLab Container Registry.
    1. Test Stage: Deploys to a temporary testing environment (Docker). Runs tests.
    1. Artifact Storage: Docker image and build artifacts stored in the GitLab Container Registry.

  Continuous Delivery (CD) - Staging:

  GitLab CI/CD https://github.com/wkwwa/store-cd/blob/main/.gitlab-ci.yml

    1. Terraform: Manages the staging environment infrastructure (Kubernetes cluster, load balancer).
    1. Helm: Defines the application deployment to staging (pulls Docker image from the GitLab Container Registry). Creates Helm package and pushes in the Nexus repository.
    1. Deployment: GitLab CI/CD deploys to staging using Helm.
  
  Continuous Delivery (CD) - Production (using Argo CD):
  
  GitLab CI/CD https://github.com/wkwwa/argocd-app/blob/main/.gitlab-ci.yml
  
    1. Nexus Repository for Deployment Configuration: A separate repository stores the Helm chart values for the production environment. This is the source of truth for Argo CD.
    1. Argo CD Setup: Argo CD is installed in the production Kubernetes cluster.
    1. Argo CD Application Definition: An Argo CD Application custom resource is created. This resource points to:

        * The Git repository containing the production deployment configuration.
        * The path within the repository to the application manifests.
        * The target Kubernetes cluster (production).
        * The desired revision (branch, tag, or commit) to track.

    1. Automated Synchronization: Argo CD automatically monitors the Git repository for changes. When a change is detected (e.g., a new version of the Helm chart values is pushed), Argo CD synchronizes the production environment to the desired state defined in Git.
    1. Deployment Trigger: The GitLab CI/CD pipeline, after successful staging tests, commits the updated Helm chart values (or other configuration) to the Git repository that Argo CD is monitoring. This triggers the Argo CD synchronization and deploys the new version to production.

  Monitoring and Logging:

  GitLab CI/CD https://github.com/wkwwa/store-cd/blob/main/monitoring-tools/.gitlab-ci.yml

    1. Prometheus: Deployed in the Kubernetes cluster to collect metrics.
    1. Grafana: Visualizes metrics from Prometheus.

  Infrastructure as Code (IaC):

    1. Terraform: Manages staging and production infrastructure. https://github.com/wkwwa/store-cd/blob/main/terraform/.gitlab-ci.yml
  </details>

* Automated virtual machine deployment with Vagrant. Installing Nexus on a VM using Vagrant and VMWare (MacOS Apple Silicon chip) https://github.com/wkwwa/vm-vagrant
* Infrastructure deploy using the Infrastructure as Code approach and creating a virtual machine and S3 bucket using Terraform in Yandex Cloud https://github.com/wkwwa/terraform-yc-instance
* Terraform config deploys a virtual machine and a VPC infrastructure. Demo shows creating a Terraform configuration using variables and modules for reuse or extension configuration https://github.com/wkwwa/tf-var-modules-yc-instance
* Automated RKE Installation. The roject provides scripts and configuration files to automate the installation of a Kubernetes cluster on Yandex Cloud using Rancher Kubernetes Engine https://github.com/wkwwa/k8s_install_yandex_cloud_rke

## Golang:
