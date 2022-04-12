# Essential Google Cloud Infrastructure Foundation

# Week 1

## Using Google Cloud

### Four ways to interact with GCP

- GCP Console (Web)
- Cloud Shell(CLI) ad Cloud SDK
- REST API
- Cloud Mobile App

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled.png)

### VPC Objects

- VPC is a comprehensive set of Google managed networking objects
- VPC Objects
    - Projects
    - Networks
        - Default mode
        - Auto mode
        - Custom mode
    - Subnetworks
    - Regions
    - Zones
    - IP addresses
        - Internal,
        - External
        - Range
    - Virtual machines (VM’s)
    - Routes
    - Firewall rules

### Projects, Networks and Subnetworks

- **Projects**
    - Associates objects and services with billing
    - Contains networks (max 5) that can be shared/peered.
- **Networks**
    - Has no range and is global
    - Spans all regions
    - Contains subnetworks
    - Available as default, auto or custom
- 3 VPC Network Types
    - Default
        - Every project
        - One subnet per region
        - Default firewall rules
    - Automode
        - Default network
        - One subnet per region
        - Regional IP allocation
        - Fixed /20 subnetwork per region
        - Expandable up to /16
    - Custom Mode
        - No default subnets created
        - Full control of IP ranges
        - Regional IP allocation
        - Expandable to IP ranges you specify.
        
        ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%201.png)
        
        ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%202.png)
        
- Expand subnets without recreating instances
    - Cannot overlap with other subnets
    - IP Range must be unique with valid CIDR block
    - New subnet IP ranges have to fall within valid IP ranges
    - Can expand but not shrink
    - Auto mode can be expanded from /20 to /16
    - Avoid large subnets
    
    ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%203.png)
    
- External IPs are mapped to internal IP’s
- DNS Resolution for internal addresses
    - Each instance has a hostname that can be resolved to a internal IP address
        - Host name is same as instance name
        - FQDN is [hostname].[zone].c.[project-id].internal
    - Name Resolution is handled by interal DNS resolver
        - Provided as part of Compute Engine
        - Configured for use on instance via DHCP
        - Provides answer for internal and external addresses.
- Host DNS Zones using Cloud DNS
    - Google DNS Service
    - Translate domain names into IP address
    - Low latency
    - High availablity
    - Create and update millions of DNS records
    - UI command line or API
    
    ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%204.png)
    

### Routes and Firewall Rules

