- **Type:** #[[__ 🟦  Reference Note]] | [[Azure]] [[Azure App Services]]
- **Source:** https://docs.microsoft.com/en-us/learn/modules/host-a-web-app-with-azure-app-service/ 
- **Author:** [[Azure Documentation]] 
- **Summary:** 
- **Highlights:**
    - **Introduction**
        - Hosting your web application using Azure App Service makes deploying and managing a web app much easier when compared to managing a physical 
server. In this module, we'll implement and deploy a web app to App 
Service.
        - **Learning objectives:**
            - Use the Azure portal to create an Azure App Service web app
            - Use developer tools to create the code for a starter web application
            - Deploy your code to App Service
    - **Create a web app in the Azure portal**
        - There are several ways you can create a web app. You can use the Azure 
portal, the Azure Command Line Interface (CLI), a script, or an IDE.
        - The information presented below will discuss how to use the Azure portal
 to create a web app, and in the next exercise you will use this 
information to create a web app.
        - What is [[Azure App Services]]? [[🟨 What is Azure App Services]]
            - Azure App Service is **a fully managed web application hosting platform**. This platform as a service (PaaS) offered by Azure **allows you to focus on designing and building your app** while Azure takes care of the infrastructure to run and scale your applications.
            - Deployment slots
                - Using the Azure portal, you can easily add **deployment slots** to an App Service web app.
                - For instance, you can create a **staging** deployment slot where you can push your code to test on Azure. Once you are happy with your code, you can easily **swap** the staging deployment slot with the production slot. You do all this with a few simple mouse clicks in the Azure portal.
            - **Continuous integration/deployment support**
                - The Azure portal provides **out-of-the-box continuous integration and 
deployment** with Azure DevOps, GitHub, Bitbucket, FTP, or a local Git 
repository on your development machine.
                - **Connect your web app with any of the above sources and App Service will 
do the rest for you by automatically syncing your code and any future 
changes on the code into the web app.**
                - Furthermore, with Azure DevOps, you can define your own build and 
release process that compiles your source code, runs the tests, builds a
 release, and finally deploys the release into your web app every time 
you commit the code. All that happens implicitly without any need to 
intervene.
            - Built-in auto scale support (automatic scale-out based on real-world load)
                - Baked into the web app is the ability to scale up/down or scale out.
                - Depending on the usage of the web app, you can scale your app up/down by
 increasing/decreasing the resources of the underlying machine that is 
hosting your web app.
                - Resources can be number of cores or the amount of RAM available.
                - Scaling out, on the other hand, is the ability to increase the number of machine instances that are running your web app.
        - Creating a web app
            - When you're ready to run a web app on Azure, you visit the Azure portal and create a **Web App** resource.
            - Creating a web app allocates a set of hosting resources in App Service, 
which you can use to host any web-based application that is supported by
 Azure, whether it be ASP.NET Core, Node.js, Java, Python, etc.
        - Operating systems
            - If you are deploying your app as code, many of the available runtime 
stacks are limited to one operating system or the other. After choosing a
 runtime stack, the toggle will indicate whether or not you have a 
choice of operating system.
            - If your application is packaged as a Docker image, choose the operating system on which your image is designed to run.
        - App Service plans
            - An **App Service plan** is a set of virtual server resources that run App Service apps.
            - A plan's **size** (sometimes referred to as its **sku** or **pricing tier**)
 determines the performance characteristics of the virtual servers that 
run the apps assigned to the plan and the App Service features that 
those apps have access to. Every App Service web app you create must be 
assigned to a single App Service plan that runs it.
            - A single App Service plan can host multiple App Service web apps. In 
most cases, the number of apps you can run on a single plan will be 
limited by the performance characteristics of the apps and the resource 
limitations of the plan.
            - App Service plans are the unit of billing for App Service. The size of 
each App Service plan in your subscription, in addition to the bandwidth
 resources used by the apps deployed to those plans, determines the 
price that you pay.
    - **Deploy code to App Service**
        - Automated deployment
            - Automated deployment, or continuous integration, is a process used to 
push out new features and bug fixes in a fast and repetitive pattern 
with minimal impact on end users.
            - Azure supports automated deployment directly from several sources.
            - **Azure DevOps**: You can push your code to Azure DevOps 
(previously known as Visual Studio Team Services), build your code in 
the cloud, run the tests, generate a release from the code, and finally,
 push your code to an Azure Web App.
            - **GitHub**: Azure supports automated deployment directly 
from GitHub. When you connect your GitHub repository to Azure for 
automated deployment, any changes you push to your production branch on 
GitHub will be automatically deployed for you.
        - Manual deployment
            - **Git**: App Service web apps feature a Git URL that you 
can add as a remote repository. Pushing to the remote repository will 
deploy your app.
            - **Visual Studio**: Visual Studio features an App Service deployment wizard that can walk you through the deployment process.
    - **Summary**
        - App Service simplifies managing and controlling your web app in comparison to traditional hosting options.
        - App Service can help you reduce the time and effort spent running and 
managing your web app, and provide advanced cloud features such as auto 
scaling and Git integration.
