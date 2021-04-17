# Custom VMSS Deployment Walkthrough

[home](../README.md)

## Technical Implementation

### Step 1 - Create Custom Image Virtual Machine

1. Create [Linux - Ubuntu](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal) VM via Azure Portal

   ![create-linux-vm](./media/create-linux-vm.png)

1. Configure VM as Ngnix Server
   Install web server
   ```
   sudo apt-get -y update
   sudo apt-get -y install nginx
   ```
   ![configure-ngnix-svr](./media/configure-ngnix-svr.png)
1. Prepare VM images

   [Generalized and Specialized images](https://docs.microsoft.com/en-us/azure/virtual-machines/shared-image-galleries#generalized-and-specialized-images)

   **Option 1 - Create Custom Image from Generalized VM**

   [How to create a managed image of a virtual machine or VHD](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/capture-image)

   \*Only follow the steps to generalize the VM

   **Option 2 - Create Disk Snapshot from Specialized VM**

   [Create a snapshot using the portal or PowerShell](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/snapshot-copy-managed-disk)

   ![create-disk-snapshot](./media/create-disk-snapshot.png)

### Step 2 - Create Shared Image Gallery

1. Create [Shared Image Gallery](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/shared-images-portal)

   ![create-shared-gallery](./media/create-shared-gallery.png)

1. Capture generalized VM with versioning

   - View VM information

   ![capture-generalized-vm](./media/capture-generalized-vm.png)

   - Capture the image and store it in image gallery

   ![capture-generalized-vm-p2](./media/capture-generalized-vm-p2.png)

1. Test the created VM with new VM instance

   - Find the created image in image gallery

   ![view-captured-img](./media/view-captured-img.png)

   - Create a new VM from the image

   ![test-custom-img](./media/test-custom-img.png)

   - View the new VM information

   ![test-custom-img-p2](./media/test-custom-img-p2.png)

   - Check the connectivity and expected response

   ![test-custom-img-p3](./media/test-custom-img-p3.png)

### Step 3 - Create Virtual Machine Scale Sets

1. Create [Virtual Machine Scale Sets](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-portal) based on Custom Image and Load Balancer

   - Search Virtual Machine Scale Set in Marketplace

   ![create-vmss-p1](./media/create-vmss-p1.png)

   - Create VMSS with Custom Image

   ![create-vmss-p2](./media/create-vmss-p2.png)

   - Configure Network Interface of VMSS with **inbound rules**

   ![create-vmss-p3](./media/create-vmss-p3.png)

   - Configure **Load Balancer** and backend pool

   ![create-vmss-p4](./media/create-vmss-p4.png)

   - Configure **Scaling policy**

   ![create-vmss-p5](./media/create-vmss-p5.png)

   - Configure **Upgrade Policy**

   ![create-vmss-p6](./media/create-vmss-p6.png)

   - Configure **Health Probe**

   ![create-vmss-p7](./media/create-vmss-p7.png)

1. Review VMSS and connectivity

   - Review Resource Group

   ![review-vmss-p1](./media/review-vmss-p1.png)

   - Check Load Balancer and Public IP Address

   ![review-vmss-p2](./media/review-vmss-p2.png)

   - Check VMSS instances

   ![review-vmss-p4](./media/review-vmss-p4.png)

   - Check VMSS connectivity

   ![review-vmss-p3](./media/review-vmss-p3.png)

### FAQ

1. What are the alternative options for deploying custom VMSS without Shared Image Gallery?

   - Upload a VHD and create an image from it
   - Change the image your scale set uses by updating the image reference ID property using Cloud Shell: (more information please refer to [Update the OS image for your scale set](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-upgrade-scale-set#update-the-os-image-for-your-scale-set))
   - Select the instance you want to upgrade, and then click "Upgrade" to make the modified image take effect in the corresponding VMSS instance
