# MacOS local machine requirements

## Contents
- [MacOS local machine requirements](#macos-local-machine-requirements)
  - [Contents](#contents)
  - [Installing Docker and Docker Compose](#installing-docker-and-docker-compose)
  - [Installing IBM Cloud tools.](#installing-ibm-cloud-tools)
  - [Add test environment to your hosts file](#add-test-environment-to-your-hosts-file)
  - [Openshift CLI](#openshift-cli)
  - [GitHub](#github)

## Installing Docker and Docker Compose

1. Go to docker desktop for Mac in [this link](https://docs.docker.com/docker-for-mac/install/)
2. Select your Mac's chip type (Intel or Apple), and check if your Mac is in the minimum supported version in System Requirements section.
3. Follow the instructions to install docker desktop.

Docker installation in Mac includes docker compose, kubernetes and other useful tools.

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

Type your Mac user password, and add the following line at the end of the file:
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

1. Download [OC CLI installation file](https://downloads-openshift-console.apps-crc.testing/amd64/mac/oc.zip).
2. Follow the instructions [here](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-macos_cli-developer-commands).


## GitHub
Git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```