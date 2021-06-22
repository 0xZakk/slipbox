- **Type:** #[[__ 🟦  Reference Note]] | [[Blockchain]]
- **Source:** [[Hyperledger Fabric Documentation]] https://hyperledger-fabric.readthedocs.io/en/latest/install.html 
- **Project(s):** [[📦 Grokking Blockchain]] [[📦 Building Blockchain Applications with Hyperledger Fabric]] [[📦 Article: Setting up your computer for Hyperledger Fabric]]
- **Summary:** This page of the documentation walks you through downloading everything necessary to start running Hyperledger Fabric. Currently, there isn't a real installer for the Fabric binaries, so you download everything by cloning a repository from GitHub and running a bash script from within that repository. The bash script downloads a list of binaries as well as a set of docker images from Docker Hub.
- **Highlights:**
    - [[🟨 Installing Hyperledger Fabric]]
    - While we work on developing real installers for the Hyperledger Fabric
binaries, we provide a script that will download and install samples and
binaries to your system. We think that you’ll find the sample applications
installed useful to learn more about the capabilities and operations of
Hyperledger Fabric.
    - Determine a location on your machine where you want to place the fabric-samples repository and enter that directory in a terminal window. The
command that follows will perform the following steps:
        - If needed, clone the [hyperledger/fabric-samples](https://github.com/hyperledger/fabric-samples) repository
        - Checkout the appropriate version tag
        - Install the Hyperledger Fabric platform-specific binaries and config files
for the version specified into the /bin and /config directories of fabric-samples
        - Download the Hyperledger Fabric docker images for the version specified
    - Once you are ready, and in the directory into which you will install the
Fabric Samples and binaries, go ahead and execute the command to pull down the binaries and images:
        - `curl -sSL https://bit.ly/2ysbOFE | bash -s`
    - The command above ^^**downloads and executes a bash script
that will download and extract all of the platform-specific binaries you
will need to set up your network**^^ and place them into the cloned repo you
created above.
    - It retrieves the following platform-specific binaries and places them in the bin sub-directory of the current working directory:
        - `configtxgen`,
        - `configtxlator`,
        - `cryptogen`,
        - `discover`,
        - `idemixgen`
        - `orderer`,
        - `peer`,
        - `fabric-ca-client`,
        - `fabric-ca-server`
- You may want to add that to your PATH environment variable so that these
can be picked up without fully qualifying the path to each binary. e.g.:
    - `export PATH=<path to download location>/bin:$PATH`
- Finally, the script will download the Hyperledger Fabric docker images from
[Docker Hub](https://hub.docker.com/u/hyperledger/) into your local Docker registry and tag them as ‘latest’.
