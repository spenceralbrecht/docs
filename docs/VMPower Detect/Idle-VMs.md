# Idle VMs

Idle VMs are VMs identified by VMPower that have *very* low utilization statistics. Typically this means that CPU, network and disk consumption is at a minimal. The only exception is Azure where Disk consumption is typically at least around 300KB/s even for idle VMs.

Below is an example of Idle VMs listed:

![Idle VMs Page](https://cdn.vmpower.com/docs/idle-vms-ss1.png)


You can provide feedback to VMPower if you think VMPower is correct or not about the VM being idle. Clicking on the VM name will take you to the VM Utilization page:

![Idle VMs Page](https://cdn.vmpower.com/docs/idle-vms-ss2.png)

Note that the result of Idle VMs is impacted by any [Auto-off](/VMPower%20Detect/Auto-off) settings the VMs may be under.

