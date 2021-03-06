# Block Storage

## What is block storage? 

Block storage is an equivalent for most of the existing storage media offered in the physical world.

-   In the physical world, these media are typically mapped by the operating system (Windows, Linux, etc.) to a disk drive (C:, D:).
-   In the world of VMs and servers, they are mapped into two basic types: persistent (drives) and pluggable (thumb drives).

Block services add the concept of ephemeral vs. persistent.

![](https://www.stratoscale.com/wp-content/uploads/block_storage_intro.png)

# Use Cases and Basic Consumption

## Use Cases

-   Boot disks for VMs (Drive “C:” in Windows)
-   Additional Data disks for VMs (All the rest “E:”, “F:”, etc.)

## Basic Consumption

As an end user:

-   You can  [create a disk (volume)](https://www.stratoscale.com/knowledge/creating-a-volume)  at any size you want.
-   You can later  [extend this volume](https://www.stratoscale.com/knowledge/extending-the-size-of-a-volume), if you need more space.
-   You can  [delete the volume](https://www.stratoscale.com/knowledge/deleting-a-volume)  when you do not need it any more.
-   You can move volumes between VMs by  [detaching from](https://www.stratoscale.com/knowledge/detaching-a-volume-from-a-virtual-machine)  and  [attaching to](https://www.stratoscale.com/knowledge/attaching-a-volume-to-a-virtual-machine)  various VMs.

With Symphony, consuming storage is a self-service activity submitted to capacity quotas. This is in contrast to a gory ticketing system where you have to ask an admin to do storage tasks for you, or you have to physically access a server and replace or add disks.

# Using Snapshots

End users can save restoration points of the volumes:

-   Users can delete the snapshots when they are no longer needed.
-   Snapshots can serve as the basis for  data protection.

This allows the users to:

-   Track changes to the VM by snapshotting prior to critical changes.
-   Restore a VM/Volume from a specific time by creating it from a snapshot.

# Cloning and Creating an Image from a Volume

**Clones**: A clone is a volume copied from an existing source volume.

**Create an image from a volume**: You can create an image from any volume. This lets you deploy many VMs out of this volume.

It can be very useful to create a working copy of a virtual machine. This speeds up deployment: prepare once -> use for many.

![](https://www.stratoscale.com/wp-content/uploads/clone.png)

# How Block Storage is Consumed

The user consumes block storage by:

-   CLI
-   GUI
-   API  
    - Symphony’s block API  
    - AWS EBS and EC2 APIs

# Block Storage Summary – Key Points

-   Block storage is equivalent to disks and removable disks.
-   It abstracts away all storage underlay.
-   Consumption is quota based from different classes of storage.

Ephemeral (Instance store) - A volume that is created when a VM starts and deleted when it is powered off – coming soon.

Persistent (EBS volume) - A volume that exists independent of a VM and can be attached to any VM.

# Symphony-supported AWS – EBS APIs and Parameters

Below is a list of the AWS - EBS APIs that Symphony supports, together with their supported Required and Optional request parameters.

Click on the API name to access the complete AWS documentation for that action.

<table class="wrapped confluenceTable"><colgroup><col><col><col></colgroup><tbody><tr><th class="confluenceTh">Name</th><th class="confluenceTh">Required Parameters</th><th class="confluenceTh">Optional Parameters</th></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_AttachVolume.html" rel="nofollow">AttachVolume</a></td><td class="confluenceTd"><ul><li>Device</li><li>InstanceId</li><li>VolumeId</li></ul></td><td class="confluenceTd"></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_CreateSnapshot.html" rel="nofollow">CreateSnapshot</a></td><td class="confluenceTd"><ul><li>VolumeId</li></ul></td><td class="confluenceTd"><ul><li>Description</li><li>TagSpecification</li></ul></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_CreateVolume.html" rel="nofollow">CreateVolume</a></td><td class="confluenceTd"><ul><li>AvailabilityZone</li></ul></td><td class="confluenceTd"><ul><li>Size</li><li>SnapshotId</li><li>TagSpecification</li><li>VolumeType</li></ul></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DeleteSnapshot.html" rel="nofollow">DeleteSnapshot</a></td><td class="confluenceTd"><ul><li>SnapshotId</li></ul></td><td class="confluenceTd"></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DeleteVolume.html" rel="nofollow">DeleteVolume</a></td><td class="confluenceTd"><ul><li>VolumeId</li></ul></td><td class="confluenceTd"></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeSnapshots.html" rel="nofollow">DescribeSnapshots</a></td><td class="confluenceTd"></td><td class="confluenceTd"><ul><li>SnapshotId</li><li>Owner</li><li>Filter</li><li>MaxResults</li></ul></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeVolumes.html" rel="nofollow">DescribeVolumes</a></td><td class="confluenceTd"></td><td class="confluenceTd"><ul><li>VolumeId</li><li>Filter</li><li>MaxResults</li></ul></td></tr><tr><td class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DetachVolume.html" rel="nofollow">DetachVolume</a></td><td class="confluenceTd"><ul><li>VolumeId</li></ul></td><td class="confluenceTd"><ul><li>Device</li><li>InstanceId</li><li>Force</li></ul></td></tr><tr><td colspan="1" class="confluenceTd"><a class="external-link" href="https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ModifyVolume.html" rel="nofollow">ModifyVolume</a></td><td colspan="1" class="confluenceTd"><ul><li>VolumeId</li></ul></td><td colspan="1" class="confluenceTd"><ul><li>Iops</li><li>Size</li><li>VolumeType</li></ul></td></tr></tbody></table>