[VPC firewall rules overview | Google Cloud](https://cloud.google.com/vpc/docs/firewalls#firewall_rule_components)

- A route is a mapping of IP range to a destination
- Every network has
    - Routes that let instances in a network send traffic directly to each other
    - A default route that directs packets to destinations that are outside the network
    - Firewall rules must also allow the packet
- Routes map traffic to destination networks~
    
    ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%205.png)
    
    - Each route in the routes collection may apply to one or more instances. A route applies to an instance if the network and instance tags match. If the network matches and there are no instance tags specified, the route applies to all instances in that network.
    - Compute Engine then uses the routes collection to create individual read-only routing tables for each instance. This diagram shows a massively scalable virtual router at the core of each network
    - //Bullet this para → Every virtual machine instance in the network is directly connected to this router, and all packets leaving a virtual machine instance, are first handled at this layer, before they are forwarded to the next top. The virtual network router selects the next stop for a packet by consulting the routing table for that instance.GCP firewall rules protect your virtual machine instances from unapproved connections both inbound and outbound known as ingress and egress respectively. Essentially, every VPC network functions as a distributed firewall. Although firewall rules are applied to the network as a whole, connections are allowed or denied at the instance level. You can think of the firewall as existing not only between your instances and other networks, but between individual instances within the same network. GCP firewall rules are stateful. This means that if a connection is allowed between a source and a target or a targeted at destination, all subsequent traffic in either direction will be allowed. In other words, firewall rules allow bidirectional communication once a session is established. Also, if for some reason all firewall rules in a network are deleted, there's still an implied deny all ingress rule and an implied allow all egress rule for the network. You can express your desired firewall configuration as a set of firewall rules. Conceptually, a firewall rule is composed of the following parameters. The direction of the rule, inbound connections are matched against ingress rules only, and up on connections are matched against egress rules only. The source of the connection for ingress packets or D destination of the connection for egress packets, the protocol and port of the connection where any rule can be restricted to apply to specific protocols only or specific combinations of protocols and ports only. The action of the rule which is to allow or deny packets that match the direction, protocol, port, and source or destination of the rule. The priority of the rule which governs the order in which rules are evaluated; the first matching rule is applied. The rule assignment. By default all rules are assigned to all instances, but you can assign certain rules to certain instances only. For more information on firewall rule components, please refer to the links section of this video. Let's look at some GCP firewall overall use cases for both egress and ingress. Egress firewall rules control outgoing connections originated inside your GCP network. Egress allow rules, allow outbound connections that match the civic protocol ports and IP addresses. Egress deny rules prevent instances from initiating connections that match non permitted port protocol in the IP range combinations. For egress firewall rules, destinations to which a rule applies maybe specified using IP CIDR ranges. Specifically, you can use the destination ranges to protect from undesired connections initiated by a VM instance towards an external host as shown on the left. You can also use destination ranges to prevent undesired connections, some internal VM instances to specific GCP CIDR ranges. This is illustrated in the middle where VM in a specific subnet is shown attempting to connect inappropriately to another VM within the same network. Ingress firewall rules protect against incoming connections to the instance from any source. Ingress allow rules, allow specific protocol ports and IP ranges to connect in. The firewall prevents instances from receiving connections on non permitted ports and protocols. Rules can be restricted to only affect particular sources. Source CIDR ranges can be used to protect an instance from undesired connections coming either from external networks or from GCP IP ranges. This diagram illustrates a VM receiving a connection from an external address and another VM receiving a connection from a VM within the same network. You can control ingress connections from a VM instance by constructing inbound connection conditions using source CIDR ranges, protocols, or ports
    
    ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%206.png)
    

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%207.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%208.png)

