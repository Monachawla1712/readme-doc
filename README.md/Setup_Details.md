
### Pre-requisites Before Creating Infrastructure Setup in DigitalOcean
 

1. Create a Digital Ocean Token .
       - Set this variables in terraform cloud at the Organization level

2. Create a Reserved IP. 
3. Create an SSH key and Pass the ID into the code.
       - Perform this step inside the 01-network_setup directory.


We have already parameterized all the values. Any values that need to be passed externally should be set in the corresponding section within the env folder.


### After Installation Steps : 

1. In Production Cluster
       - To create the secret for Mimir authentication, use the following command:

  **"kubectl create secret generic kubepromsecret --from-literal=username=admin --from-literal=password='mimir@123' -n monitoring"**

2. In Development Cluster 
       - Apply the probe.yaml to check the application health status. 
**" kubectl apply -f probe.yaml "**

3. Add Custom Dashboard for Application Logs in Grafana:
 
       - Application Logs Dashboard (ACC):

              - Click on New Dashboard.
              - Go to Import Dashboard.
              - Add the JSON file in the Import via Dashboard JSON Model.

       - Application Logs Dashboard (PROD):

              - Click on New Dashboard.
              - Go to Import Dashboard.
              - Add the JSON file in the Import via Dashboard JSON Model.
              
       - Application Logs Dashboard (TST):

              - Click on New Dashboard.
              - Go to Import Dashboard.
              - Add the JSON file in the Import via Dashboard JSON Model.

Note: You can find these JSON files and probe.yaml in the files subfolder within the Readme_Doc folder.