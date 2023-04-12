# VM Groups

VM Groups are logical groups of Virtual Machines. VM Groups allow VMPower Automate to act on VMs in batches. VM Groups can be associated to a single VM Schedule to perform batch *power on*, *power off*, *backup* and *resize* operations.

VM Groups can:

* Span Across Subscriptions
* Span Across Cloud Providers

## Creating a VM Group

To create a VM Group go to the [Virtual Machines](https://app.vmpower.io/dashboard/virtual-machines) section. Select the cloud subscription your VMs are in and click 'Select VM' on each VM you would like to add to a VM Group. Then click 'Add to VM Group' to either add the VMs to an existing or a new VM Group:

![Create VM Group Demo Gif](https://cdn.vmpower.com/docs/vm-group-demo.gif)

Your new VM Group will be listed in the [VM Groups](https://app.vmpower.io/dashboard/vm-groups) section:

## Modifying a VM Group

You can add more VMs to the VM Group from other cloud subscriptions by going to the [virtual machines section]( https://app.vmpower.io/dashboard/virtual-machines) and clicking 'Select VM' and adding it to the existing VM Group.

To remove a VM from a VM Group, simply press the red 'Remove from VM Group' button within the [VM Groups](https://app.vmpower.io/dashboard/vm-groups) section:

![VM Group screenshot](https://cdn.vmpower.com/docs/vm-group.png)