- **Pricing**
    - [https://cloud.google.com/compute/all-pricing#general_network_pricing](https://cloud.google.com/compute/all-pricing#general_network_pricing)
    - [https://cloud.google.com/products/calculator/](https://cloud.google.com/products/calculator/)
- Common Network Designs and Private Google Access

## Week 2

### Compute Engine(Creating VM’s)

![Screenshot 2022-03-25 at 4.15.17 PM.png](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Screenshot_2022-03-25_at_4.15.17_PM.png)

- Infrastructure as a Service
- Predefined or custom machine types
    - vCPUS(cores) and memory(RAM)
    - Storage
        - Zonal or regional persistent disk
        - Local SSD
        - Cloud storage
    - Networking
    - Linux or windows
        
        ![Screenshot 2022-03-25 at 4.16.48 PM.png](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Screenshot_2022-03-25_at_4.16.48_PM.png)
        
- Compute
    - Several Machine Types
        - Networks scales through 2Gbps per vCPU
        - Theoretical max of 32Gbps with 16vCPU or 100Gbps with T4 or V100 GPU’s
    - A vCPU is equal to 1 Hardware hyper thread
- Storage
    - Disks
        - Standard, SSD or Local SSD
        - Standard and SSD PD scale in performance for each GB of allocated space
    - Resize disks or migrate instances with no downtime
- Netoworking
    - Robust Networking features
        - Default, custom networks
        - Inbound/Outbound firewall rules
            - IP Based
            - Instance/group tags
        - Regional HTTPS load balancing
        - Network Load Balancing
            - Does not require pre-warning
        - Global and multi-regional subnetworks

### VM Access and Lifecycle

**VM Access**

| Linux:SSH | Windows: RDP |
| --- | --- |
| SSH from Cloud Console or Cloudshell via CloudSDK | RDP Clients |
| SSH from computer or third party client and geenrate key pair | Power shell terminal |
| Requires firewall rule to allow tcp:22 | Requires setting the windows password |
|  | Requires the firewall rule to allow tcp:3389 |

![Screenshot 2022-03-25 at 4.29.44 PM.png](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Screenshot_2022-03-25_at_4.29.44_PM.png)

The lifecycle of a VM is represented by different statuses. We will cover this lifecycle
on a high level, but we recommend returning to this diagram as a reference.
When you define all the properties of an instance and click Create, the instance
enters the provisioning state. Here the resources such as CPU, memory, and disks
are being reserved for the instance, but the instance itself isn’t running yet. Next, the
instance moves to the staging state where resources have been acquired and the
instance is prepared for launch. Specifically, in this state, Compute Engine is adding
IP addresses, booting up the system image, and booting up the system.
After the instance starts running, it will go through pre-configured startup scripts and
enable SSH or RDP access. Now, you can do several things while your instance is
running. For example, you can live migrate your virtual machine to another host in the
same zone instead of requiring your instance to be rebooted. This allows Google
Cloud to perform maintenance that is integral to keeping the infrastructure protected
and reliable, without interrupting any of your VMs. While your instance is running, you
can also move your VM to a different zone, take a snapshot of the VM’s persistent
disk, export the system image, or reconfigure metadata. We will explore some of
these tasks in later labs.
Some actions require you to stop your virtual machine; for example, if you want to upgrade your machine by adding more CPU. When the instance enters this state, it
will go through pre-configured shutdown scripts and end in the terminated state. From
this state, you can choose to either restart the instance, which would bring it back to
its provisioning state, or delete it.
You also have the option to reset a VM, which is similar to pressing the reset button
on your computer. This actions wipes the memory contents of the machine and resets
the virtual machine to its initial state. The instance remains in the running state
through the reset.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%209.png)

There are different ways you can change a VM state from running. Some methods
involve the Cloud Console and the gcloud command, while others are performed from
the OS, such as for reboot and shutdown.
It’s important to know that if you are restarting, rebooting, stopping, or even deleting
an instance, the shutdown process will take about 90 sec. For a preemptible VM, if
the instance does not stop after 30 seconds, Compute Engine sends an ACPI G3
Mechanical Off signal to the operating system. Remember that when writing shutdown
scripts for preemptible VMs.

**Availability Policy: Automatic Changes**

- Called "scheduling options" in SDK/API
    - Automatic restart
        - Automatic VM restart due to crash or maintenance event
            - Not preemption or a user-initiated terminate
    - On host maintenance
        - Determines whether host is live-migrated or terminated due to a maintenance event.
        Live migration is the default.
    - Live migration
        - During maintenance event, VM is migrated to different hardware without interruption.
        - Metadata indicates occurrence of live migration.

---

### Patch Management

Patch management is an essential part of managing an infrastructure

The OS patch management service has two main components:

- Patch compliance reporting, which provides insights on the patch status of
your VM instances across Windows and Linux distributions. Along with the
insights, you can also view recommendations for your VM instances.
- Patch deployment, which automates the operating system and software patch
update process. A patch deployment schedules patch jobs. A patch job runs
across VM instances and applies patches.
- There are several tasks that can be performed with patch management.
    - Create patch approvals.
    - Set up flexible scheduling.
    - Apply advanced patch configuration settings.
    - Manage these patch jobs or updates from a centralized location.
    - And you can manage these patch jobs or updates from a centralized location.
- When a VM is terminated, you do not pay for memory and CPU resources. However, you are charged for any attached disks and reserved IP addresses. In the terminated state, you can perform any of the actions listed here, such as changing the machine type, but you cannot change the image of a stopped VM. Also, not all of the actions listed here require you to stop a virtual machine. For example, VM availability policies can be changed while the VM is running, as discussed previously.

---

## Working With VM’s

### Compute Options

- Three options for creating a VM
    - Console
    - Shell
    - REST API
- Machine Type Structure
    - Machine Family → Machine Series → Machine Type
- Machine Families
    - General Purpose
    - Compute Optimized
    - Memory Optimized
    - Accelerator Optimized
- Machine Types
    - Predefined machine types: Ratio of GB of memory per vCPU
        - Standard
            - Standard machine types are suitable for tasks that have a balance of CPU and memory needs. Standard machine types have 3.75 GB of memory per vCPU. The vCPU configurations come in different intervals from 1 vCPU all the way to 96 vCPUs, as shown on this table. Each of these machines supports a maximum of 128 persistent disks with a total persistent disk size of 257 TB, which is also the case for the High-memory, High-CPU, Memory-optimized, and Compute-optimized machine types.
            
            ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2010.png)
            
        - High-memory
            - High-memory machine types are ideal for tasks that require more memory relative to vCPUs. High-memory machine types have 6.50 GB of system memory per vCPU. Similarly to the standard machine types, the vCPU configurations come in different intervals from 2 vCPUs all the way to 96 vCPUs, as shown on this table.
            
            ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2011.png)
            
        - High-CPU
            - High-CPU machine types are ideal for tasks that require more vCPUs relative to memory. High-CPU machine types have 0.90 GB of memory per vCPU.
            
            ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2012.png)
            
        - Memory-optimized
            - Memory-optimized machine types are ideal for tasks that require intensive use of memory, with higher memory to vCPU ratios than high-memory machine types. These machines types are perfectly suited for in-memory databases and in-memory analytics, such as SAP HANA and business warehousing workloads, genomics analysis, and SQL analysis services. Memory-optimized machine types have more than 14 GB of memory per vCPU. These machine come in 4 configurations as shown in this table, with only the m1-megamem-96 currently supporting a local SSD.
            
            ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2013.png)
            
        - Compute-optimized
            - Compute-optimized machine types are ideal for compute-intensive workloads. These machine types offer the highest performance per core on Compute Engine. Built on the latest-generation Intel Scalable Processors (the Cascade Lake), C2 machine types offer up to 3.8 Ghz sustained all-core turbo and provide full transparency into the architecture of the underlying server platforms, enabling advanced performance tuning. C2 machine types offer much more computing power, run on a newer platform, and are generally more robust for compute-intensive workloads than the N1 high-CPU machine types.
            
            ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2014.png)
            
        - Shared-Core
            - Shared-core machine types provide one vCPU that is allowed to run for a portion of the time on a single hardware hyper-thread on the host CPU running your instance. Shared-core instances can be more cost-effective for running small, non-resource-intensive applications than other machine types. There are only two shared-core machine types to choose from:
                - f1-micro
                - g1-small
            - f1-micro machine types offer bursting capabilities that allow instances to use additional physical CPU for short periods of time. Bursting happens automatically when your instance requires more physical CPU than originally allocated. During these spikes, your instance will opportunistically take advantage of available physical CPU in bursts. Note that bursts are not permanent and are only possible periodically.
            
            ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2015.png)
            
    - Custom Machine Types: You specify the amount of memory and number of CPU’s
        - If none of the predefined machine types match your needs, you can independently specify the number of vCPUs and the amount of memory for your instance. Custom machine types are ideal for the following scenarios:
            - When you have workloads that are not a good fit for the predefined machine types that are available to you.
            - Or when you have workloads that require more processing power or more memory, but don't need all of the upgrades that are provided by the next larger predefined machine type.
        - It costs slightly more to use a custom machine type than an equivalent predefined machine type, and there are still some limitations in the amount of memory and vCPUs you can select:
            - Only machine types with 1 vCPU or an even number of vCPUs can be created.
            - Memory must be between 0.9 GB and 6.5 GB per vCPU (by default).
            - The total memory of the instance must be a multiple of 256 MB.
        - By default, a custom machine can have up to 6.5 GB of memory per vCPU. However, this might not be enough memory for your workload. At an additional cost, you can get more memory per vCPU beyond the 6.5 GB limit. This is referred to as extended memory, and you can learn more about this in the links section of this video
