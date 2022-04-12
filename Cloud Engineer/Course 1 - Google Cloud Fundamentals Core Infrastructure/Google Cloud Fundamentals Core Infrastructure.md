# Google Cloud Fundamentals: Core Infrastructure

# Week 1 - Introducing GCP

## GCP Fundamentals

- GCP offers four main kinds of services: compute, storage, big data and machine learning.
- What is cloud computing?
    - On-demand service - No human intervention
    - Broad network access - Access from anywhere
    - Resource Pooling - Provide shared resources to customers
    - Rapid elasticity - Get more resources if quickly needed
    - Measured Service - Pay only for what you consume

- The first wave of the trend towards cloud computing was colocation. Colocation gave users the financial efficiency of renting physical space, instead of investing in data center real estate.
- Virtualized data centers of today, the second wave, share similarities with the private data centers and colocation facilities of decades past. The components of virtualized data centers match the physical building blocks of hosted computing—servers, CPUs, disks, load balancers, and so on—but now they are virtual devices. Virtualization does provide a number of benefits: your development teams can move faster, and you can turn capital expenses into operating expenses. With virtualization you still maintain the infrastructure; it is still a user-controlled/user-configured environment.
- About 10 years ago, Google realized that its business couldn’t move fast enough within the confines of the virtualization model. So Google switched to a container-based architecture—a fully automated, elastic third-wave cloud that consists of a combination of automated services and scalable data. Services automatically provision and configure the infrastructure used to run applications. Today Google Cloud Platform makes this third-wave cloud available to Google customers.

### How did we get here?

- Google believes that in the future every company, regardless of size or industry, will differentiate itself from its competitors through technology largely in the form of software, great software centered on data
- GCP Computing Architectures
    - IAAS - Infrastructure as a Service
        - IaaS offerings provide raw compute, storage, and network organized in ways that are familiar from data centers.
        - In the IaaS model, you pay for what you allocate.
    - PAAS - Platform as a Service
        - PaaS offerings, on the other hand, bind application code you write to libraries that give access to the infrastructure your application needs. That way, you can just focus on your application logic.
        - In the PaaS model, you pay for what you use.
    - SaaS - Software as a service
        - Google's popular applications like, Search, Gmail, Docs and Drive are Software as a Service applications in that they're consumed directly over the internet by end users.
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled.png)
        

### Google's Network

- Google's network carries as much as 40 percent of the world's Internet traffic every day.
- Google's network is the largest of its kind on earth and the company has invested billions of dollars over the years to build it
- The network interconnects at more than 90 Internet exchanges and more than 100 points of presence worldwide. When an Internet user sends traffic to a Google resource, Google responds to the user's request from an edge network location that will provide the lowest latency. Google's Edge-caching network sites content close to end users to minimize latency.

### Region and Zones

- A zone is a deployment area for Google Cloud Platform Resources.
    - For example, when you launch a virtual machine in GCP using Compute Engine, which we'll discuss later, it runs in a zone you specify.
- Although people think of a zone as being like a GCP Data Center, that's not strictly accurate because a zone doesn't always correspond to a single physical building.
- Zones are grouped into regions, independent geographic areas, and you can choose what regions your GCP resources are in. All the zones within a region have fast network connectivity among them.
- Locations within regions usually have round trip network latencies of under five milliseconds. Think of a zone as a single failure domain within a region.
- As part of building a fault tolerant application, you can spread their resources across multiple zones in a region. That helps protect against unexpected failures. You can run resources in different regions too.
- Lots of GCP customers do that, both to bring their applications closer to users around the world, and also to protect against the loss of an entire region, say, due to a natural disaster. A few Google Cloud Platform Services support placing resources in what we call a Multi-Region.
- As of last year google(2020) had 17 regions.
- The following services have one or more multi-regional deployments in addition to any regional deployments:
    - Google App Engine and its features
    - Google Cloud Datastore
    - Google Cloud Storage
    - Google BigQuery

### Environmental Responsibility

- all existing data centers use roughly two percent of the world's electricity, so Google works to make data centers run as efficiently as possible. Google's data centers were the first to achieve ISO 14001 certification, which is a standard that maps out a framework for improving resource efficiency and reducing waste
- Google's data center in Hamina, Finland, one of the most advanced and efficient data centers in the Google fleet. Its cooling system uses seawater from the bay of Finland to reduce energy use. It's the first of its kind anywhere in the world.
- Google is one of the world's largest corporate purchasers of wind and solar energy. Google has been a hundred percent carbon neutral since 2007, and will shortly reach a hundred percent renewable energy sources for its data centers.
- Just like its customers, Google is trying to do the right things for the planet. GCP customers have environmental goals of their own, and running their workloads in GCP can be a part of meeting them.

### Friendly Pricing

- Google was the first major cloud provider to deliver per-second billing for its Infrastructure-as-a-Service compute offering, Google Compute Engine. Per-second billing is offered for users of Compute Engine, Kubernetes Engine (container infrastructure as a service), Cloud Dataproc (the open-source Big Data system Hadoop as a service), and App Engine flexible environment VMs (a Platform as a Service).
- Google Compute Engine offers automatically applied sustained-use discounts, which are automatic discounts that you get for running a virtual-machine instance for a significant portion of the billing month. Specifically, when you run an instance for more than 25% of a month, Compute Engine automatically gives you a discount for every incremental minute you use for that instance.
- Custom virtual machine types allow Google Compute Engine virtual machines to be fine-tuned for their applications, so that you can tailor your pricing for your workloads.

### Open API's

- Google gives customers the ability to run their applications elsewhere if Google becomes no longer the best provider for their needs.]
- Using Open APIs. Google services are compatible with open-source products. For example, Google Cloud Bigtable, a horizontally scalable managed database: Bigtable uses the Apache HBase interface, which gives customers the benefit of code portability. Another example: Google Cloud Dataproc offers the open-source big data environment Hadoop as a managed service.
- Google publishes key elements of its technology, using open-source licenses, to create ecosystems that provide customers with options other than Google. For example, TensorFlow, an open-source software library for machine learning developed inside Google, is at the heart of a strong open-source ecosystem.
- Google provides interoperability at multiple layers of the stack. Kubernetes and Google Kubernetes Engine give customers the ability to mix and match microservices running across different clouds. Google Stackdriver lets customers monitor workloads across multiple cloud providers.

### Why choose GCP?

- Google Cloud Platform's products and services can be broadly categorized as compute, storage, big data, machine learning, networking and operations and tools.
- Google Cloud Platform enables developers to build, test, and deploy applications on Google’s highly secure, reliable, and scalable infrastructure

### Security Features

