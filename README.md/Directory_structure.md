
- This repository contains the complete directory structure for our Terraform infrastructure code.

       - **Top-Level Folders**: The repository is organized into two main folders: env and modules.

       - **env Folder**: This folder contains the entire Infrastructure as Code (IaaC) for deploying the VPC, DigitalOcean Kubernetes Service (DOKS), and Kubernetes addons. It includes the modules that reference resources from the modules folder.

       - **modules Folder**: This folder contains the code for creating various resources (DOKS, DOKS addons, Terraform state, and VPC) that are called within the env folder.

       
       -  **env Folder Structure**:

              1. 01-network: This folder contains the code for creating the VPC network and the gateway droplet.

              2. 02-dev: This folder is dedicated to creating the development environment.

              3. 03-prod: This folder is dedicated to creating the production environment.

       
       - **modules Folder Structure** :

              1. doks - Contains all necessary resources for creating the DOKS cluster, node pools, as well as respective variables, versions, and outputs.
              
              2. doks-bootstrap - Contains all necessary resources for creating addons like cert-manager, ingress-nginx controller, DigitalOcean registry integration, static-route-operator, and monitoring (Prometheus, Grafana, Loki, and Mimir).

              3. vpc - Contains resources for creating the VPC network and gateway droplet.
       
##  Directory Structure
### Major Folders 

```

├── env             
└── modules

```

## Sub-folders inside Each Major Folders 

```
env
├── 01-network_setup
├── 02-dev
├── 03-prod

modules
├── doks
├── doks-bootstrap
│   └── addons
│       ├── cert-manager
│       ├── do-registry-set
│       ├── monitoring
│       ├── nginx-ingress-controller
│       └── static-route-operator
└── vpc

```

### High Level Directory Structure of Entire Tf infrastructure code. 

```

env                   
├── network
│   ├── backend.tf
│   ├── main.tf
│   ├── outputs.tf
│   ├── variables.tf
│   └── versions.tf
├── dev
│   ├── doks
│   ├── doksbootstrap
│   ├── backend.tf
│   ├── main.tf
│   ├── outputs.tf
│   ├── variables.tf
│   └── versions.tf
├── prod
│   ├── doks
│   ├── doksbootstrap
│   ├── backend.tf
│   ├── main.tf
│   ├── outputs.tf
│   ├── variables.tf
│   └── versions.tf

modules
├── doks
│   ├── main.tf
│   ├── outputs.tf
│   ├── providers.tf
│   ├── variables.tf
│   └── versions.tf
├── doksbootstrap
│   ├── main.tf
│   ├── outputs.tf
│   ├── variables.tf
│   └── versions.tf
│   └── addons
│       ├── cert-manager
│       │   ├── cluster-issuer.yaml
│       │   ├── main.tf
│       │   ├── variables.tf
│       │   ├── versions.tf
│       │   └── values.tf
│       ├── do-registry-set
│       │   ├── main.tf
│       │   ├── variables.tf
│       │   └── versions.tf
│       ├── monitoring
│       │   ├── main.tf
│       │   ├── variables.tf
│       │   ├── outputs.tf
│       │   ├── files
│       │   │   └── (multiple .json files)
│       │   └── helm
│       │       ├── blackbox
│       │       ├── loki
│       │       ├── prometheus
│       │       └── mimir
│       ├── nginx-ingress-controller
│       │   ├── main.tf
│       │   ├── variables.tf
│       │   ├── outputs.tf
│       │   └── values.yaml
│       └── static-route-operator
│           ├── egress.yaml
│           ├── main.tf
│           ├── variables.tf
│           └── versions.tf
└── vpc
    ├── gateway.tf
    ├── main.tf
    ├── outputs.tf
    ├── providers.tf
    ├── variables.tf
    ├── versions.tf
    └── scripts
        └── gateway.droplet.sh
```
