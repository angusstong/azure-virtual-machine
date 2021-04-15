# Azure Virtual Machine Scale Set

[Docs - What are virtual machine scale sets?](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview)

## Features and Benefits

- Easily create and manage multiple virtual machine
- All VMs in a scale set are identical with consistent configuration
  - VM size
  - Disk configuration
  - Any software that you install
- Azure Load Balancer is also deployed along with the VMs
- Increase or decrease VMs automatically with auto-scaling
  - Auto scale based on metrics
  - Auto scale based on a defined schedule

## Common Use Cases

- Application demand spikes during specific times of a day
- Launching a new product or a business line
- Application demand cannot be predicted

## Technical Implementation

### High-level Steps

1. Create [Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal) / [Linux](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal) VM as image VM
1. Configure and generalize the VM as an image
1. Create [Shared Image Gallery](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/shared-images-portal) and store the VM image with versioning
1. Create [Virtual Machine Scale Sets](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-portal) and select prepared custom image
1. Configure endpoint with [Load Balancer](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview) or [Application Gateway](https://docs.microsoft.com/en-us/azure/application-gateway/overview) for public access

### References

[Custom VMSS deployment walkthrough](./vmss-walkthrough.md)

[Build automatically-scalable applications with Azure Virtual Machine Scale Sets](https://www.youtube.com/watch?v=TN0b2cMQKAM)

## Pricing

See [Virtual Machine Scale Sets Pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machine-scale-sets/windows/)

You are only charged for the Azure VMs you deploy, as well as any additional underlying infrastructure resources consumed such as storage and networking. There are no incremental charges for the Virtual Machine scale sets service itself. Standard egress charges apply.
