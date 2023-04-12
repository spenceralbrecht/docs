# Auto-off

Auto-off is a feature which allows you to configure VMPower to automatically turn off VMs when their utilization meets certain requirements for a specified amount of time.

## Configuring Auto-off

First, create a [VM Group](/VMPower%20Automate/Vm-Groups) if you already haven't done so. VM Groups organize virtual machines into logical group in VMPower.

Next, go to the [Auto-off](https://app.vmpower.io/dashboard/auto-off) section and select your VM Group from the dropdown list:

![Auto-off Group Select](https://cdn.vmpower.com/docs/auto-off-ss1.png)

### Auto-off Settings

Then you'll see the Auto-off settings you can apply to each VM in the group below:

![Auto-off Group Select](https://cdn.vmpower.com/docs/auto-off-ss2.png)

* **Auto-off After** - The number of hours that each VMs in this group should be 'idle' for before VMPower shuts it off
* **Notify Me** - The number of hours before notifying that at VM in the group will be turning off.
* **Exception Hours** - When enabled, Auto-off will not occur between these hours daily.

### Idle Settings

Configure a set of rules for VMPower to consider VMs in your group as idle. For example, the configuration below instructs VMPower to consider a VM idle if its Max CPU has never exceeded 10%:


![Idle Settings](https://cdn.vmpower.com/docs/auto-off-ss3.png)

Without these settings VMPower may never tag your VMs as idle.

### Auto-off login user rule

You can use the VMPower agent to detect when users login your VMs. With this information, you can set VMs to turn off when a user has not logged for a while. For example, this rule will configure VMs in the group to turn off when no user logs in for 12 hours.

![Idle Settings](https://cdn.vmpower.com/docs/vmpower-auto-off-login-user.png)

### Notifications

When you get an Auto-off warning notification email, VMPower sends a secure one-click link to power off the VM immediatley you can click directly from your email - even if not logged in:

![Auto-off warning email](https://cdn.vmpower.com/docs/auto-off-ss4.png)


When the VM is powered off you can easily start it up with another power-on secure one-click link:

![Auto-off email](https://cdn.vmpower.com/docs/auto-off-ss5.png)


