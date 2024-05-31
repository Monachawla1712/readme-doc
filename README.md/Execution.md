### Terraform cloud Executions Steps

1. Sign up for Terraform cloud.
2. Create an Organization. 
3. Create a project.
4. Create a workspace inside the project.
5. Choose the version control workflow while creating workspace. ( because we want to integrate terraform cloud with a github repo )


( Choose workflow - Version Control workflow , 
CLI - Driven workflow , API - Driven workflow ) 


6. Connect to the Version Control provider - choose github.com(custom)

7. For set up the  provider -
- On Github , register a new OAuth Application - Enter the information given by terraform cloud.
- Application name 
- Homepage URL
- Authorization callback URL
- Enter Client ID  and Client Secret in terraform cloud and click on continue.
- Update the application .

8. Authorize terraform cloud to access the github user.
9. Choose a repository  to automate.


### Syncing Local Terraform State with Terraform Cloud:

1. Log in to Terraform via the terminal:
- terraform login 
- Enter yes
- Provide the API token generated in Terraform Cloud.

2. Update the backend.tf file and add a cloud block that includes the organization name and workspace name.

3. Initialize Terraform:

terraform init - This will now sync the state with Terraform Cloud.




### Automatic Triggering Run (Pipeline):


1. Set up triggers in Terraform cloud :
- Go to specific workspace.
- Go to settings.
- Go to version control 
- Provide the Terraform working directory., e.g., env/02-dev.
- Select auto-apply to enable auto-apply run triggers
- Under VCS Triggers, enable automatic run triggering. 
- Choose the option: Only trigger runs when files in specified paths change.    
- Specify the VCS branch, e.g., main.

Finally update these settings.


    