- Both the server boards and the networking equipment in Google data centers are custom designed by Google. Google also designs custom chips, including a hardware security chip called Titan that's currently being deployed on both servers and peripherals. Google server machines use cryptographic signatures to make sure they are booting the correct software. Google designs and builds its own data centers which incorporate multiple layers of physical security protections. Access to these data centers is limited to only a very small fraction of Google employees, not including me.
- Google's infrastructure provides cryptographic privacy and integrity for remote procedure called data-on-the-network, which is how Google services communicate with each other. The infrastructure automatically encrypts our PC traffic in transit between data centers. Google Central Identity Service, which usually manifests to end users as the Google log-in page, goes beyond asking for a simple username and password.
- It also intelligently challenges users for additional information based on risk factors such as whether they have logged in from the same device or a similar location in the past. Users can also use second factors when signing in, including devices based on the universal second factor U2F open standard.
- Most applications at Google access physical storage indirectly via storage services and encryption is built into those services. Google also enables hardware encryption support in hard drives and SSDs. That's how Google achieves encryption at rest of customer data.
- Google services that want to make themselves available on the Internet register themselves with an infrastructure service called the Google Front End, which checks incoming network connections for correct certificates and best practices. The GFE also additionally, applies protections against denial of service attacks. The sheer scale of its infrastructure, enables Google to simply absorb many denial of service attacks, even behind the GFEs.
- Google also has multi-tier, multi-layer denial of service protections that further reduce the risk of any denial of service impact. Inside Google's infrastructure, machine intelligence and rules warn of possible incidents. Google conducts Red Team exercises, simulated attacks to improve the effectiveness of its responses.
- Google aggressively limits and actively monitors the activities of employees who have been granted administrative access to the infrastructure. To guard against phishing attacks against Google employees, employee accounts including mine require use of U2F compatible security keys.
- To help ensure that code is as secure as possible Google stores its source code centrally and requires two-party review of new code. Google also gives its developers libraries that keep them from introducing certain classes of security bugs. Externally, Google also runs a vulnerability rewards program, where we pay anyone who is able to discover and inform us of bugs in our infrastructure or applications.

### Budgets and Billing

- GCP provides four tools to help:
    - budgets and alerts,
        - You can define budgets either per billing account or per GCP project. A budget can be a fixed limit or you can tie it to another metric. For example, a percentage of the previous month spend. To be notified when costs approach your budget limit, create an alert. For example, with a budget limit of $20,000 and an alert set at 90 percent, you'll receive a notification alert when your expenses reach $18,000
        - Alerts are generally set at 50 percent, 90 percent, and 100 percent. But you can customize that.
    - billing,
    - export,
        - Billing export lets you store detailed billing information in places where it's easy to retrieve for more detailed analysis, such as a BigQuery dataset or a Cloud storage bucket
    - reports and quotas.
        - Reports is a visual tool in the GCP console that allows you to monitor your expenditure.
        - GCP also implements quotas, which protect both account owners and the GCP community as a whole. Quotas are designed to prevent the over-consumption of resources, whether because of error or malicious attack. There are two types of quotas: rate quotas and allocation quotas. Both get applied at the level of the GCP project. Rate quotas reset after a specific time. For example, by default, the Kubernetes Engine service sets a quota of a 1000 calls to its API from each GCP project every 100 seconds. After that 100 seconds, the limit is reset. Allocation quotas, on the other hand, govern the number of resources you can have in your projects. For example, by default, each GCP project has a quota allowing it no more than five Virtual Private Cloud networks. Although projects all start with the same quotas, you can change some of them by requesting an increase from Google Cloud support.

## Getting Started With GCP

### GCP Resource Hierarchy

- Resource Hierarchy levels define trust boundaries
- Resources → Projects → Folders → Org Node
- Policies are inherited downwards in the hierarchy
- All GCP services you use are associated with a project
    - Track resource and quota usage.
    - Enable billing
    - Manage permissions and credentials.
    - Enable services and APIs.
- Each project is a separate compartment and each resource belongs to exactly one. Projects can have different owners and users - they're built separately and they're managed separately.
- Each GCP project has a name and a project ID that you assign. The project ID is a permanent, unchangeable identifier and it has to be unique across GCP. You use project IDs in several contexts to tell GCP which project you want to work with. On the other hand, project names are for your convenience and you can assign them. GCP also assigns each of your projects a unique project number and you'll see a display to you in various contexts.
    
    
    | Project ID | Globally Unique | Chosen by you | Immutable |
    | --- | --- | --- | --- |
    | Project Name | Neednt be unique | Chosen by you | Mutable |
    | Project Number | Globally Unique | Assigned by GCP | Immutable |
- In general, project IDs are made to be human readable strings and you'll use them frequently to refer to projects. You can organize projects into folders, although you don't have to. They're a tool at your disposal to make your life easier. For example, you can use folders to represent different departments, teams, applications or environments in your organization. Folders let teams have the ability to delegate administrative rights, so they can work independently.
- The resources in a folder inherit IAM policies from the folder. So, if project three and four are administered by the same team by design, you can put IAM policies into folder B instead. Doing it the other way, putting duplicate copies of those policies on project three and project four would be tedious and error prone. One word of caution: to use folders, you need an organization node at the top of the hierarchy.
- You probably want to organize all the projects in your company into a single structure. Most companies want the ability to have centralized visibility on how resources are being used and to apply policy centrally. That's what the organization node is for. It's the top of the hierarchy.
- Org node is created by default if GSuite is subscribed, else Google Cloud identity is used to create one.
- There are some special roles associated with Org Node. For example, you can designate an organization policy administrator, so that only people with privilege can change policies. You can also assign a project creator role, which is a great way to control who can spend money.
    
    ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%201.png)
    
- A policy is set on a resource.
- Each policy contains a set of roles and role members.
- Resources inherit policies from parent. Resource policies are a union of parent and resource.
- A less restrictive parent policy overrides a more restrictive resource policy.

### Identity And Access Management

- IAM lets administrators authorize who can take action on specific resources. An IAM policy has a “who” part, a “can do what” part, and an “on which resource” part.
- The “who” part of an IAM policy can be a Google account, a Google group, a service account, or an entire G Suite or Cloud Identity domain.
- The “can do what” part is defined by an IAM role. An IAM role is a collection of permissions. Most of the time, to do any meaningful operations, you need more than 1 permission. For example, to manage instances in a project, you need to create, delete, start, stop and change an instance. So the permissions are grouped together into a role to make them easier to manage.
- When you give a user, group, or service account a role on a specific element of the resource hierarchy, the resulting policy applies to the element you chose, as well as to elements below it in the hierarchy.
- Three Types of IAM Roles
    - Primitive
        - Primitive roles are broad. You apply them to a GCP project, and they affect all resources in that project
        - These are the Owner, Editor, and Viewer roles. If you’re a viewer on a given resource, you can examine it but not change its state. If you’re an editor, you can do everything a viewer can do plus change its state. And if you’re an owner, you can do everything an editor can do plus manage roles and permissions on the resource. The owner role on a project lets you do one more thing too: you can set up billing. Often companies want someone to be able to control the billing for a project without the right to change the resources in the project, and that’s why you can grant someone the billing administrator role.
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%202.png)
        
    - Predefined
        - GCP services offers their own sets of predefined roles, and they define where those roles can be applied. For example, later in this course, we’ll talk more about Compute Engine, which offers virtual machines as a service. Compute Engine offers a set of predefined roles, and you can apply them to Compute Engine resources in a given project, a given folder, or an entire organization.
        - Compute Engine’s instanceAdmin role let's whoever has it perform a certain set of actions on virtual machines. What set of actions? Those listed here: listing them, reading and changing their configurations, and starting and stopping them. And which virtual machines? Well, that depends on where the role is applied.
        - In this example, all the users of a certain Google group have the role, and they have it on all the virtual machines in project A.
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%203.png)
        
    - Custom
        - IAM custom roles let you define a precise set of permissions
        - What if you need something even finer-grained? That’s what custom roles permit. A lot of companies use a “least-privilege” model, in which each person in your organization the minimal amount of privilege needed to do his or her job. So, for example, maybe I want to define an “instanceOperator” role, to allow some users to stop and start Compute Engine virtual machines but not reconfigure them. Custom roles allow me to do that
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%204.png)
        
