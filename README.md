# azure-iothub
A role to create IoT Hub in Azure

Azure IoT Hub is a cloud-based service provided by Microsoft that allows for easy management of Internet of Things (IoT) devices and their data. It provides a secure and scalable platform for connecting, monitoring, and managing IoT devices and their data, allowing for real-time insights and actions.

Azure IoT Hub supports a variety of communication protocols, including HTTPS, MQTT, and AMQP, and can integrate with a range of devices and platforms, such as Raspberry Pi, Arduino, and other IoT devices. It also provides features for device provisioning, device-to-cloud and cloud-to-device messaging, device management, and security.

With Azure IoT Hub, users can connect and manage millions of devices, monitor device health and performance, and analyze data from IoT devices to gain valuable insights and take appropriate actions. It can also integrate with other Azure services, such as Azure Stream Analytics and Azure Functions, to enable real-time processing and automated actions based on IoT data.

Overall, Azure IoT Hub simplifies IoT device management, enhances security, and enables efficient data processing and analysis, making it an integral part of any IoT solution.

# Requirements

## Applications

You will need to have the following installed and configured on your local host.

- Podman or Docker
- Python 3.8+
- Ansible, Ansible Runner, Ansible Navigator

## Azure Tenancy and Subscription

This demo assumes that you have permissions to create, manage, and destroy Azure resources such as Resource Groups, Virtual Machines, Networking, etc.  If you do not have access to a tenancy and subscription with access to those resources, then you will receive errors when attempting to run automation in later steps.

## Azure CLI

This guide will assume that the Azure CLI is using the default path `$HOME/.azure` as its path.

If you have the Azure CLI already installed on your local machine, then run `az login` to ensure that you have an active session.  You can skip to the next section.

If you do not have the Azure CLI installed on your local machine, then we can use a container to setup the CLI authentication without having to install the CLI on your local PC.

1. Create a directory in your home directory for the Azure configuration: `mkdir $HOME/.azure`
2. Pull a container with the Azure CLI: `docker pull bitnami/azure-cli:latest`
3. Login to Azure with the CLI in the container: `docker run -it --rm -v $HOME/.azure:/.azure bitnami/azure-cli:latest login`
4. Follow the instructions to login to Azure with your web browser. Once logged in, be sure to wait until the CLI recognizes the login.

## Create a Service Principal

1. Create a service principal for Ansible operations on Azure.
    - Running the CLI on your host: `az ad sp create-for-rbac --name ansible --role Contributor`
    - Running the CLI in a container: `docker run -it --rm -v $HOME/.azure:/.azure bitnami/azure-cli:latest ad sp create-for-rbac --name ansible --role Contributor`
2. Edit a new text file at `$HOME/.azure/credentials`
3. Paste the following replacing the values with the output of command in step 1.

```plaintext
[default]
subscription_id=xxxxxxx-xxxxx-xx-xxxxx
client_id=xxxxxxx-xxxxx-xx-xxxxx
secret=xxxxxxx-xxxxx-xx-xxxxx
tenant=xxxxxxx-xxxxx-xx-xxxxx
```

4. Save the file and exit.

# Dependencies

# Ansible Tags

# Role Variables

# License

# Change Log