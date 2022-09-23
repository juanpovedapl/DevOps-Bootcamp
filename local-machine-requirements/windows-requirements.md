# Windows local machine requirements

## Contents
- [Windows local machine requirements](#windows-local-machine-requirements)
  - [Contents](#contents)
  - [Installing Docker and Docker Compose](#installing-docker-and-docker-compose)
  - [GitHub](#github)
  - [Installing IBM Cloud tools](#installing-ibm-cloud-tools)
  - [Openshift CLI](#openshift-cli)


## Installing Docker and Docker Compose

1. Go to docker desktop for Windows in [this link](https://docs.docker.com/docker-for-windows/install/)
2. Click on “Docker Desktop for Windows” button, it will download a .exe file. 
3. Once downloaded, click on the downloaded .exe file and allow changes into your machine. Docker will start downloading required packages for installation.
4. Check the “Install required Windows components for WSL 2” and it's up to you to check whether you want a shortcut to desktop or not. Click next.
5. Wait for installation to finish, it will ask to restart your machine, proceed when most convenient for you.

Docker installation in Windows includes docker compose, kubernetes and other useful tools.

---

## GitHub
1. Go to [Git official page](https://git-scm.com/download/win) and under “Git for Windows Setup”, select the option that suits your machine architecture.
   
2. Run Git for Windows launcher allowing application to make changes in your device.
3. Accept the license and for each configuration accept the defaults (unless you want to configure or change them).
4. Once finished, launch Git in Windows, there are two ways:
   1.  you can do it using PowerShell and typing:
   
```
git --version
```

   1. Using Git Bash, which is a shell designed for git. Search in your machine “Git Bash” and execute it, once open type the following:

```
git --version
```

---  

## Installing IBM Cloud tools

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

---

## Openshift CLI

1. Download [OC CLI installation file](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/openshift-client-windows-4.7.5.zip).
2. Follow the instructions [here](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-windows_cli-developer-commands).