- Choosing Region and Zone
    - The first thing you want to consider when choosing a region and zone is the geographical location in which you want to run your resources. This map shows the current and planned GCP regions and number of zones. For up-to-date information on the available regions and zones, see the documentation linked for this video.
    - Each zone supports a combination of Ivy Bridge, Sandy Bridge, Haswell, Broadwell, and Skylake platforms. When you create an instance in the zone, your instance will use the default processor supported in that zone. For example, if you create an instance in the us-central1-a zone, your instance will use a Sandy Bridge processor.

### Compute Pricing

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2016.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2017.png)

### Special Compute Configurations

**Preemptible VM’s**

- Lower price for interruptible service (up to 80%)
- VM might be terminated at any time
    - No charge if terminated in the first minute
    - 24 hours max
    - 30-second terminate warning, but not guaranteed
        - Time for a shutdown script
- No live migrate; no auto restart
- You can request that CPU quota for a region be split between regular and preemption
    - Default: preemptible VMs count against region CPU quota
    
    ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2018.png)
    

**Sole Tenant Nodes**

- If you have workloads that require physical isolation from other workloads or virtual machines in order to meet compliance requirements, you want to consider sole-tenant nodes.
- A sole-tenant node is a physical Compute Engine server that is dedicated to hosting VM instances only for your specific project. Use sole-tenant nodes to keep your instances physically separated from instances in other projects, or to group your instances together on the same host hardware, for example if you have a payment processing workload that needs to be isolated to meet compliance requirements.
- The diagram on the left shows a normal host with multiple VM instances from multiple customers. A sole tenant node as shown on the right also has multiple VM instances, but they all belong to the same project. As of this recording, the only available node type can accommodate VM instances up to 96 vCPUs and 624 GB of memory. You can also fill the node with multiple smaller VM instances of various sizes, including custom machine types and instances with extended memory. Also, if you have existing operating system licenses, you can bring them to Compute Engine using sole-tenant nodes while minimizing physical core usage with the in-place restart feature

