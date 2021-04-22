
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

By default podman and podman-compose  is installed on RH 8.x, verify your installation:

```.term1
podman --version
```
In case it is not installed, please follow the next steps:

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

3. Enable container and install **podamn**

```.term1
sudo yum module enable -y container-tools:1.0

sudo yum module install -y container-tools:1.0
```

More [info](https://podman.io/getting-started/installation)

4. Verify your installation:
```.term1
podman --version
```

5. In order to install **podman-compose** run on your terminal:
```.term1
podman-compose
 ```

And type **y** to accept the installation of the packages and proceed with the changes. And verify your installation:

```.term1
podman-compose version
```
Podman installation in RedHat 8.x includes kubernetes and other useful tools.

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

1. If you have a RedHat account, please follow this instrucctions [here](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-rpm_cli-developer-commands).
2. If you don't have a redhat account download [OC CLI installation file](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/openshift-client-linux-4.7.5.tar.gz).
2.1 Follow the instructions [here](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-linux_cli-developer-commands).


## GitHub
Git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```
