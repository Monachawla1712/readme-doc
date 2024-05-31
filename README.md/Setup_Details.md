## Deployment

We have already parameterized all the values. Any values that need to be passed externally should be set in the corresponding section within the env folder.


First, create an access key and secret key, and generate a token from DigitalOcean.

**1. To store terraform state in Digital Ocean Space :**

#### Navigate to the tfstate directory inside 00-global directory:


  - cd env/00-global/tfstate

#### To apply the configuration:

 
       - export TF_VAR_digitalocean_token=

       - export TF_VAR_access_id=

       - export TF_VAR_secret_key=

       - terraform init 

       - terraform plan 

       - terraform apply 
 
 - Save the output values.

 #### To destroy the resources:

      - terraform destroy 


**2. To deploy network-setup - vpc, gateway_droplete :**

  *This module creates a vpc, gateway_droplete.* 

#### Navigate to the 01-network-setup directory inside env directory:

 - cd env/01-network-setup/

#### To apply the configuration:

       - export TF_VAR_digitalocean_token=

       - export TF_VAR_access_id=

       - export TF_VAR_secret_key=

       - terraform init -backend-config="access_key=" - backend-config="secret_key="

       - terraform plan

       - terraform apply

- Save the output values.

 #### To destroy the resources:

       - terraform destroy 

**3. To deploy dev (non-prod) - doks, doks-bootstrap ( cert-manager, do-registry-set, static-route-operator, nginx-ingress-controller and monitoring) :**

  *This module creates a doks cluster, doks-bootstrap (nginx-ingress-controller, cert-manager, do-registry-set, static-route-operator and monitoring)* 

#### Navigate to the 02-dev directory inside env directory:

 - cd env/02-dev/

#### To apply the configuration:

       - export TF_VAR_digitalocean_token=

       - export TF_VAR_access_id=

       - export TF_VAR_secret_key=

       - terraform init -backend-config="access_key=" -backend-config="secret_key="  

       - terraform plan

       - terraform apply

- Save the output values.

 #### To destroy the resources:

       - terraform destroy 


**4. To deploy prod env - doks, doks-bootstrap ( cert-manager, do-registry-set, static-route-operator, nginx-ingress-controller and monitoring) :**

  *This module creates a doks cluster, doks-bootstrap (nginx-ingress-controller, cert-manager, do-registry-set, static-route-operator and monitoring)* 

#### Navigate to the 03-prod directory inside env directory:

 - cd env/03-prod/

#### To apply the configuration:

       - export TF_VAR_digitalocean_token=

       - export TF_VAR_access_id=

       - export TF_VAR_secret_key=

       - terraform init -backend-config="access_key=" -backend-config="secret_key="   

       - terraform plan

       - terraform apply

- Save the output values.

 #### To destroy the resources:

       - terraform destroy 


