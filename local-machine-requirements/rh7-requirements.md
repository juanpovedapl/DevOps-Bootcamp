
#### 1. Installing IBM Cloud tools.

1. For Mac and Linux, run the following command:
```
curl -sL http://ibm.biz/idt-installer | bash
```  
2. Verify the installation running:

```
ibmcloud help
```
More info [here](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started)

#### 2. Installing Docker Engine

>Docker is included and installed in prerequisite 1, if docker is not installed after IBM Clouds tools installation completed, please follow the next steps:

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

Run the following:
```
docker --help
lvm2
```

#### 4. Installing DockerCompose

For RHEL7 workstations, follow the next steps:

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
For other OS or troubleshooting check the link [here](https://docs.docker.com/compose/install/).

#### 5. Openshift CLI

1. Download [OC CLI installation file](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/), select the corresponding to your OS. i.e. `openshift-client-linux-4.7.5.tar.gz`

2. Execute following commands to get your oc binary working 

```
wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/openshift-client-linux-4.7.5.tar.gz .
tar zxvf openshift-client-linux-4.7.5.tar.gz
mv oc /usr/local/bin/
oc version
```

For more information refer following link: [Linux OC CLI installation instructions](https://docs.openshift.com/container-platform/4.7/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-linux_cli-developer-commands)

#### 6. GitHub
Similar to docker, git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```
