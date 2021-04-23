# RedHat 7.x local machine requirements

## Contents
- [RedHat 7.x local machine requirements](#redhat-7x-local-machine-requirements)
  - [Contents](#contents)
  - [Installing IBM Cloud tools](#installing-ibm-cloud-tools)
  - [Installing Docker Engine](#installing-docker-engine)
  - [Installing Docker Compose](#installing-docker-compose)
  - [Add test environment to your hosts file](#add-test-environment-to-your-hosts-file)
  - [Openshift CLI](#openshift-cli)
  - [GitHub](#github)

## Installing IBM Cloud tools

1. For Linux, run the following command:
```
curl -sL http://ibm.biz/idt-installer | bash
```  

2. Verify the installation running:

```
ibmcloud help
```

You can find more info [here](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started).

## Installing Docker Engine

Docker is included and installed in prerequisite 1, if docker is not installed after IBM Clouds tools installation completed, please follow the next steps:

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


4. Testing Docker installation

Run the following:

```
docker --help
```

## Installing Docker Compose

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

For troubleshooting check the link [here](https://docs.docker.com/compose/install/).

## Add test environment to your hosts file
1. Open a terminal window and execute:
```
sudo vi /etc/hosts
```

Type your user session password, and add the following line at the end of the file:
```
9.220.50.15 api.crc.testing console-openshift-console.apps-crc.testing default-route-openshift-image-registry.apps-crc.testing oauth-openshift.apps-crc.testing
```

Verify you can ping one of the aliases as in the example below:
```
$ ping console-openshift-console.apps-crc.testing
PING api.crc.testing (9.220.50.15): 56 data bytes
64 bytes from 9.220.50.15: icmp_seq=0 ttl=53 time=101.662 ms
...
```

## Openshift CLI

1. Download [OC CLI installation file](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/), select the corresponding to your OS. i.e. `openshift-client-linux-4.7.5.tar.gz`

2. Execute following commands to get your oc binary working 

```
wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/openshift-client-linux-4.7.5.tar.gz .
tar zxvf openshift-client-linux-4.7.5.tar.gz
mv oc /usr/local/bin/
oc version
```

For more information refer following link: [Linux OC CLI installation instructions](https://docs.openshift.com/container-platform/4.7/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-linux_cli-developer-commands)

## GitHub
Similar to docker, git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```