- Service Accounts control server to server instructions
    - What if you want to give permissions to a Compute Engine virtual machine rather than to a person? That’s what service accounts are for. For instance, maybe you have an application running in a virtual machine that needs to store data in Google Cloud Storage. But you don’t want to let just anyone on the Internet have access to that data; only that virtual machine. So you’d create a service account to authenticate your VM to Cloud Storage. Service accounts are named with an email address, but instead of passwords they use cryptographic keys to access resources.
- Service Accounts and IAM
    - Service accounts auth using keys
    - Google manages keys for compute engine and auth engine
- You can define a Predefined or Custom IAM role to the service account
- In this simple example, a service account has been granted Compute Engine’s Instance Admin role. This would allow an application running in a VM with that service account to create, modify, and delete other VMs. Incidentally, service accounts need to be managed too! For example, maybe Alice needs to manage what can act as a given service account, while Bob just needs to be able to view what can. Fortunately, in addition to being an identity, a service account is also a resource! So it can have IAM policies of its own attached to it. For instance, Alice can have the editor role on a service account and Bob can have the viewer role. This is just like granting roles for any other GCP resource.
- You can grant different groups of VMs in your project different identities. This makes it easier to manage different permissions for each group. You also can change the permissions of the service accounts without having to recreate the VMs. Here’s a more complex example. Say you have an application that’s implemented across a group of Compute Engine virtual machines. One component of your application needs to have an editor role on another project, but another component doesn’t. So you would create two different service accounts, one for each subgroup of virtual machines. Only the first service account has privilege on the other project. That reduces the potential impact of a miscoded application or a compromised virtual machine.

### Interacting with GCP

