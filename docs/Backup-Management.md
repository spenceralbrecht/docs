# Backup Management

VMPower's backup management provides management of Virtual Machine snapshots for AWS, Azure and Google Cloud Platform.

## Automating Snapshots

You can automate when VMPower takes snapshots of VM disks attached to your VMs by setting up a [VM Schedule](/VMPower%20Automate/Vm-Schedules/) backup events. You can read more about that [here](/VMPower%20Automate/Vm-Schedules/).

## Taking a One-off Snapshot

You can take a one-off snapshot by heading to the [Backups](https://app.vmpowerio/backups/vms) section, select the VMs you want to take snapshots of and click 'Start Backup':

![Backup animation](https://cdn.vmpower.com/docs/one-off-backup.gif)

The snapshot will report as **Pending** until it has completed on your cloud platform. This can be delayed as VMPower polls for the snapshot status at 15 minute intervals.

## Expiring Snapshots

Every backup taken on VMPower can be set with a retention policy which is the number of days a backup should exist before VMPower deletes the backup.

You can modify the expiration of an existing backup by selecting the VM or Volume, going to the snapshot and changing the date:

![Backup retention animation](https://cdn.vmpower.com/docs/backup-retention.gif)

## Restoring Snapshots

You can easily restore volumes from the point-in-time snapshots created by VMPower by simply clicking the Restore Snapshot button:

![Backup restore animation](https://cdn.vmpower.com/docs/backup-restore.gif)

If you check your Unused Volumes section you will see a new VM disk has appeared which is unattached:

![Backup restored disk](https://cdn.vmpower.com/docs/backup-restored-disk.png)

After the disks are restored you can create a new VM with the restored disk on your cloud portal.

## Deleting Snapshots

Snapshots can easily be deleted by clicking the red delete button on a snapshot.

## Azure Backup Management

Azure has two kinds of VM disks, [managed VM disks]() and [unmanaged VM disks](). They are essentially the same physical hardware however managed VM disks are exposed as their own resources. Where as unmanaged VM disks are stored as raw `.vhd` files in your Azure Storage account.

VMPower supports both of these disks and can manage snapshots for both. However the way the snapshots are indexed and stored within azure varies.

### Azure Unmanaged Disks

Azure unmanaged disks are backed up using Azure Storage blob snapshots. These are differential backups and only occupy the space required to record the difference from your VHD file and the last snapshot taken.

You won't be able to see these snapshots in the Azure portal. To find these snapshots in Azure you'll need to download the [Azure Storage Explorer](http://storageexplorer.com) and check the blob for the VHD by right clicking and selecting 'Manage Snapshots':

![Storage Explorer manage snapshots screenshot](https://cdn.vmpower.com/docs/backup-snapshot-unmanaged-1.png)

You'll then see the snapshots VMPower has created:

![Storage Explorer manage snapshots screenshot](https://cdn.vmpower.com/docs/backup-snapshot-unmanaged-2.png)

#### Azure Unmanaged Snapshot IDs:

You can locate a snapshot created by VMPower by examining the VMPower snapshot ID. For example, a snapshot ID for an unmanaged Azure disk looks like:

```
Snapshot ID: vmpower-rg/vmpower/vhds/DokkuVM-20160623-123810.vhd-2017-05-25T18:37:50.7350991Z-unmanaged
```

The VMPower Snapshot ID is made up of key information on how to find this snapshot in Azure. From left to right here i

```
Resource Group: vmpower-rg
Storage Account Name: vmpower
Storage Account Container: vhds
Blob Name: DokkuVM-20160623-123810.vhd
Azure Storage Snapshot ID: 2017-05-25T18:37:50.7350991Z
Managed Snapshot Indicator: unmanaged
```

You can use this information to confirm the snapshot exists.

#### Azure Unmanaged Snapshot Restore

Unmanaged snapshots are restored by creating a **new** VHD blob in the same container with the timestamp appended to the name. You will see this disk appear both in the VMPower dashboard and the Azure portal as a new `.vhd` blob.

### Azure Managed Disks

Azure managed disks are backed up using Azure Managed Snapshots. These are full-copy backups and do occupy the space of the original disk size. The cost of the snapshot space is charged at standard storage rates, even for premium disks.

These snapshots are much easier to find and manage than unmanaged snapshots.

When VMPower creates a snapshot, snapshots will appear in a resource group titled `_vmpower-backups-<region>` where `<region>` is the region is the Azure data center region for the snapshot:

[Azure Managed Snapshot RG](https://cdn.vmpower.com/docs/backup-resource-group.png)

Within this resource group, all VM disk snapshots are stored:

[Azure Managed Snapshot RG](https://cdn.vmpower.com/docs/backup-azure-snapshots.png)

It is important to note that you should avoid directly managing these snapshots as they are indexed inside VMPower.

## AWS Backup Management

VMPower backup management generates standard AWS EBS snapshots. These snapshots are point-in-time snapshots of your EBS disks and occupy only the amount of space required to store the changes in the VM disk since the last backup. You can restore these snapshots directly though the VMPower dashboard to create a new VM on the AWS Console.

## Google Cloud Backup Management

VMPower backup management generates standard Google Cloud snapshots. These snapshots are point-in-time snapshots of your EBS disks and occupy only the amount of space required to store the changes in the VM disk since the last backup. You can restore these snapshots directly though the VMPower dashboard to create a new VM on the Google Cloud Engine dashboard.


