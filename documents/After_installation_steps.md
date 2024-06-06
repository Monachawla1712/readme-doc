
## After Installation Steps after Terraform execution : 

1. In Production Cluster
       - To create the secret for Mimir authentication, use the following command:

     **"kubectl create secret generic kubepromsecret --from-literal=username=admin --from-literal=password='mimir@123' -n monitoring"**


2. In Development Cluster 
       - Apply the probe.yaml to check the application health status. 

    **" kubectl apply -f probe.yaml "**

file location : probe.yaml inside files subfolder in documents folder.


3. Add Data sources for production environment.

    - Go to Data sources in grafana.
    - Go to add new data sources
    - Select prometheus data source
        
        1. Give the name to identify prod prometheus

        2. Give the mimir url inside connection url - https://mimir-grafana.arx-dev.com/prometheus

        3. Give user and password in authentication.
        user - admin
        password - mimir@123

        These user and password for mimir authentication is mentioned inside env/03-prod/files/mimir-values.yaml
    
    - Select Loki data source
        
        1. Give the name for identify the loki-prod

        2. Give the loki connection URL - https://loki-grafana.arx-dev.com

        3. Give user and Password for loki authentication.
        user- admin
        password - loki@123

        These user and password for loki authentication is mentioned inside env/03-prod/files/loki-values.yaml


4. Add Custom Dashboard for Application Logs in Grafana
 
    - Application Logs Dashboard (ACC):

        - Click on New Dashboard.
        - Go to Import Dashboard.
        - Add the JSON file in the Import via Dashboard JSON Model.
        - Refer the document to get the json File: 
            - documents/files/acc-application.json

    - Application Logs Dashboard (PROD):

        - Click on New Dashboard.
        - Go to Import Dashboard.
        - Add the JSON file in the Import via Dashboard JSON Model.
        - Refer the document to get the json File: 
            - documents/files/prod-application.json

    - Application Logs Dashboard (TST):

        - Click on New Dashboard.
        - Go to Import Dashboard.
        - Add the JSON file in the Import via Dashboard JSON Model.
        - Refer the document to get the json File: 
            - documents/files/tst-application.json


Note: You can find these JSON files and probe.yaml in the files subfolder within the documents folder.