- There are 4 ways to interact with GCP
    - Cloud Platform Console
        - Centralized console for all project data
        - Dev Tools
            - Cloud source Repos
            - Cloud shell
            - Test lab
        - Access to product API's
        - Manage and create projects
    - Cloud shell and cloud sdk
        - SDK includes CLI tools for Cloud Platform products and services
        - Available as Docker image
        - Available via Cloud Shell
    - Cloud console mobile app
    - Rest-based API
        - Programmatic access to products and services
        - Enabled through the Google Cloud Platform Console
        - To help you control spend, most include daily quotas and rates
    - [https://developers.google.com/apis-explorer/](https://developers.google.com/apis-explorer/)

### Cloud Marketplace

- TODO

### Virtual Machines in the Cloud

- Virtual Private Cloud
    - VPC networks connect your Google Cloud platform resources to each other and to the internet. You can segment your networks, use firewall rules to restrict access to instances, and create static routes to forward traffic to specific destinations.
    - The Virtual Private Cloud networks that you define have global scope. They can have subnets in any GCP region worldwide and subnets can span the zones that make up a region. This architecture makes it easy for you to define your own network layout with global scope.
    - You can also have resources in different zones on the same subnet. You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it. Doing that doesn't affect already configured VMs.
- Compute Engine
    - Compute Engine offers managed virtual machines
    - High CPU, high memory, standard and shared-core machine types
    - Persistent disks
        - Standard SSD, Local SSD
        - Snapshots
    - Resize disks with no downtime
    - Instance metadata and startup scripts
    - Virtual machines have the power and generality of a full-fledged operating system in each. You configure a virtual machine much like you build out a physical server: by specifying its amounts of CPU power and memory, its amounts and types of storage, and its operating system. Compute Engine lets you create and run virtual machines on Google infrastructure. There are no upfront investments, and you can run thousands of virtual CPUs on a system that is designed to be fast and to offer consistent performance
    - You can flexibly reconfigure Compute Engine virtual machines. And a VM running on Google’s cloud has unmatched worldwide network connectivity.
    - You can create a virtual machine instance by using the Google Cloud Platform Console or the gcloud command-line tool. A Compute Engine instance can run Linux and Windows Server images provided by Google or any customized versions of these images. You can also build and run images of other operating systems.
    - Compute Engine offers customer friendly pricing
        - Per-second billing, sustained use discounts, committed use discounts
        - Preemptible instances
        - High throughput to storage at no extra cost
        - Custom machine types: Only pay for the hardware you need
    - Scale up or scale out with Compute Engine
        - You can make very large VMs in Compute Engine. At the time this deck was produced, the maximum number of virtual CPUs in a VM was 96, and the maximum memory size was in beta at 624. Check the GCP website to see where these maximums are today.
        - These huge VMs are great for workloads like in-memory databases and CPU-intensive analytics. But most GCP customers start off with scaling out, not up. Compute Engine has a feature called Autoscaling that lets you add and take away VMs from your application based on load metrics. The other part of making that work is balancing the incoming traffic among the VMs. And Google VPC supports several different kinds of load balancing!
- Important VPC Capabilities
    - We control the topology of the VPC Network
        - Use its route table to forward traffic within the network, even across subnets.
        - Use its firewall to control what network traffic is allowed.
        - Use Shared VPC to share a network, or individual subnets, with other GCP projects.
        - Use VPC Peering to interconnect networks in GCP projects
    - Much like physical networks, VPCs have routing tables. These are used to forward traffic from one instance to another instance within the same network, even across subnetworks and even between GCP zones, without requiring an external IP address. VPCs’ routing tables are built in; you don’t have to provision or manage a router.
    - Another thing you don’t have to provision or manage for GCP: a firewall. VPCs give you a global distributed firewall you can control to restrict access to instances, both incoming and outgoing traffic. You can define firewall rules in terms of metadata tags on Compute Engine instances, which is really convenient. For example, you can tag all your web servers with, say, “WEB,” and write a firewall rule saying that traffic on ports 80 or 443 is allowed into all VMs with the “WEB” tag, no matter what their IP address happens to be.
    - Recall that VPCs belong to GCP projects. But what if your company has several GCP projects, and the VPCs need to talk to each other? If you simply want to establish a peering relationship between two VPCs, so that they can exchange traffic, configure VPC Peering does. On the other hand, if you want to use the full power of IAM to control who and what in one project can interact with a VPC in another, configure Shared VPC.
    - With global Cloud Load Balancing, your application presents a single front-end to the world
        - Users get a single, global anycast IP address.
        - Traffic goes over the Google backbone from the closest point-of-presence to the user.
        - Backends are selected based on load.
        - Only healthy backends receive traffic.
        - No pre-warming is required.
    - 
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%205.png)
        
    - Google VPC offers a suite of load-balancing options
        - If you need cross-regional load balancing for a Web application, use HTTP(S) load balancing. For Secure Sockets Layer traffic that is not HTTP, use the Global SSL Proxy load balancer. If it’s other TCP traffic that does not use Secure Sockets Layer, use the Global TCP Proxy load balancer.
        - Those two proxy services only work for specific port numbers, and they only work for TCP. If you want to load balance UDP traffic, or traffic on any port number, you can still load balance across a GCP region with the Regional load balancer.
        - Finally, what all those services have in common is that they’re intended for traffic coming into the Google network from the Internet. But what if you want to load balance traffic inside your project, say, between the presentation layer and the business layer of your application? For that, use the Internal load balancer. It accepts traffic on a GCP internal IP address and load balances it across Compute Engine VMs.
    - Cloud DNS is highly available and scalable
        - Create managed zones, then add, edit, delete DNS records
        - Programmatically manage zones and records using RESTful API or command-line interface
        - One of the most famous Google services that people don’t pay for is 8.8.8.8, which provides a public Domain Name Service to the world. DNS is what translates Internet hostnames to addresses, and as you would imagine, Google has a highly developed DNS infrastructure. It makes 8.8.8.8 available so that everybody can take advantage of it.
        - But what about the Internet hostnames and addresses of applications you build in GCP? GCP offers Cloud DNS to help the world find them. It’s a managed DNS service running on the same infrastructure as Google. It has low latency and high availability, and it’s a cost-effective way to make your applications and services available to your users. The DNS information you publish is served from redundant locations around the world.
        - Cloud DNS is also programmable. You can publish and manage millions of DNS zones and records using the GCP Console, the command-line interface, or the API.
        - Google has a global system of edge caches. You can use this system to accelerate content delivery in your application using Google Cloud CDN. Your customers will experience lower network latency, the origins of your content will experience reduced load, and you can save money too. Once you've set up HTTP(S) Load Balancing, simply enable Cloud CDN with a single checkbox
        - There are lots of other CDNs out there, of course. If you are already using one, chances are, it is a part of GCP’s CDN Interconnect partner program, and you can continue to use it
    - Google Cloud Platform offers many interconnect options
        - Many customers using VPC Networks want to communicate between networks. Some interconnect options are listed below
            - VPN - Secure multi-Gbps connection over VPN tunnels
            - Direct Peering - Private connection between you and Google for your hybrid cloud workloads
            - Carrier Peering - Connection through the largest partner network of service providers
            - Dedicated Interconnect - Connect N X 10G transport circuits for private cloud traffic to Google Cloud at Google POPs (SLA Available -  Service Legal Agreement)
            - Partner Interconnect - Connectivity between your on-premises network and your VPC network through a supported service provider (SLA Available - Service Legal Agreement)
        - Lots of GCP customers want to interconnect their other networks to their Google VPCs. such as on-premises networks or their networks in other clouds. There are many good choices.
        - Many customers start with a Virtual Private Network connection over the Internet, using the IPsec protocol. To make that dynamic, they use a GCP feature called Cloud Router. Cloud Router lets your other networks and your Google VPC exchange route information over the VPN using the Border Gateway Protocol. For instance, if you add a new subnet to your Google VPC, your on-premises network will automatically get routes to it.
        - But some customers don’t want to use the Internet, either because of security concerns or because they need more reliable bandwidth. They can consider peering with Google using Direct Peering. Peering means putting a router in the same public datacenter as a Google point of presence and exchanging traffic. Google has more than 100 points of presence around the world. Customers who aren’t already in a point of presence can contract with a partner in the Carrier Peering program to get connected.
        - One downside of peering, though, is that it isn’t covered by a Google Service Level Agreement. Customers who want the highest uptimes for their interconnection with Google should use Dedicated Interconnect, in which customers get one or more direct, private connections to Google. If these connections have topologies that meet Google’s specifications, they can be covered by up to a 99.99% SLA. These connections can be backed up by a VPN for even greater reliability.
        - Partner Interconnect provides connectivity between your on-premises network and your VPC network through a supported service provider. A Partner Interconnect connection is useful if your data center is in a physical location that can't reach a Dedicated Interconnect colocation facility or if your data needs don't warrant an entire 10 Gbps connection. Depending on your availability needs, you can configure Partner Interconnect to support mission-critical services or applications that can tolerate some downtime. As with Dedicated Interconnect, if these connections have topologies that meet Google’s specifications, they can be covered by up to a 99.99% SLA, but note that Google is not responsible for any aspects of Partner Interconnect provided by the third party service provider nor any issues outside of Google's network.
        
        ### GCP Storage Options
        
        - **Cloud Storage**
            - Cloud Storage is binary large-object storage
            - High performance, internet-scale
            - Simple administration
            - Data encryption at rest
            - Data encryption in transit by default from Google to endpoint
            - Online and offline import services are available
            - Google Cloud Storage offers developers and IT organizations durable and highly available object storage. It assesses no minimum fee; you pay only for what you use. Prior provisioning of capacity isn’t necessary.
            - What’s object storage? It’s not the same as file storage, in which you manage your data as a hierarchy of folders. It’s not the same as block storage, in which your operating system manages your data as chunks of disk. Instead, object storage means this: you say to your storage, “Here, keep this arbitrary sequence of bytes,,” and the storage lets you address it with a unique key. In Google Cloud Storage and in other systems, these unique keys are in the form of URLs, which means object storage interacts well with web technologies.
            - Google Cloud Storage always encrypts your data on the server side, before it is written to disk, at no additional charge. Data traveling between a customer’s device and Google is encrypted by default using HTTPS/TLS (Transport Layer Security). In fact, Google was the first major cloud provider to enable HTTPS/TLS by default.
            - Google Cloud Storage is not a file system, although it can be accessed as one via third-party tools such as Cloud Storage FUSE. The storage objects offered by Google Cloud Storage are “immutable,” which means that you do not edit them in place, but instead create a new version. Google Cloud Storage’s primary use is whenever binary large-object storage is needed: online content, backup and archiving, storage of intermediate results in processing workflows, and more.
            - Offline Media Import/Export is a third-party solution that allows you to load data into Google Cloud Storage by sending your physical media, such as hard disk drives (HDDs), tapes, and USB flash drives, to a third-party service provider who uploads data on your behalf. Offline Media Import/Export is helpful if you’re limited to a slow, unreliable, or expensive internet connection.
            - Offline import is available through third-party providers: [https://cloud.google.com/storage/docs/offline-media-import-export](https://cloud.google.com/storage/docs/offline-media-import-export) Cloud Storage Transfer Service enables you to import large amounts of online data into Google Cloud Storage quickly and cost-effectively. To use Cloud Storage Transfer Service, you set up a transfer from a data source to data sink. Data sources can be an Amazon Simple Storage Service (Amazon S3) bucket, an HTTP/HTTPS location, or another Google Cloud Storage bucket. Data sinks are always a Google Cloud Storage bucket.
            - Example uses of Cloud Storage Transfer Service include:
                - Backing up data to a Google Cloud Storage bucket from other storage providers
                - Moving data from a Standard Storage bucket to a Nearline Storage bucket to lower your storage costs
            
            ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%206.png)
            
            - Your Cloud Storage files are organized into buckets. When you create a bucket: you give it a globally-unique name; you specify a geographic location where the bucket and its contents are stored; and you choose a default storage class. Pick a location that minimizes latency for your users. For example, if most of your users are in Europe, you probably want to pick a European location: a GCP region in Europe, or else the EU multi-region.
            - There are several ways to control users’ access to your objects and buckets. For most purposes, Cloud IAM is sufficient. Roles are inherited from project to bucket to object. If you need finer control, you can create access control lists (“ACLs”) that offer finer control, ACLs define who has access to your buckets and objects, as well as what level of access they have. Each ACL consists of two pieces of information: A scope, which defines who can perform the specified actions (for example, a specific user or group of users). And a permission, which defines what actions can be performed (for example, read or write).
            - Remember that Cloud Storage objects are immutable. You can turn on object versioning on your buckets if you want. If you do, Cloud Storage keeps a history of modifications--that is, overwrites or deletes--of all objects in the bucket. You can list the archived versions of an object, restore an object to an older state, or permanently delete a version, as needed. If you don’t turn on object versioning, new always overwrites old.
            - Cloud Storage also offers lifecycle management policies. For example, you could tell Cloud Storage to delete objects older than 365 days, or to delete objects created before January 1, 2013; or to keep only the 3 most recent versions of each object in a bucket that has versioning enabled.
            
            ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%207.png)
            
            - There are several ways to bring data into Cloud Storage
                - Online Transfer (Self-managed copies using command-line tools or drag-and-drop)
                    - Many customers simply use gsutil, which is the Cloud Storage command from the Cloud SDK. You can also move data in with a drag and drop in the GCP Console, if you use the Google Chrome browser. But what if you have to upload terabytes or even petabytes of data? Google Cloud Platform offers the online Storage Transfer Service and the offline Transfer Appliance to help.
                - Storage Transfer Service (Scheduled, managed batch transfers )
                    - The Storage Transfer Service lets you schedule and manage batch transfers to Cloud Storage from another cloud provider, from a different Cloud Storage region, or from an HTTP(S) endpoint.
                - Transfer Appliance (Rackable appliances to securely ship your data)
                    - The Transfer Appliance is a rackable, high-capacity storage server that you lease from Google Cloud. You simply connect it to your network, load it with data, and then ship it to an upload facility where the data is uploaded to Cloud Storage. The service enables you to securely transfer up to a petabyte of data on a single appliance. As of this recording, it’s still beta, and it’s not available everywhere, so check the website for details.
                
                ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%208.png)
                
        - Cloud Big Table
            - Fully managed NoSQL, wide-column database service for terabyte applications
            - Integrated
                - Accessed using HBase API
                - Native compatibility with big data, Hadoop ecosystems
            - Cloud Bigtable is ideal for applications that need very high throughput and scalability for non-structured key/value data, where each value is typically no larger than 10 MB. Cloud Bigtable also excels as a storage engine for batch MapReduce operations, stream processing/analytics, and machine-learning applications.
            - Cloud Bigtable is offered through the same open source API as HBase, the native Hadoop database. This enables portability of applications between HBase and Bigtable.
            - Why chose Big Table
                - Replicated Storage
                - Data encryption in-flight and at rest
                - Role-based ACL’s
                - Drives major applications such as Google Analytics and Gmail
            - Customers frequently choose Bigtable if the data is:
                - Big (> 1 TB)
                - Fast(Data is high throughput or rapidly changing)
                - NO SQL(Transactions, strong relational semantics not required)
                - Especially if it is Time series, big data and machine learning
            - Bigtable is designed to handle massive workloads at consistent low latency and high throughput, so it's a great choice for both operational and analytical applications, including IoT, user analytics, and financial data analysis.
                
                ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%209.png)
                
        - Cloud SQL or Cloud Spanner
            - Managed RDBMS
            - Offers MySQL and PostgreSQL databases as a service
            - Automatic replication
            - Managed backups
            - Vertical scaling (read and write)
            - Horizontal scaling (read)
            - Google security
            - Cloud SQL is an easy-to-use service that delivers fully managed relational databases. Cloud SQL lets you hand off to Google the mundane, but necessary and often time-consuming tasks—like applying patches and updates, managing backups, and configuring replications—so you can put your focus on building great applications.
            - Every Cloud SQL instance includes a network firewall, allowing you to control network access to your database instance by granting access. Cloud SQL is easy to use: it doesn't require any software installation or maintenance.
            - Easily scale up to 64 processor cores and more than 100 GB of RAM. Quickly scale out with read replicas.
            - Automatic replication - Google Cloud SQL supports the following read replica scenarios:
                - Cloud SQL instances replicating from a Cloud SQL master instance Replicas are other instances in the same project and location as the master instance. This feature is in Beta.
                - Cloud SQL instances replicating from an external master instance The master instance is external to Google Cloud SQL. For example, it can be outside the Google network or in a Google Compute Engine instance. This feature is in Beta.
                - External MySQL instances replicating from a Cloud SQL master instance External replicas are in hosting environments, outside of Cloud SQL.
            - Managed backups
                - Cloud SQL takes care of securely storing your backed-up data and makes it easy for you to restore from a backup and perform a point-in-time recovery to a specific state of an instance.
                - Cloud SQL retains up to 7 backups for each instance, which is included in the cost of your instance. Cloud SQL customer data is encrypted when on Google's internal networks and when stored in database tables, temporary files, and backups.
            - More benefits of Cloud SQL
                - Another benefit of Cloud SQL instances is that they are accessible by other GCP services and even external services.
                - You can use Cloud SQL with App Engine using standard drivers like Connector/J for Java or MySQLdb for Python.
                - You can authorize Compute Engine instances to access Cloud SQL instances and configure the Cloud SQL instance to be in the same zone as your virtual machine.
                - Cloud SQL also supports other applications and tools that you might be used to, like SQL Workbench, Toad and other external applications using standard MySQL drivers.
            - Cloud Spanner is Horizontally scalable RDBMS
                - Automatic replication
                - Strong global consistency
                - Managed instances with high availability
                - Can store more than 2TB of data
                - Many IOPS (Tens of thousands of reads/writes per second or more)
        - Cloud Datastore
            - Cloud Datastore is a horizontally scalable NoSQL DB
            - NoSQL designed for application backends
            - Uses a distributed architecture to automatically manage scaling
            - Built-in redundancy
            - Supports ACID transactions
            - The total size of Cloud Datastore databases can grow to terabytes and more.
            - Includes a free daily quota
            - Access from anywhere through a RESTful interfac
            
            ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2010.png)
            
            ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2011.png)
            

