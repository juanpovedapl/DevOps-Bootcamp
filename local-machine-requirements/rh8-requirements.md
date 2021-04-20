
#### 1. Installing IBM Cloud tools.

1. For Mac and Linux, run the following command:
```
curl -sL http://ibm.biz/idt-installer | bash
```  
For Windows 10, run the following command (Right-click the Windows PowerShell icon, and select Run as administrator):
```
[Net.ServicePointManager]::SecurityProtocol = "Tls12"; iex(New-Object Net.WebClient).DownloadString('https://ibm.biz/idt-win-installer')
```  
2. Verify the installation running:

```
ibmcloud help
```

After this installation, windows will request to restart your machine.

More info [here](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started)

#### 2. Installing Docker in RHEL

Docker is included and installed in prerequisite 1, in all operative systems (except for RHEL).
If you're working with RHEL follow the next steps:

1. Install required packages
```
sudo yum install -y yum-utils \
device-mapper-persistent-data \
lvm2
```

2. Add **stable** repository
```
sudo yum-config-manager \
--add-repo \
https://download.docker.com/linux/centos/docker-ce.repo
```

3. Install Docker
```
sudo yum install docker-ce docker-ce-cli containerd.io
```

More info [here](https://docs.docker.com/install/linux/docker-ce/centos/)


#### 3. Testing Docker installation

To test your installation in Windows 10 test your installation following the instructions [here](https://docs.docker.com/docker-for-windows/#test-your-installation).

For any other OS, run the following:
```
docker --help
lvm2
```

#### 4. Installing DockerCompose

For RHEL workstations, follow the next steps:

1. Run this command to download the current stable release of Docker Compose:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

2. Apply executable permissions to the binary:
```
sudo chmod +x /usr/local/bin/docker-compose
```

3. Test the installation:
```
docker-compose --version
```
Docker Desktop for Windows and Docker Toolbox already include Compose along with other Docker apps, so most Windows users do not need to install Compose separately.

For other OS or troubleshooting check the link [here](https://docs.docker.com/compose/install/).

#### 5. Openshift CLI

1. Download [OC CLI installation file](link.here), select the corresponding to your OS.
2. Follow the instructions depending on your OS:
- [Linux OC CLI installation instructions](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-linux_cli-developer-commands)
- [Windows OC CLI installation instructions](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-windows_cli-developer-commands)
- [MacOS  OC CLI installation instructions](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-macos_cli-developer-commands)

#### 6. GitHub
Similar to docker, git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```

##### Check your keys in GitHub enterprise

1. Log in to [IBM GitHub Enterprise](https://github.ibm.com/)

2. Click on your profile photo, and go to "Settings", and then click on "SSH and GPG keys":
If you have added your keys before, you're going to see something like the following:

![Check git keys](resources/img/Check_git_keys.gif)

If you don't see any key, follow the instructions in [here](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account) to add a new key.

**Tip:** If you don't feel confident using git in the terminal, you can check and practice with this [cheat-sheet](https://www.git-tower.com/blog/git-cheat-sheet).


### 7. IBM Cloud Kubernetes Cluster creation.
1. Verify if you have an IBM Cloud account with your w3 ID. 
   - Go to [IBM Cloud](https://cloud.ibm.com/login) and login with your w3 credentials.
   - Check in the up-right corner the dropdown list, and verify that your name is listed or selected, as in the following screen:
![IBM Cloud w3 account](resources/img/w3-account.png)
   - If your name is listed, select it and proceed with step 3, if your name is not listed proceed to create a personal account in step 2.

2. Go to [IBM Cloud](https://cloud.ibm.com/login) and create a personal account. Click on **Create an account**.

![Create an account](resources/img/Create-an-account.png)

3. Once logged in, it will display the dashboard of your profile, go to the left menu and click on **Kubernetes**.

![Kubernetes menu](resources/img/ibm-cloud-k8s.png)

4. Now click **Create a cluster**.

![Create a cluster](resources/img/Create%20Cluster.png)

5. Write down the cluster name (any name, i.e. mycluster-bootcamp), settings should look like the following:

![Create a cluster summary](resources/img/kubernetes-cluster-summary.png)

Click **Create cluster**.

6. The cluster has been requested, it will take some minutes to be configured and ready to use. Status will change to green (normal) when it is ready to be used.

![](resources/img/cluster.gif)

### 8. Create an IBM Cloud APIKEY.

As an IBM Cloud user you might want to use an API key when you enable a program or script without distributing your password to the script. To create an API key for your user identity in the UI, complete the following steps:
1. Go to **Manage > Access(IAM) > IBM Cloud API Keys.**
2. Click **Create an IBM Cloud API key.**
3. Enter a name and description for your API key.
4. Click **Create.**
5. Then, click **Show** to display the API key. Or, click **Copy** to copy and save it for later, or click **Download.**

![](resources/img/apikey.gif)

### 9. Connecting to IBM Cloud Kubernetes Service cluster.

1. Log in to your IBM Cloud account. We will use our API key to log in into our cluster.

```
ibmcloud login -apikey <YOUR_APIKEY>
```

<details>
  <summary>Are you having problems in this step?</summary>

>1. Could not find default resource: If you get this issue, try connecting to IBM Cloud KS Cluster with the following:
>
>```
>ibmcloud login -apikey <YOUR_APIKEY>  -r us-south -g Default
>```
</details>

2. Download the kubeconfig files for your cluster.
```
ibmcloud ks cluster config --cluster <YOUR_CLUSTER_NAME>
```
3. Verify kubectl can communicate with your cluster.
```
kubectl cluster-info
```