
# RedHat 8.x local machine requirements

## Contents
- [RedHat 8.x machine requirements](#RedHat8.x-machine-requirements)
  - [Contents](#contents)
  - [Installing Podman and Podman-Compose](#installing-podman-and-podman-compose)
  - [Installing IBM Cloud tools.](#installing-ibm-cloud-tools)
  - [Add test environment to your hosts file](#add-test-environment-to-your-hosts-file)
  - [Openshift CLI](#openshift-cli)
  - [GitHub](#github)

## Installing Podman and Podman-Compose

### By default **podman** is installed on RH 8.x, verify your installation:

```.term1
podman --version
```
In case it is not installed, please follow the next steps:

1. Enable EPEL and codeready-builder repository
```
sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

sudo subscription-manager repos --enable codeready-builder-for-rhel-8-rpms
```

2. Enable container-tools and install **podamn**

```.term1
sudo yum module enable -y container-tools

sudo yum module install -y container-tools
```

More [info](https://podman.io/getting-started/installation)

3. Verify your installation running:
```.term1
podman version
```

4. In order to install **podman-compose** run on your terminal:
```.term1
sudo yum install podman-compose
 ```
Verify your installation:

```.term1
podman-compose version
```

## Installing IBM Cloud tools.

1. Run the following command:
```
curl -sL http://ibm.biz/idt-installer | bash
```  

2. Verify the installation running:
```
ibmcloud help
```

More info [here](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started)

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

1. Download [OC CLI installation file](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/openshift-client-linux-4.7.5.tar.gz).

2. Locate the path where download is saved and create a folder to decompress. And then decompress the file running:
```.term1
tar xvfz openshift-client-linux-4.7.5.tar.gz -C <folder>
```
3. Export variable running:
```.term1
cd <folder>
pwd
export PATH=$PATH:<pwd_direction>
```
4. Verify the installation running:
```.term1
oc version

kubectl version
```

More [info](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-linux_cli-developer-commands).


## GitHub
Git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git version
```