### Containerization and Kubernetes (GKE)

TODO

- Anthos
    - Distributed Systems housed on-premises lacks flexibility and agility
    - Housed on premises means difficult to upgrade since there is a need to buy new servers if capacity increase is needed (Upgrade is costly and server lifespan is short)
    - Lead time for new capacity could be up to a year or more
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2012.png)
        
    - Benefits of Cloud solution
        - Move only some of your compute workloads to cloud
        - Move at our own pace
        - Lower costs and scalability
        - Add specialized services to your compute resources stack
    - Anthos is a hybrid and multi-cloud solution powered by the latest innovations in distributed systems, and service management software from Google. The Anthos framework rests on Kubernetes and Google Kubernetes engine deployed on-prem. Which provides the foundation for an architecture that is fully integrated with centralized management through a central control plane that supports policy based application lifecycle delivery across hybrid and multi-cloud environments.
    - Anthos also provides a rich set of tools for monitoring and maintaining the consistency of your applications across all of your network, whether on-premises, in the Cloud, or in multiple clouds.
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2013.png)
        
    - -

### Google App Engine

- Introduction to App Engine
    - App Engine is a PaaS for building scalable applications
        - App Engine makes deployment, maintenance, and scalability easy so you can focus on innovation
        - Especially suited for building scalable web applications and mobile backends
        - App Engine provides you with built-in services and APIs such as NoSQL datastores, memcache, load balancing, health checks, application logging, and a user authentication API, common to most applications.
        - App Engine will scale your application automatically in response to the amount of traffic it receives so you only pay for the resources you use. Just upload your code and Google will manage your app's availability. There are no servers for you to provision or maintain.
        - [Security Scanner](https://cloud.google.com/security-command-center) automatically scans and detects common web application vulnerabilities. It enables early threat identification and delivers very low false-positive rates. You can easily set up, run, schedule, and manage security scans from the Google Cloud Platform Console.
        - App Engine works with popular development tools such as Eclipse, IntelliJ, Maven, Git, Jenkins, and PyCharm. You can build your apps with the tools you love without changing your workflow.
- Google App Engine Standard Environment
    - Easily deploy your applications
    - Autoscale workloads to meet demand
    - Economical
        - Free daily quota
        - Usage based pricing
    - SDK’s for development, testing and deployment
    - The App Engine standard environment is based on container instances running on Google's infrastructure. Containers are preconfigured with one of several available runtimes (Java 7, Python 2.7, Go and PHP). Each runtime also includes libraries that support App Engine standard APIs. For many applications, the standard environment runtimes and libraries may be all you need.
    - The App Engine standard environment makes it easy to build and deploy an application that runs reliably even under heavy load and with large amounts of data. It includes the following features:
        - Persistent storage with queries, sorting, and transactions
        - Automatic scaling and load balancing
        - Asynchronous task queues for performing work outside the scope of a request
        - Scheduled tasks for triggering events at specified times or regular intervals
        - Integration with other Google cloud services and APIs
    - Requirements
        - Specific versions of Java, Python, PHP, and Go are supported
        - Few constraints
            - No writing to local file system
            - All requests time out at 60 seconds
            - Third-party software installations are limited
    - Software Development Kits (SDKs) for App Engine are available in all
    supported languages. Each SDK includes:
        - All of the APIs and libraries available to App Engine
        - A simulated, secure sandbox environment that emulates all of the App
        Engine services on your local computer
        - Deployment tools that allow you to upload your application to the cloud
        and manage different versions of your application’
    - The SDK manages your application locally, and the Google Cloud Platform Console manages your application in production. The Google Cloud Platform Console uses a web-based interface to create new applications, configure domain names, change which version of your application is live, examine access and error logs, and much more.
    - Applications run in a secure, sandboxed environment, allowing the App Engine standard environment to distribute requests across multiple servers, and scaling servers to meet traffic demands. Your application runs within its own secure, reliable environment that is independent of the hardware, operating system, or physical location of the server.
    - In this diagram we see App Engine Standard Environment in practice. You’ll develop your application and run a test version of it locally using the App Engine SDK. Then, when you’re ready, you’ll use the SDK to deploy it.
    - Each App Engine application runs in a GCP project. App Engine automatically provisions server instances and scales and load-balances them. Meanwhile, your application can make calls to a variety of services using dedicated APIs. For example, a NoSQL datastore to make data persistent; caching of that data using memcache; searching; logging; user login; and the ability to launch actions not triggered by direct user requests, like task queues and a task scheduler
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2014.png)
        
