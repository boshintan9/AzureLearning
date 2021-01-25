# Build-From-Scratch ARM Template
This template deploys a Windows 10 VM (latest) and a Bastion host to connect through to it. The VM will have internet connectivity via a NAT gateway. Two public IP addresses are deployed - one for Bastion host access and one for the Internet NAT gateway.

## How to Deploy
This template can be deployed via the Azure Cloud Shell or via the Azure Console GUI.

### Azure Cloud Shell
The below code will perform a full deployment without any user prompts. The administrator password to the Windows VM will be generated as one of the deployment's outputs.

When copying the below commands directly, replace the text `your-resource-group` with the name of the resource group under your subscription that you want the ARM template to deploy under.
```powershell
$templateURI = "https://raw.githubusercontent.com/boshintan9/AzureLearning/main/build-from-scratch/azuredeploy.json"
az deployment group create --name "build-from-scratch" --resource-group "your-resource-group" --template-uri $templateURI
```

### Azure Console GUI
#### Create the Template
1. Navigate to [the Azure portal](https://portal.azure.com) and log in. 
2. Using the search bar at the top of the page, type "Templates" and click on "Templates" under "Services" on the left of the drop down.
3. Click the + Add button to create a new template. Give the template a name and meaningful description and click "OK" in the bottom left. This will take you to the Azure template editor.
4. In a new browser tab, [open the raw json view of this repo's ARM template](https://raw.githubusercontent.com/boshintan9/AzureLearning/main/build-from-scratch/azuredeploy.json). Copy all text from this page.
5. Back in the tab with the template editor, delete the pre-generated template text and paste in the copied content.
6. Go through the template and remove all of the line comments (denoted by two forward slashes).
7. Click OK when you are done.

#### Deploy the Template
1. The new template should now be listed under the Templates page. Click on the template and an overloay should open wiht the template's name at the top - click the "Deploy" button.
2. The "Custom Deployment" page should open. Select the Resource Group that you wish the template to deploy under. All other fields should be automatically filled.
3. Check the "I agree to the terms and conditions stated above" box at the bottom of the page.
4. Click the "Purchase" button to initiate deployment. Note: If you are using a Visual Studio subscription, there are no deployment elements in this template that would incur charges outside of your credit.

#### Review Deployment
1. Once the deployment has completed, open the resource group that you deployed the template to and select "Settings" -> "Deployments"
2. The name of the deployment will read as "user_account.template-name", but it should be the most recent one. Click on the deployment.
3. From the deployment overview page, click on "Outputs" on the left. This page will list the Window's VM administrator username and generated password. Note: this is not best practice.

## Before You Go
Don't forget to delete all of the resources that were created as part of this deployment!