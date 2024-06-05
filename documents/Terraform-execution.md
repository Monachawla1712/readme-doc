## Steps for Terraform Cloud Setup and Integration with GitHub
### Setting Up Terraform Cloud:

1. Sign Up for Terraform Cloud.
    - Visit the Terraform Cloud website and sign up for an account.

2. Create an Organization. 
    - After logging in, create a new organization for your projects.

3. Create a project.
    - Within your organization, create a new project to group related workspaces.

4. Create workspaces.
    - Inside your project, create new workspaces.

5. Select Version Control Workflow:
    - When creating each workspace, choose the version control workflow to integrate with a GitHub repository.

6. Connect to GitHub:
    - Select GitHub.com (custom) as your version control provider.



### Setting Up the GitHub OAuth Application:
7. Register a New OAuth Application on GitHub:

    - Go to GitHub and register a new OAuth application. Provide the necessary information from Terraform Cloud:

        - Application name 
        - Homepage URL
        - Authorization callback URL

8. Enter OAuth Credentials in Terraform Cloud:

    - Enter the Client ID and Client Secret from GitHub into Terraform Cloud and proceed.

9. Update GitHub Application:

    - Finalize the OAuth application setup on GitHub by updating the application.

10. Authorize Terraform Cloud:

    - Authorize Terraform Cloud to access your GitHub account.

11. Select a Repository:

    - Choose the repository you want Terraform Cloud to automate.

## Adding a Variable in Terraform cloud at the Organization Level. 

1. Set the Digital Ocean Token Variable in Terrform Cloud.

    - Navigate to Settings in Terraform Cloud.
    - Create a new Variable Set.
    - Add a new variable named digitalocean_token.
    - Under the Variable Set Scope, choose to apply it to specific projects and workspaces.
    - Select the project and workspaces where you want to use this variable.

### Syncing Local Terraform State with Terraform Cloud:

1. Login to Terraform via Terminal:
    - Run terraform login and follow the prompts.
    - Enter yes and provide the API token generated from Terraform Cloud.

2. Update Backend Configuration:

    - Modify your backend.tf file to include a cloud block with your organization and workspace names.

3. Initialize Terraform:

    - Run **terraform init** to sync your local state with Terraform Cloud.




### Setting Up Automatic Run Triggers (Pipeline):

1. Configure Triggers in Terraform Cloud:

    - Navigate to the specific workspace.
    - Go to the Settings tab and select Version Control.

2. Specify Working Directory and Enable Auto-Apply:

    - Provide the Terraform working directory (e.g., env/02-dev).
    - Enable the auto-apply option to trigger automatic runs.

3. Configure VCS Triggers:

    - Enable automatic run triggering under VCS Triggers.
    - Select the option to trigger runs only when files in specified paths change.
    - Specify the branch (e.g., main).

4. Save and Update Settings:

    - Update these settings to finalize the automatic trigger configuration.

By following these steps, you will have Terraform Cloud integrated with your GitHub repository, allowing for automated and synchronized infrastructure management.


**Whenever anything is pushed to the specified location in the GitHub repository, the workspaces will trigger automatically and create plans. However, the apply step will need to be done manually, as it is a crucial step.**








