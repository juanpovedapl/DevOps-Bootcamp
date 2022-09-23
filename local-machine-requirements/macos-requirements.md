# MacOS local machine requirements

## Contents
- [MacOS local machine requirements](#macos-local-machine-requirements)
  - [Contents](#contents)
  - [Installing Docker and Docker Compose](#installing-docker-and-docker-compose)
  - [Docker installation in Mac includes docker compose, kubernetes and other useful tools.](#docker-installation-in-mac-includes-docker-compose-kubernetes-and-other-useful-tools)
  - [Installing IBM Cloud tools.](#installing-ibm-cloud-tools)
  - [Openshift CLI](#openshift-cli)
  - [GitHub](#github)

## Installing Docker and Docker Compose

1. Go to docker desktop for Mac in [this link](https://docs.docker.com/docker-for-mac/install/)
2. Select your Mac's chip type (Intel or Apple), and check if your Mac is in the minimum supported version in System Requirements section.
3. Follow the instructions to install docker desktop.

Docker installation in Mac includes docker compose, kubernetes and other useful tools.
---

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

---

## Openshift CLI

1. Download [OC CLI installation file](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.7.5/openshift-client-mac-4.7.5.tar.gz).
2. Follow the instructions [here](https://docs.openshift.com/container-platform/4.6/cli_reference/openshift_cli/getting-started-cli.html#cli-installing-cli-on-macos_cli-developer-commands).

---

## GitHub
Git is installed within IBM Cloud Tools, just verify your installation:

```.term1
git --version
```
