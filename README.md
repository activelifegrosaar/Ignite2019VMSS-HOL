# Autoscale demo app on RHEL 7.7 with cloud-init

### This demo app was modifed from the Azure Quickstart templates
The original demo app was the Autoscale demo app on Ubuntu 16.04, located [here](https://github.com/Azure/azure-quickstart-templates/tree/master/201-vmss-bottle-autoscale).

### Description
Simple self-contained RHEL autoscale example which includes a Python Bottle server to do work. The VM Scale Set scales up when average CPU across all VMs > 60%, scales down when avg CPU < 30%.

This app provisions a VM scale set using the latest RHEL 7.7 cloud-init enabled image using ARM, and deploys a simple web application to it. You can use the web application to increase the load on your VM scale set instances, which will in turn cause the scale set to automatically scale out more instances.

- Deploy the scale set with an instance count of 1
- After it is deployed look at the resource group public IP address resource (in portal or resources explorer). Get the IP or domain name.
- Browse to the website of vm#0 (port 9000), which shows the current backend VM name.
- To start doing work on the first VM browse to dns:9000/do_work
- After a few minutes the VM Scale Set capacity will increase. Note that the first scale out takes longer than subsequent ones whlie the autoscale pipeline gets initialized (i.e. wait up to half an hour before you concluding there's a problem).
- You can stop doing work by browsing to dns:9000/stop_work.
- To SSH into a VMSS instance, run ssh dns -p 50000