**Shielded VM’s**

- Another compute option is to create shielded VMs. Shielded VMs offer verifiable integrity of your VM instances, so you can be confident that your instances haven't been compromised by boot- or kernel-level malware or rootkits. Shielded VM's verifiable integrity is achieved through the use of Secure Boot, virtual trusted platform module or vTPM-enabled Measured Boot, and integrity monitoring.
- Shielded VMs is the first offering in the Shielded Cloud initiative. The Shielded Cloud initiative is meant to provide an even more secure foundation for all of Google Cloud by providing verifiable integrity and offering features, like vTPM shielding or sealing, that help prevent data exfiltration.

**Confidential VM’s**

- Encrypts data while it’s being processed.
- Easy to use with no changes to code or performance compromise.
- N2D Compute Engine VM running on second generation AMD Epyc processors.
- Provides high memory capacity, high throughput, and supports parallel and compute heavy workloads.
- You can select Confidential VM service when creating a new VM.

---

### Image

**What is an image? Images include all the below things**

- Bootloader
- OS
- File System Structure
- Software
- Customizations

**Types of Images**

- Public base images
    - Google, third-party vendors, and community; Premium images (p)
    - Linux
        - CentOS, CoreOS, Debian, RHEL(p), SUSE(p), Ubuntu, openSUSE, and FreeBSD
    - Windows
        - Windows Server 2019(p), 2016(p), 2012-r2(p)
        - SQL Server pre-installed on Windows(p)
- Custom images
    - Create new image from VM: pre-configured and installed SW
    - Import from on-prem, workstation, or another cloud
    - Management features: image sharing, image family, deprecation

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2019.png)

### Disks

**Boot Disks**

- VM comes with a single root persistent disk.
- Image is loaded onto root disk during first boot:
    - Bootable: you can attach to a VM and boot from it.
    - Durable: can survive VM terminate.
- Some OS images are customized for Compute Engine.
- Can survive VM deletion if “Delete boot disk when instance is deleted” is disabled.

**Types of Disks** 

- **Persistent Disks**
    
    The first disk that we create is what we call a persistent disk. That means it's going to be attached to the VM through the network interface. Even though it's persistent, it's not physically attached to the machine. This separation of disk and compute allows the disk to survive if the VM terminates. You can also perform snapshots of these disks, which are incremental backups that we’ll discuss later.
    
    - Network storage appearing as a block device
    - Attached to a VM through the network interface
    - Durable storage: can survive VM terminate
    - Bootable: you can attach to a VM and boot from it
    - Snapshots: incremental backups
    - Performance: Scales with size
    - HDD (magnetic) or SSD (faster, solid-state) options
    - Disk resizing: even running and attached!
    - Can be attached in read-only mode to multiple VMs
        - You can also attach a disk in read-only mode to multiple VMs. This allows you to share static data between multiple instances, which is cheaper than replicating your data to unique disks for individual instance
    - Zonal or Regional
        - Zonal persistent disks offer efficient, reliable block storage. Regional persistent disks provide active-active disk replication across two zones in the same region. Regional persistent disks deliver durable storage that is synchronously replicated across zones and are a great option for high-performance databases and enterprise applications  that also require high availability. When you configure a zonal or regional persistent disk, you can select one of the following disk types.
            - pd-standard
            - pd-ssd
            - pd-balanced
            - pd-extreme (zonal only)
    - Encryption keys:
        - Google-managed
        - Customer-managed
        - Customer-supplied