- App Engine Flexible Environment
    - Build and deploy containerized apps with a click
    - No sandbox constraints
    - Can access App Engine resources
    - Standard runtimes: Python, Java, Go, Node.js
    - Custom runtime support: Any language that supports HTTP requests
        - Package your runtime as a Dockerfile
    - Your application runs inside Docker containers on Google Compute Engine virtual machines (VMs). App Engine manages these Compute Engine machines for you. They’re health-checked, healed as necessary, and you get to choose what geographical region they run in. And critical, backward-compatible updates to their operating systems are automatically applied. All this so that you can just focus on your code.
    - Microservices, authorization, SQL and noSQL databases, traffic splitting, logging, search, versioning, security scanning, memcache, and content delivery networks are all supported natively. In addition, the App Engine flexible environment allows you to customize your runtime and even the operating system of your virtual machine using Dockerfiles.
        - Runtimes: The flexible environment includes native support for Java 8/Servlet 3.1/Jetty 9, Python 2.7 and Python 3.4, Node.js, and Go. Developers can customize these runtimes or provide their own runtime, such as Ruby or PHP, by supplying a custom Docker image or Dockerfile from the open source community.
        - Infrastructure customization: Because VM instances in the flexible environment are Compute Engine virtual machines, you can use SSH to connect to every single VM and Docker container for debugging purposes and further customization.
        - Performance: Take advantage of a wide array of CPU and memory configurations. You can specify how much CPU and memory each instance of your application needs, and the flexible environment will provision the necessary infrastructure for you. App Engine manages your virtual machines, ensuring that:
        - Instances are health-checked, healed as necessary, and co-located with other module instances within the project.
        - Critical, backward-compatible updates are automatically applied to the underlying operating system.
        - VM instances are automatically located by geographical region according to the settings in your project. Google's management services ensure that all of a project's VM instances are co-located for optimal performance.
        - VM instances are restarted on a weekly basis. During restarts, Google's management services will apply any necessary operating system and security updates.
        - App Engine flexible environment apps that use standard runtimes can access App Engine services: Datastore, Memcache, task queues, logging, users, and so on.
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2015.png)
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2016.png)
        
