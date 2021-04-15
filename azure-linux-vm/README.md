# Linux virtual machines in Azure

Azure Virtual Machines (VM) is one of several types of [on-demand, scalable computing resources](/azure/architecture/guide/technology-choices/compute-decision-tree) that Azure offers. Typically, you choose a VM when you need more control over the computing environment than the other choices offer. This article gives you information about what you should consider before you create a VM, how you create it, and how you manage it.

Azure virtual machines can be used in various ways. Some examples are:

* **Development and test** – Azure VMs offer a quick and easy way to create a computer with specific configurations required to code and test an application.
* **Applications in the cloud** – Because demand for your application can fluctuate, it might make economic sense to run it on a VM in Azure. You pay for extra VMs when you need them and shut them down when you don’t.
* **Extended datacenter** – Virtual machines in an Azure virtual network can easily be connected to your organization’s network.

The number of VMs that your application uses can scale up and out to whatever is required to meet your needs.

## What do I need to think about before creating a VM?
There are always a multitude of [design considerations](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/windows-vm) when you build out an application infrastructure in Azure. These aspects of a VM are important to think about before you start:

* The names of your application resources
* The location where the resources are stored
* The size of the VM
* The maximum number of VMs that can be created
* The operating system that the VM runs
* The configuration of the VM after it starts
* The related resources that the VM needs

## Availability
Azure announced an industry leading single instance virtual machine Service Level Agreement of 99.9% provided you deploy the VM with premium storage for all disks.  In order for your deployment to qualify for the standard 99.95% VM Service Level Agreement, you still need to deploy two or more VMs running your workload inside of an availability set. An availability set ensures that your VMs are distributed across multiple fault domains in the Azure data centers as well as deployed onto hosts with different maintenance windows. The full [Azure SLA](https://azure.microsoft.com/support/legal/sla/virtual-machines/) explains the guaranteed availability of Azure as a whole.

## Distributions 
Microsoft Azure supports running a number of popular Linux distributions provided and maintained by a number of partners.  You can find distributions such as Red Hat Enterprise, CentOS, SUSE Linux Enterprise, Debian, Ubuntu, CoreOS, RancherOS, FreeBSD, and more in the Azure Marketplace. Microsoft actively works with various Linux communities to add even more flavors to the [Azure endorsed Linux Distros](endorsed-distros.md) list.

If your preferred Linux distro of choice is not currently present in the gallery, you can "Bring your own Linux" VM by [creating and uploading a Linux VHD in Azure](create-upload-generic.md).

Microsoft works closely with partners to ensure the images available are updated and optimized for an Azure runtime.  For more information on Azure partners, see the following links:

* Linux on Azure - [Endorsed Distributions](endorsed-distros.md)
* SUSE - [Azure Marketplace - SUSE Linux Enterprise Server](https://azuremarketplace.microsoft.com/marketplace/apps?search=suse%20sles&page=1)
* Red Hat - [Azure Marketplace - Red Hat Enterprise Linux 8.1](https://azuremarketplace.microsoft.com/marketplace/apps/RedHat.RedHatEnterpriseLinux81-ARM)
* Canonical - [Azure Marketplace - Ubuntu Server](https://azuremarketplace.microsoft.com/marketplace/apps/Canonical.UbuntuServer)
* Debian - [Azure Marketplace - Debian 8 "Jessie"](https://azuremarketplace.microsoft.com/marketplace/apps/credativ.debian)
* FreeBSD - [Azure Marketplace - FreeBSD 10.4](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.FreeBSD104)
* CoreOS - [Azure Marketplace - Container Linux by CoreOS](https://azuremarketplace.microsoft.com/marketplace/apps/CoreOS.CoreOS)
* RancherOS - [Azure Marketplace - RancherOS](https://azuremarketplace.microsoft.com/marketplace/apps/rancher.rancheros)
* Bitnami - [Bitnami Library for Azure](https://azure.bitnami.com/)
* Mesosphere - [Azure Marketplace - Mesosphere DC/OS on Azure](https://azure.microsoft.com/services/kubernetes-service/mesosphere/)
* Docker - [Azure Marketplace - Docker images](https://azuremarketplace.microsoft.com/marketplace/apps?search=docker&page=1&filters=virtual-machine-images)
* Jenkins - [Azure Marketplace - CloudBees Jenkins Platform](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/cloudbees.cloudbees-core-contact)