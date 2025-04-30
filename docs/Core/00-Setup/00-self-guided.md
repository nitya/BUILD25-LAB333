# Lab 1: Setup AI Project

!!! quote "BY THE END OF THIS LAB YOU SHOULD HAVE"

    1. A personal copy of the workshop repo in your GitHub profile
    1. A pre-configured development environment in GitHub Codespaces
    1. An provsisoned Azure AI project in Azure AI Foundry

!!! info "IN-VENUE LAB ATTENDEES CAN SKIP THIS STEP - you will get a pre-provisioned Azure subscription"

---

## 1. Launch GitHub Codespaces

This repository is configured with a `devcontainer.json` that can be activated in GitHub Codespaces (cloud) or Docker Desktop (local device) to give you a prebuild development environment with least effort. **We recommend using GitHub Codespaces for this lab.**

1. Log into your personal GitHub profile
1. Fork this repo to get a personal copy in your profile.
1. Open the forked repo in your browser and click on the green 
1. Select the `Codespaces` tab and create a new codespace.

**This will open a new tab with a VS Code editor in the browser.** Wait till the editor is fully loaded and the Visual Studio Code terminal is active.

---

## 2. Verify Azure CLI Exists

1. The `devcontainer` should have the Azure CLI pre-installed. Verify this now: 

    ``` title="" linenums="0"
    az version
    ```

1. You should see something like: 

    ``` title="" linenums="0"
    {
    "azure-cli": "2.71.0",
    "azure-cli-core": "2.71.0",
    "azure-cli-telemetry": "1.1.0",
    "extensions": {}
    }
    ```

---

## 3. Authenticate with Azure

1. Use the Azure CLI to log into your Azure account using this command.

    ``` title="" linenums="0"
    az login --use-device-code
    ```

1. This starts a browser-based authentication flow. Follow the instructions in the terminal to complete the login process. Then return to the VS Code terminal. **You are now connected to your Azure backend from the codespace**.


---

## 4. Deploy with Azure CLI

1. Next, use the Azure CLI to create a new resource group for the lab. This sets up a resource group called `rg-lab-reasoning` in the `EastUS 2` region.

    ``` title="" linenums="0"
    az group create --name rg-lab-reasoning --location 'EastUS 2'
    ```

1. You should see something like this. **Your resource group is ready to be provisioned**.

    ``` title="" linenums="0"
    {
        "id": "/subscriptions/XXXXXX/resourceGroups/rg-lab-reasoning",
        "location": "eastus2",
        "managedBy": null,
        "name": "rg-lab-reasoning",
        "properties": {
            "provisioningState": "Succeeded"
        },
        "tags": null,
        "type": "Microsoft.Resources/resourceGroups"
    }
    ```

1. Now, use this command to deploy the defined template to that resource group. 

    ``` title="" linenums="0"
    az deployment group create --name reasoning-template --resource-group rg-lab-reasoning --template-file infra/template.json
    ```

1. You will be prompted for a **uniqueSuffix** - provide a random 4-digit number. This will reduce naming conflicts with soft-deleted resources from previous runs, that aren't yet purged.

1. The script takes a few minutes to run. Next, we'll validate the setup.