- Cloud Endpoints and Apigee Edge
    - Distributed API management through an API console
    - Expose your API using a RESTful interface
    - Control access and validate calls with JSON Web Tokens and Google API keys
    - Identify web, mobile users with Auth0 and Firebase Authentication
    - Generate client libraries
    - Cloud Endpoints is a distributed API management system. It provides an API console, hosting, logging, monitoring, and other features to help you create, share, maintain, and secure your APIs. You can use Cloud Endpoints with any APIs that support the OpenAPI Specification, formerly known as the Swagger spec.
    - Cloud Endpoints uses the distributed Extensible Service Proxy to provide low latency and high performance for serving even the most demanding APIs. Extensible Service Proxy is a service proxy based on NGINX. It runs in its own Docker container for better isolation and scalability. The proxy is containerized and distributed in the Container Registry and Docker registry, and can be used with App Engine, Kubernetes Engine, Compute Engine or Kubernetes
    - Cloud Endpoint Features
        - User auth  - JWT Validation and streamlined experience for GAuth and Firebase Auth
        - Automated Deployment
        - Loggin and Monitoring
        - API Keys
        - Easy Integration
    - Supported Platforms
        - Runtime Env -  App Engine Flexible, Kubernetes Engine and Compute Engine
        - Clients -  Android, iOS and JavaScript
    - Apigee Edge helps you secure and monetize APIs
        - A platform for making APIs available to your customers and partners
        - Contains analytics, monetization, and a developer portal
        - Peel of services from legacy application if it needs to be retired or decommisioned.

### Development in the Cloud

- Cloud Source Repositories
    - Fully featured Git repositories hosted on GCP
    - Supports collaborative development of cloud apps
    - Includes integration with Stackdriver Debugger
    - Cloud Source Repositories provides Git version control to support collaborative development of any application or service, including those that run on App Engine and Compute Engine. If you are using the Stackdriver Debugger, you can use Cloud Source Repositories and related tools to view debugging information alongside your code during application runtime. Cloud Source Repositories also provides a source viewer that you can use to browse and view repository files from within the Google Cloud Platform Console.
    - With Cloud Source Repositories, you can have any number of private Git repositories, which allows you to organize the code associated with your cloud project in whatever way works best for you. Google Cloud diagnostics tools like the Debugger and Error Reporting can use the code from your Git repositories to let you track down issues to specific errors in your deployed code without slowing down your users. If you’ve already got your code in GitHub or BitBucket repositories, you can bring that into your cloud project and use it just like any other repository, including browsing and diagnostics.
- Cloud Functions
    - Create single-purpose functions that respond to events without a server or runtime
        - Event examples: New instance created, file added to Cloud Storage
    - Written in Javascript; execute in managed node.js env on GCP
    - Cloud Functions is a lightweight, event-based, asynchronous compute solution that allows you to create small, single-purpose functions that respond to cloud events without the need to manage a server or a runtime environment. You can use these functions to construct applications from bite-sized business logic. You can also use Cloud Functions to connect and extend cloud services.
    - You are billed, to the nearest 100 milliseconds, only while your code is running.
    - Cloud Functions are written in JavaScript and execute in a managed Node.js environment on Google Cloud Platform. Events from Cloud Storage and Cloud Pub/Sub can trigger Cloud Functions asynchronously, or you can use HTTP invocation for synchronous execution.
    - Cloud Events are things that happen in your cloud environment. These might be things like changes to data in a database, files added to a storage system, or a new virtual machine instance being created.
    - Events occur whether or not you choose to respond to them. Creating a response to an event is done with a trigger. A trigger is a declaration that you are interested in a certain
- Deployment : Infrastructure as a Code
    - Infrastructure management service
    - Create a .yaml template describing your environment and use Deployment Manager to create resources
    - Provides repeatable deployments
    - Here’s a tip: you can store and version-control your Deployment Manager templates in Cloud Source Repositories.
- Monitoring: Proactive Instrumentation
    - Stackdriver is GCP’s tool for monitoring, logging, and diagnostics. Stackdriver gives you access to many different kinds of signals from your infrastructure platforms, virtual machines, containers, middleware, and application tier: logs, metrics, traces. It gives you insight into your application’s health, performance, and availability, so if issues occur you can fix them faster.
    - Capabilities
        - Monitoring
            - Platform, system, and application metrics
            - Uptime/health checks
            - Dashboards and alerts
        - Error Reporting
            - Error notifications and dashboard
        - Logging
            - Platform, system, and application logs
            - Log search, view, filter, and export
            - Log-based metrics
        - Debugger
            - Debug Applications
        - Trace
            - Latency reporting and sampling
            - Per-URL latency and statistics
        - Profiler
            - Continuous profiling of CPU and memory consumption

### Introduction to Machine Learning and Bigdata

- Cloud Dataproc
    - Cloud Dataproc is managed Hadoop
    - Fast, easy, managed way to run Hadoop and Spark/Hive/Pig on GCP
    - Create clusters in 90 seconds or less on average.
    - Scale clusters up and down even when jobs are running.
    - Why use cloud dataproc?
        - Easily migrate on-premises Hadoop jobs to the cloud.
        - ‘Quickly analyze data (like log data) stored in Cloud Storage; create a cluster in 90 seconds or less on average, and then delete it immediately.
        - Use Spark/Spark SQL to quickly perform data mining and analysis.
        - Use Spark Machine Learning Libraries (MLlib) to run classification algorithms.
- Cloud Dataflow
    - Cloud Dataflow offers managed data pipelines
    - Processes data using Compute Engine instances.
        - Clusters are sized for you
        - Automated scaling, no instance provisioning required
    - Write code once and get batch and streaming.
        - Transform-based programming model
    - Cloud Dataproc is great when you have a dataset of known size, or when you want to manage your cluster size yourself. But what if your data shows up in realtime? Or it’s of unpredictable size or rate? That’s where Cloud Dataflow is a particularly good choice. It’s both a unified programming model and a managed service, and it lets you develop and execute a big range of data processing patterns: extract-transform-and-load, batch computation, and continuous computation. You use Dataflow to build data pipelines, and the same pipelines work for both batch and streaming data.
    - Dataflow is a unified programming model and a managed service for developing and executing a wide range of data processing patterns including ETL, batch computation, and continuous computation. Cloud Dataflow frees you from operational tasks like resource management and performance optimization.
    - Cloud Dataflow features:
        - Resource Management
            - Cloud Dataflow fully automates management of required processing resources. No more spinning up instances by hand.
        - On Demand
            - All resources are provided on demand, enabling you to scale to meet your business needs. No need to buy reserved compute instances.
        - Intelligent Work Scheduling
            - Automated and optimized work partitioning which can dynamically rebalance lagging work. No more chasing down “hot keys” or pre-processing your input data.
        - Auto Scaling
            - Horizontal auto scaling of worker resources to meet optimum throughput requirements results in better overall price-to-performance.
        - Unified Programming Model
            - The Dataflow API enables you to express MapReduce like operations, powerful data windowing, and fine grained correctness control regardless of data source.
        - Open Source
            - Developers wishing to extend the Dataflow programming model can fork and or submit pull requests on the Java-based Cloud Dataflow SDK. Dataflow pipelines can also run on alternate runtimes like Spark and Flink.
        - Monitoring
            - Integrated into the Google Cloud Platform Console, Cloud Dataflow provides statistics such as pipeline throughput and lag, as well as consolidated worker log inspection—all in near-real time.
        - Integrated
            - Integrates with Cloud Storage, Cloud Pub/Sub, Cloud Datastore, Cloud Bigtable, and BigQuery for seamless data processing. And can be extended to interact with others sources and sinks like Apache Kafka and HDFS.
        - Reliable & Consistent Processing
            - Cloud Dataflow provides built-in support for fault-tolerant execution that is consistent and correct regardless of data size, cluster size, processing pattern or pipeline complexity.
        
        ![Untitled](Google%20Cloud%20Fundamentals%20Core%20Infrastructure%20Attachments/Untitled%2017.png)
        
    - Why use cloud dataflow?
        - ETL (extract/transform/load) pipelines to move, filter, enrich, shape data
        - Data analysis: batch computation or continuous computation using streaming
        - Orchestration: create pipelines that coordinate services, including external services
        - Integrates with GCP services like Cloud Storage, Cloud Pub/Sub, BigQuery, and Bigtable
            - Open source Java and Python SDKs
        - People use Dataflow in a variety of use cases.
        - For one, it serves well as a general-purpose ETL tool. And its use case as a data analysis engine comes in handy in things like these: fraud detection in financial services; IoT analytics in manufacturing, healthcare, and logistics; and clickstream, Point-of-Sale, and segmentation analysis in retail.
        - And, because those pipelines we saw can orchestrate multiple services, even external services, it can be used in realtime applications such as personalizing gaming user experiences
