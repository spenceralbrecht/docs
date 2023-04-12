# VM Schedules

VM Schedules are *weekly schedules* that can execute an arbitrary, repeating set of automations events on your [VM Group](/VMPower%20Automate/VM-Groups).

## Creating a Schedule

To create a VM Schedule first go to the [VM Group](https://app.vmpower.io/dashboard/vm-groups) and click the icon that says 'Edit or Create VM Schedule' for the VM Group you wish to automate.

![Edit or create schedule button](https://cdn.vmpower.com/docs/edit-create-vm-schedule.png)

## Building Your Schedule

Build your schedule by clicking on the calendar to drop events. Click the event again to change the event type:

![Event create demo gif](https://cdn.vmpower.com/docs/event-create-demo.gif)

## Event Kinds

VM Schedules support multiple kinds of batch automations.

### Power On & Power Off

These events do exactly what they sound like. VMPower will stop & deallocate VMs at the beginning of the event timespan and send a notification.

### Resize

These events can vertically scale (resize) the VMs in the group to a selected target size available for each VM and their corresponding data center. When you select a resize event, you will be presented with the Resize selector which lists the available target VM sizes for each VM:

![Schedule resize modal](https://cdn.vmpower.com/docs/schedule-resize-modal.png)

If a VM is running before a resize event starts, VMPower will shutdown the VM, resize the VM and start it again. It isn't necessary to place a power-off event before a resize event or a power-on event after a resize event.

### Backup

These events can backup all the disks currently attached to each VM at the time of automation. A backup is a snapshot of all the volumes attached to a VM. When you select a backup event, you will have the chance to set the retention of the backups created. This is the number of days VMPower should hold on to backups before deleting them:

![Backup modal](https://cdn.vmpower.com/docs/backup-modal.png)

You can learn more about VMPower Backup management [here](/VMPower%20Automate/Backup%20Management).

## Event Based Scheduling

Each VM Schedule events happens exactly once per week. So if you set a Power Off event to trigger at 6PM and a Power On event to trigger at 6AM the next day, your VM will be off approximately between 6PM to 6AM the next day, unless you or someone else turns the VM on.

## Logged in users

If your VM has the VMPower agent, you can skip an automation action there is an active SSH or RDP session. Do this by checking the box "Skip action for VMs with active RDP/SSH" when creating the action.

![VMPower schedule login user toggle](https://cdn.vmpower.com/docs/vmpower-schedule-login-user.png)

You'll see a person icon on the scheduled event which indicates this action will skip for VMs with active RDP/SSH sessions.


![VMPower scheduled event that skips login user](https://cdn.vmpower.com/docs/vmpower-schedule-login-user-2.png)


## Why isn’t My Schedule Executing?

### Check that You Have VMs in Your VM Group

Your schedule is associated with a [VM Group](https://app.vmpower.io/dashboard/vm-groups) and it is possible that your VM Group is empty. This can happen after a trial expiration where VMs that do not qualify for a free plan are removed from VM Groups.

### Check that Your Schedule is Enabled

This might sound simple but your schedule may simply be disabled. Make sure the 'Enabled' switch is ON.

### Your VMs May Already be in the Desired State

If you have a POWER OFF event and your VMs are currently OFF, VMPower won't modify the VM. Same goes for a RESIZE event where a VM is in its target state.

### Contact Us

If you've checked all the above and your VMs are still not automating, [contact us](mailto:support@vmpower.io).