- **Local SSD disks are physically attached to a VM**
    - Now, local SSDs are different from persistent disks in that they are physically attached to the virtual machine. Therefore, these disks are ephemeral but provide very high IOPS. For up-to-date numbers I recommend referring to the documentation [[https://cloud.google.com/compute/docs/disks/performance](https://cloud.google.com/compute/docs/disks/performance)].
    - Currently, you can attach up to 8 local SSD disks with 375 GB each, resulting in a total of 3 TB.
    - Data on these disks will survive a reset but not a VM stop or terminate, because these disks can’t be reattached to a different VM.
- **RAM Disk**
    - tmpfs
    - Faster than local disk, slower than memory
        - Use when your application expects a file system structure and cannot directly store its data in memory
        - Fast scratch disk, or fast cache
    - Very volatile; erase on stop or restart
    - May need a larger machine type if RAM was sized for the application
    - Consider using a persistent disk to back up RAM disk data

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2020.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2021.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2022.png)

### Common Compute Engine actions

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2023.png)

- Every VM instance stores its metadata on a metadata server. The metadata server is particularly useful in combination with startup and shutdown scripts, because you can use the metadata server to programmatically get unique information about an instance, without additional authorization. For example, you can write a startup script that gets the metadata key/value pair for an instance's external IP address and use that IP address in your script to set up a database. Because the default metadata keys are the same on every instance, you can reuse your script without having to update it for each instance. This helps you create less brittle code for your applications.
- Storing and retrieving instance metadata is a very common Compute Engine action. I recommend storing the startup and shutdown scripts in Cloud Storage, as you will explore in the upcoming lab of this module.

**Moving Instances to a New Zone**

- Automated process (moving within region):
    - gcloud compute instances move
    - Update references to VM; not automatic
- Manual process (moving between regions):
    - Snapshot all persistent disks on the source VM.
    - Create new persistent disks in destination zone restored from snapshots.
    - Create new VM in the destination zone and attach new persistent disks.
    - Assign static IP to new VM.
    - Update references to VM.
    - Delete the snapshots, original disks, and original VM.

**Snapshot: Backup Critical Data**

- Snapshots have many use cases. For example, they can be used to backup critical data into a durable storage solution to meet application, availability, and recovery requirements. These snapshots are stored in Cloud Storage, which is covered later.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2024.png)

- Snapshots can also be used to migrate data between zones. I just discussed this when going over the manual process of moving an instance between two regions, but this can also be used to simply transfer data from one zone to another. For example, you might want to minimize latency by migrating data to a drive that can be locally attached in the zone where it is used.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2025.png)

- another snapshot use case of transferring data to a different disk type. For example, if you want to improve disk performance, you could use a snapshot to transfer data from a standard HDD persistent disk to a SSD persistent disk.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Foundation%20Attachments/Untitled%2026.png)

**Persistent Disk Snapshots**

- Snapshot is not available for local SSD.
- Creates an incremental backup to Cloud Storage.
    - Not visible in your buckets; managed by the snapshot service.
    - Consider cron jobs for periodic incremental backup.
- Snapshots can be restored to a new persistent disk.
    - New disk can be in another region or zone in the same project.
    - Basis of VM migration: "moving" a VM to a new zone.
        - Snapshot doesn't back up VM metadata, tags, etc.

**Resize Persistent disk**

Another common Compute Engine action is to resize your persistent disk. The added benefit of increasing storage capacity is to improve I/O performance. This can be achieved while the disk is attached to a running VM without having to create a snapshot. Now, while you can grow disks in size, you can never shrink them, so keep this in mind.