- Big Query
    - BigQuery is a fully managed data warehouse
    - Provides near real-time interactive analysis of massive datasets (hundreds of TBs)
    - Query using SQL syntax (SQL 2011)
    - No cluster maintenance is required.
    - Why Big Query
        - If, instead of a dynamic pipeline, you want to do ad-hoc SQL queries on a massive dataset, that is what BigQuery is for. BigQuery is Google's fully managed, petabyte scale, low cost analytics data warehouse. BigQuery is Google's fully managed, petabyte scale, low cost analytics data warehouse.
        - BigQuery is NoOps: there is no infrastructure to manage and you don't need a database administrator, so you can focus on analyzing data to find meaningful insights, use familiar SQL, and take advantage of our pay-as-you-go model. BigQuery is a powerful big data analytics platform used by all types of organizations, from startups to Fortune 500 companies.
        - BigQuery’s features:
            - Flexible Data Ingestion
                - Load your data from Cloud Storage or Cloud Datastore, or stream it into BigQuery at 100,000 rows per second to enable real-time analysis of your data.
            - Global Availability
                - You have the option to store your BigQuery data in European locations while continuing to benefit from a fully managed service, now with the option of geographic data control, without low-level cluster maintenance.
            - Security and Permissions
                - You have full control over who has access to the data stored in BigQuery. If you share datasets, doing so will not impact your cost or performance; those you share with pay for their own queries.
            - Cost Controls
                - BigQuery provides cost control mechanisms that enable you to cap your daily costs at an amount that you choose. For more information, see Cost Controls.
            - Highly Available
                - Transparent data replication in multiple geographies means that your data is available and durable even in the case of extreme failure modes.
            - Super Fast Performance
                - Run super-fast SQL queries against multiple terabytes of data in seconds, using the processing power of Google's infrastructure.
            - Fully Integrated
                - In addition to SQL queries, you can easily read and write data in BigQuery via Cloud Dataflow, Spark, and Hadoop.
            - Connect with Google Products
                - You can automatically export your data from Google Analytics Premium into BigQuery and analyze datasets stored in Google Cloud Storage, Google Drive, and Google Sheets.
            - BigQuery can make Create, Replace, Update, and Delete changes to databases, subject to some limitations and with certain known issues.
        - BigQuery runs on Google’s high-performance infrastructure
        - Compute and storage are separated with a terabit network in between
        - You only pay for storage and processing used
        - Automatic discount for long-term data storage
        - It’s easy to get data into BigQuery. You can load from Cloud Storage or Cloud Datastore, or stream it into BigQuery at up to 100,000 rows per second.
        - BigQuery is used by all types of organizations, from startups to Fortune 500 companies. Smaller organizations like BigQuery’s free monthly quotas. Bigger organizations like its seamless scale and its available 99.9% service level agreement.
        - Long term storage pricing is an automatic discount for data residing in BigQuery for extended periods of time. When the age of your data reaches 90 days in BigQuery, Google will automatically drop the price of storage from $0.02 per GB per month down to $0.01 per GB per month.
- Cloud Pub/Sub
    - Cloud Pub/Sub is scalable, reliable messaging
    - Supports many-to-many asynchronous messaging
        - Application components make push/pull subscriptions to topics
    - Includes support for offline consumers
    - Based on proven Google technologies
    - Integrates with Cloud Dataflow for data processing pipelines
    - Cloud Pub/Sub is a fully managed real-time messaging service that allows you to send and receive messages between independent applications. You can leverage Cloud Pub/Sub’s flexibility to decouple systems and components hosted on Google Cloud Platform or elsewhere on the internet. By building on the same technology Google uses, Cloud Pub/Sub is designed to provide “at least once” delivery at low latency with on-demand scalability to 1 million messages per second (and beyond).
    - Cloud Pub/Sub features:
        - Highly Scalable
            - Any customer can send up to 10,000 messages per second, by default—and millions per second and beyond, upon request.
        - Push and Pull Delivery
            - Subscribers have flexible delivery options, whether they are accessible from the internet or behind a firewall.
        - Encryption
            - Encryption of all message data on the wire and at rest provides data security and protection.
        - Replicated Storage
            - Designed to provide “at least once” message delivery by storing every message on multiple servers in multiple zones.
        - Message Queue
            - Build a highly scalable queue of messages using a single topic and subscription to support a one-to-one communication pattern.
        - End-to-End Acknowledgement
            - Building reliable applications is easier with explicit application-level acknowledgements.
        - Fan-out
            - Publish messages to a topic once, and multiple subscribers receive copies to support one-to-many or many-to-many communication patterns.
        - REST API
            - Simple, stateless interface using JSON messages with API libraries in many programming languages.
    - Why use Cloud Pub/Sub?
        - Building block for data ingestion in Dataflow, Internet of Things (IoT), Marketing Analytics
        - Foundation for Dataflow streaming
        - Push notifications for cloud-based applications
        - Connect applications across Google Cloud Platform (push/pull between Compute Engine and App Engine)
- Cloud Datalab
    - Cloud Datalab offers interactive data exploration
    - Interactive tool for large-scale data exploration, transformation, analysis, and visualization
    - Integrated, open source - Built on Jupyter (formerly IPython)
    - Datalab Features
        - Integrated
        - Multi Language Support
        - Notebook format
        - Pay per use pricing
        - Interactive Data Visualisation
        - Collaborative
        - Open Source
        - Custom Deployment
        - IPython Support
    - Why Cloud Datalab?
        - Same a Jupyter notebook but on cloud
        - No Auth issues when retrieving data from Big Query, Compute Engine etc
- Machine Learning Platform
    - Self Explanatory
    - Cloud Vision API - Image Analysis using rest api
    - Cloud Speech API -  Speech Analysis
    - NLP API - Grammar Analysis, Syntax Analysis etv
    - Translation API - Self Explanatory
    - Video Intelligence API - Video Analysis
    -