- **Type:** #[[__ 🟦  Reference Note]] | [[Azure]] [[Azure App Services]]
- **Source:** https://docs.microsoft.com/en-us/learn/modules/deploy-run-container-app-service/?WT.mc_id=azureportalcard_Service_App%20Services_-inproduct-azureportal 
- **Author:** [[Azure Documentation]] 
- **Summary:** This page of the documentation introduces the reader to Azure Container Registry. After explaining what ACR is and how it works, this tutorial walks through creating a registry, uploading an image to it, and then updating that image. 
- **Highlights:**
    - Create a Docker image and store it in a repository in Azure Container 
Registry. Use Azure App Service to deploy a web application based on the
 Docker image.
    - Configure continuous deployment for the web app by using a webhook that monitors the Docker image for changes.
    - **Introduction**
        - You can build and deploy Azure-based web apps by using Docker containers. This approach ==**enables you to roll out a web app quickly**==. Support for continuous delivery ensures that users see the latest build of the app while minimizing administrative overhead.
        - **This module shows you how to create and store Docker images in Azure 
Container Registry.** You'll see how to use these images to deploy a web 
app. Then, you'll learn how to configure continuous deployment so that 
the web app is redeployed whenever a new version of the image is 
released.
        - By the end of this module, you'll be able to create and maintain web 
apps that use Docker images that are stored in Container Registry.
        - **Learning objectives**
            - Create Docker images and store them in a repository in Container Registry.
            - Use App Service to run web apps that are based on Docker images held in Container Registry.
            - Use webhooks to configure continuous deployment of a web app that's based on a Docker image.
    - **Build and store images by using Azure Container Registry**
        - ==**Azure Container Registry enables you to store Docker images in the cloud, in an Azure storage account.**==
        - In this unit, you'll learn more about Container Registry and the advantages it provides for storing Docker images.
        - **What is Container Registry?**
            - Container Registry is an Azure service that you can use to create your own private Docker registries.
            - Like Docker Hub, Container Registry is organized around repositories that contain one or more images.
            - Container Registry also lets you automate tasks such as redeploying an app when an image is rebuilt.
        - **Using Container Registry**
            - You create a registry by using either the Azure portal or the Azure CLI **acr create** command.
            - In the following code example, the name of the new registry is __myregistry__:
                - `az acr create --name myregistry --resource-group mygroup --sku standard --admin-enabled true`
            - In addition to storing and hosting images, you can also use Container Registry to build images.
            - Instead of building an image yourself and pushing it to Container Registry, use the CLI to upload the Docker file and other files that make up your image. Container Registry will then build the image for you. Use the **acr build** command to run a build:
                - `az acr build --file Dockerfile --registry myregistry --image myimage .`
    - **Exercise - Build and store an image by using Azure Container Registry**
    - **Deploy a web app by using an image from an Azure Container Registry repository**
        - You can deploy a web app to Azure App Service directly from Azure Container Registry.
        - In this unit, you'll learn how you can configure App Service to deploy a web app from a repository in Container Registry.
    - **Exercise - Create and deploy a web app from a Docker image**
    - **Update the image and automatically redeploy the web app**
        - Continuous deployment is a key feature for many fast-moving organizations. They need to deploy the latest version of their software quickly, but with the minimum of fuss.
        - In this unit, you'll configure the continuous deployment of a web app that uses an image in Azure Container Registry.
        - What is a webhook?
            - Azure App Service supports continuous deployment using __webhooks__. A webhook is a service offered by Azure Container Registry. Services and applications can subscribe to the webhook to receive notifications about updates to images in the registry.
            - A web app that uses App Service can subscribe to an Azure Container Registry webhook to receive notifications about updates to the image that contains the web app. When the image is updated, and App Service receives a notification, your app automatically restarts the site and pulls the latest version of the image.
        - What is the Container Registry tasks feature?
            - You use the __tasks__ feature of Container Registry to rebuild your image whenever its source code changes automatically.
            - You configure a Container Registry task to monitor the GitHub repository that contains your code and trigger a build each time it changes. If the build finishes successfully, Container Registry can store the image in the repository. If your web app is set up for continuous integration in App Service, it receives a notification via the webhook and updates the app.
        - Enable continuous integration from App Service
            - The **Container settings** page of an App Service resource in the Azure portal automates the setup of continuous integration.
            - If you turn on **Continuous Deployment**, App Service configures a webhook in your container registry to notify an App Service endpoint. Notifications from the registry that reach this endpoint cause your app to restart and pull the latest version of the container image.
    - **Exercise - Modify the image and redeploy the web app**
    - **Summary**
