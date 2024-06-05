## Deploying Maas Dev DOKS 

This document provides a comprehensive guide for deploying a DOKS (DigitalOcean Kubernetes) Cluster, including provisioning the network (VPC), gateway droplet, nodes, and essential addons such as bootstrap (including monitoring with Prometheus, Loki, Grafana, and Mimir), cert-manager, do-registry, static route operator, and ingress Nginx controller.

All these components are created seamlessly through Terraform Cloud by pushing code to a GitHub repository, where Terraform Cloud workspaces will automatically trigger the deployment process.


#### Quickstart
The following steps describe how to deploy a Kubernetes cluster using Terraform Cloud.

### Requirements and Prerequisites

1. Terraform Cloud Account:

    - Sign up at https://app.terraform.io/

2. DigitalOcean Cloud Account:
    - Sign up at (https://cloud.digitalocean.com/)


**Note: All values have already been parameterized. Any values that need to be passed externally should be set in the corresponding section within the env folder.**

##  Below Deployment is Orchestrated for Terraform Cloud Execution 
Refer Terraform cloud : [Terraform cloud Execution Steps](/documents/README.md/Terraform-execution.md)

 ### Deploying the 01-network_setup

This setup will create a VPC and a gateway droplet, utilizing the VPC module in the modules section.

1. **Configure Network Deployment:**

    - Fill in the necessary information in the main.tf file inside the 01-network_setup folder.

2. **Deploy the Network:**

    - Push the changes to the GitHub repository. Terraform Cloud workspaces will automatically trigger the changes from the GitHub repo and deploy the network in DigitalOcean.

3. **Workspace Setup:**

    - For details on setting up workspaces in Terraform Cloud, refer to the  [Terraform cloud Execution Steps](/documents/README.md/Terraform-execution.md)



 ### Deploying the Dev environment:
This module creates a DOKS cluster and deploys the necessary components such as the nginx-ingress-controller, cert-manager, do-registry-set, static-route-operator, and monitoring and utilizing the doks and doks-bootstrap module in the modules section. 
 

### **Configure Dev Environment Deployment:**
1. **Configuration:**
    - Fill necessary information in the main.tf file , 01-doks.tf and 02-doks-bootstrap.tf files inside the 02-dev folder.

2. **Deploy the Dev Environment:**

    - Push the changes to the GitHub repository. Terraform Cloud workspaces will automatically trigger the changes from the GitHub repo and deploy the dev cluster in DigitalOcean with configured monitoring.

3. **Workspace Setup:**

    - For details on setting up workspaces in Terraform Cloud, refer to the  [Terraform cloud Execution Steps](/documents/README.md/Terraform-execution.md)


### Deploying the Prod environment:
This module creates a DOKS cluster and deploys the necessary components such as the nginx-ingress-controller, cert-manager, do-registry-set, static-route-operator, and monitoring and utilizing the doks and doks-bootstrap module in the modules section.
 

### **Configure Prod Environment Deployment:**
1. **Configuration:**
    - Fill necessary information in the main.tf file , 01-doks.tf and 02-doks-bootstrap.tf files inside the 03-prod folder.

2. **Deploy the Dev Environment:**

    - Push the changes to the GitHub repository. Terraform Cloud workspaces will automatically trigger the changes from the GitHub repo and deploy the prod cluster in DigitalOcean with configured monitoring.

3. **Workspace Setup:**

    - For details on setting up workspaces in Terraform Cloud, refer to the  [Terraform cloud Execution Steps](/documents/README.md/Terraform-execution.md)


### Monitoring with DOKS-Bootstrap Module

The doks-bootstrap module is also utilized for monitoring, deploying various tools and services:

    - Loki for logs
    - Prometheus for metrics
    - Mimir for storing metrics
    - Blackbox Exporter to check application health status
    - Grafana for visualizing metrics and logs using dashboards

The related code can be found in the doks-bootstrap folder under addons/monitoring.


### For configuring static route operator

Additionally, this module deploys a **static route operator** to route outbound traffic through a static reserved IP. 

You can find its configuration in the doks-bootstrap folder under addons/static-route-operator.

 The destination IP is specified in the doks-bootstrap.tf file within the env folder for both 02-dev and 03-prod.


### Documents

- [Architecture Diagrams](/documents/README.md/Architecture.md)
- [Setup_Details](/documents/README.md/Setup_Details.md)  
- [Terraform cloud Execution Steps](/documents/README.md/Terraform-execution.md)
- [Directory Structure](/documents/README.md/Directory_structure.md)








