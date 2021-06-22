- **Type:** #[[__ 🟦  Reference Note]] | [[Blockchain]]
- **Source:** [[Hyperledger Fabric Documentation]] https://hyperledger-fabric.readthedocs.io/en/latest/prereqs.html
- **Project(s):** [[📦 Grokking Blockchain]] [[📦 Building Blockchain Applications with Hyperledger Fabric]] [[📦 Article: Setting up your computer for Hyperledger Fabric]]
- **Summary:** This page of the documentation walks you through the prerequisites you'll need on your mac in order to get started developing applications with Hyperledger Fabric. Specifically, it walks you through Git, cURL, Docker, and Docker Compose. 
- **Highlights:**
    - Before you begin, you should confirm that you have installed all the 
prerequisites below on the platform where you will be running 
Hyperledger Fabric.
    - **These instructions are for a mac**
    - **Prerequisites:** [[🟨 Prerequisites to developing with Hyperledger Fabric]]
        - **Git**
            - Download the latest version of [git](https://git-scm.com/downloads) if it is not already installed, or if you have problems running the curl commands.
        - **cURL**
            - Download the latest version of the [cURL](https://curl.haxx.se/download.html) tool if it is not already installed or if you get errors running the curl commands from the documentation.
        - **Docker and Docker Compose**
            - You will need bock Docker and Docker Compose installed
            - You can check the version of Docker you have installed with the following
command from a terminal prompt: `docker --version`
            - Make sure the docker daemon is running: `sudo systemctl start docker`
            - Optional: If you want the docker daemon to start when the system starts, use the following: `sudo systemctl enable docker`
            - Add your user to the docker group: `sudo usermod -a -G docker <username>`
            - You can check the version of Docker Compose you have installed with the
following command from a terminal prompt: `docker-compose --version`
