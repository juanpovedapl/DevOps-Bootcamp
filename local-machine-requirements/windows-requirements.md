# Windows local machine requirements

## Contents
- [Windows local machine requirements](#windows-local-machine-requirements)
  - [Contents](#contents)
  - [Installing Docker and Docker Compose](#installing-docker-and-docker-compose)
  - [Installing IBM Cloud tools.](#installing-ibm-cloud-tools)
      - [5. Openshift CLI](#5-openshift-cli)
      - [6. GitHub](#6-github)
  - [GitHub](#github)

## Installing Docker and Docker Compose

1. Go to docker desktop for Windows in [this link](https://docs.docker.com/docker-for-windows/install/)
2. Click on “Docker Desktop for Windows” button, it will download a .exe file. 
3. Once downloaded, click on the downloaded .exe file and allow changes into your machine. Docker will start downloading required packages for installation.
4. Check the “Install required Windows components for WSL 2” and it's up to you to check whether you want a shortcut to desktop or not. Click next.
5. Wait for installation to finish, it will ask to restart your machine, proceed when most convenient for you.

Docker installation in Windows includes docker compose, kubernetes and other useful tools.

## Installing IBM Cloud tools.

1.  Right-click the Windows PowerShell icon, and select Run as administrator
2.  Run the following command:
```
[Net.ServicePointManager]::SecurityProtocol = "Tls12, Tls11, Tls, Ssl3"; iex(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/IBM-Cloud/ibm-cloud-developer-tools/master/windows-installer/idt-win-installer.ps1')
```  

1. Verify the installation running:

```
ibmcloud help
```

After this installation, windows will request to restart your machine.

More info [here](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started)



#### 5. Openshift CLI

1. Download [OC CLI installation file]([link.here](https://downloads-openshift-console.apps-crc.testing/amd64/windows/oc.zip).
2. Follow the instructions [here](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-windows_cli-developer-commands).


#### 6. GitHub
## GitHub
Git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```