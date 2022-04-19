# Essential Google Cloud Infrastructure: Core Services

# **Week 1:**

# Course Intro

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%201.png)

# IAM

## Identity and Access Management

what is identity access management? It is a way of identifying who can do what on which resource. **The who can be a person, group, or application. The what refers to specific privileges or actions, and the resource could be any Google Cloud service.**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%202.png)

### IAM Objects

- Organization
- Folders
- Projects
- Resources
- Roles
- Members

## Organization

### Organization Node

- An organization node is a root node for Google Cloud resources
- Organization roles:
    - Org Admin - provides a user like Bob with access to administer all resources belonging to his organization, which is useful for auditing.
    - Project Creator - allows a user like Alice to create projects within her organization. I am showing the project creator role here because it can also be applied at the organization level, which would then be inherited by all the projects within the organization.

### Creating and managing organizations

- When a user with a Workspace or Cloud Identity account creates a Google Cloud Project, an Organization resource is automatically provisioned for them. Then, Google Cloud communicates its availability to the Workspace or Cloud Identity super admins. These super admin accounts should be used carefully because they have a lot of control over your organization and all the resources underneath it.
- The Workspace or Cloud Identity super administrators and the Google Cloud Organization admin are key roles during the setup process and for lifecycle control for the Organization resource. The two roles are generally assigned to different users or groups, although this depends on the organization's structure and needs.
- Click the link below for more details

[Creating and managing organizations | Resource Manager Documentation | Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-organization#adding_an_organization_admin)

- Super Admin Resposibilities
    - Assign the org admin role to some users
    - Be a POC in case of recovery issues
    - Control the lifecycle of Workspace or Cloud Identity Account and Organization Resource
- Org Admin Roles Responsibilities
    - Define IAM Policies
    - Determine the structure of the resource hierarchy
    - Delegate responsibility over critical components such as Networking, Billing, and Resource Hierarchy through IAM roles.

### Folders

- Folders can be viewed as sub-organizations within the organization.
- Folders provide an additional grouping mechanism and isolation boundary between projects. Folders can be used to model different legal entities, departments, and teams within a company. For example, a first level of folders could be used to represent the main departments in your organization, like departments X and Y.
- Because folders can contain projects and other folders, each folder could then include other sub-folders to represent different teams, like teams A and B.
- Each team folder could contain additional sub-folders to represent different applications, like Products 1 and 2.
- Folders allow delegation of administration rights, so for example, each head of a department can be granted full ownership of all GCP resources that belong to their department. Similarly, access to resources can be limited by folder, so users in one department can only access and create GCP resources within that folder

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%203.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%204.png)

### Roles

- Three type of roles
    - Basic
        - IAM basic roles apply across all Google Cloud services in a project.
        - Basic roles are the original roles that were available in the Cloud Console, but they are broad
        - You apply them to a Google Cloud project, and they affect all resources in that project.
        - IAM basic roles offer fixed, coarse-grained levels of access
        - The basic roles are the Owner, Editor, and Viewer roles.
            - The owner has full administrative access. This includes the ability to add and remove members and delete projects.
            - The editor role has modify and delete access. This allows a developer to deploy applications and modify or configure its resources.
            - The viewer role has read-only access.
        - All of these roles are concentric; that is, the Owner role includes the permissions of the Editor role, and the Editor role includes the permissions of the Viewer role.
        - There is also a billing administrator role to manage billing and add or remove administrators without the right to change the resources in the project.
        - Each project can have multiple owners, editors, viewers, and billing administrators.
        
        ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%205.png)
        
    - Predefined
        - IAM predefined roles apply to a particular GCP service in a project
        - GCP services offers their own sets of predefined roles, and they define where those roles can be applied. This provides members with granular access to specific GCP resources and prevents unwanted access to other resources.
        - These roles are collections of permissions because, to do any meaningful operations, you usually need more than one permission.
        - These permissions usually align with the action’s corresponding REST API.
        
        ![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%206.png)
        
        - Compute Engine has several predefined IAM roles. Let’s look at three of those:
            - The Compute Admin role provides full control of all Compute Engine resources. This includes all permissions that start with compute, which means that every action for any type of Compute Engine resource is permitted.
            - The Network Admin role contains permissions to create, modify, and delete networking resources, except for firewall rules and SSL certificates. In other words, the network admin role allows read-only access to firewall rules, SSL certificates, and instances to view their ephemeral IP addresses.
            - The Storage Admin role contains permissions to create, modify, and delete disks, images, and snapshots.
    - Custom
        - IAM custom roles let you define a precise set of permissions
        - That’s what custom roles permit. A lot of companies use the “least-privilege” model, in which each person in your organization is given the minimal amount of privilege needed to do their job.
        - Let’s say you want to define an “Instance Operator” role to allow some users to start and stop Compute Engine virtual machines, but not reconfigure them. Custom roles allow you to do that.

### Members

**Members define the “who” part of “who can do what on which resource.”**

- There are five different types of members:
    - Google Accounts,
        - A Google account represents a developer, an administrator, or any other person who interacts with Google Cloud. Any email address that is associated with a Google account can be an identity, including [gmail.com](http://gmail.com/) or other domains. New users can sign up for a Google account by going to the Google account signup page, without receiving mail through Gmail.
    - Service Accounts,
        - A service account is an account that belongs to your application instead of to an individual end user. When you run code that is hosted on Google Cloud, you specify the account that the code should run as. You can create as many service accounts as needed to represent the different logical components of your application.
    - Google Groups,
        - A Google group is a named collection of Google accounts and service accounts. Every group has a unique email address that is associated with the group. Google groups are a convenient way to apply an access policy to a collection of users. You can grant and change access controls for a whole group at once instead of granting or changing access controls one-at-a-time for individual users or service accounts.
    - Google Workspace domains,
        - A Workspace domain represents a virtual group of all the Google accounts that have been created in an organization's Workspace account. Workspace domains represent your organization's internet domain name, such as [example.com](http://example.com/), and when you add a user to your Workspace domain, a new Google account is created for the user inside this virtual group, such as [username@example.com](mailto:username@example.com).
    - Cloud Identity domains.
        - Google Cloud customers who are not Workspace customers can get these same capabilities through Cloud Identity. Cloud Identity lets you manage users and groups using the Google Admin Console, but you do not pay for or receive Workspace’s collaboration products such as Gmail, Docs, Drive, and Calendar.

### IAM Policies

- A policy consists of a list of bindings.
- A binding binds a list of members to a role, where the members can be user accounts, Google groups, Google domains, and service accounts. A role is a named list of permissions defined by IAM.
- A policy is a collection of access statements attached to a resource.
- Each policy contains a set of roles and role members, with resources inheriting policies from their parent. Think of it like this: resource policies are a union of parent and resource, where a less restrictive parent policy will always override a more restrictive resource policy.
- The IAM policy hierarchy always follows the same path as the Google Cloud resource hierarchy, which means that if you change the resource hierarchy, the policy hierarchy also changes. For example, moving a project into a different organization will update the project's IAM policy to inherit from the new organization's IAM policy.
- Also, child policies cannot restrict access granted at the parent level. For example, if we grant you the Editor role for Department X, and we grant you the Viewer role at the bookshelf project level, you still have the Editor role for that project. Therefore, it is a best practice is to follow the principle of least privilege. The principle applies to identities, roles, and resources. Always select the smallest scope that’s necessary for the task in order to reduce your exposure to risk.
- You can also use a recommender for role recommendations to identify and remove excess permissions from your principals, improving your resources’ security configurations. Each role recommendation suggests that you remove or replace a role that gives your principals excess permissions. At scale, these recommendations help you enforce the principle of least privilege by ensuring that principals have only the permissions that they actually need. Recommender identifies excess permissions using policy insights. Policy insights are ML-based findings about permission usage in your project, folder, or organization.
- [Role recommendations: [https://cloud.google.com/iam/docs/recommender-overview](https://cloud.google.com/iam/docs/recommender-overview)]

### IAM Conditions

Enforce conditional, attribute-based access control for Google Cloud Resources

- With IAM Conditions, you can choose to grant resource access to identities (members) only if configured conditions are met. For example, this could be done to configure temporary access for users in the event of a production issue or to limit access to resources only for employees making requests from your corporate office.
- Conditions are specified in the role bindings of a resource's IAM policy. When a condition exists, the access request is only granted if the condition expression evaluates to true. Each condition expression is defined as a set of logic statements allowing you to specify one or more attributes to check.

### Organization Policies

- An organization policy is a configuration of restrictions, defined by configuring a constraint with the desired restrictions for that organization.
- An organization policy can be applied to the organization node, and all of its folders or projects within that node. Descendants of the targeted resource hierarchy node inherit the organization policy that has been applied to their parents.
- Exceptions to these policies can be made, but only by a user who has the
organization policy admin role.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%207.png)

### Single sign-on (SSO)

- If you have your identity system, you can continue using your own system and
processes with SSO configured. When user authentication is required, Google will
redirect to your system. If the user is authenticated in your system, access to Google
Cloud is given; otherwise, the user is prompted to sign in.
- If your existing authentication system supports SAML2, SSO configuration is as
simple as 3 links and a certificate, as shown on this slide. Otherwise, you can use a
third-party solution, like ADFS, Ping, or Okta.
- Google Cloud Access without Gmail : [[https://accounts.google.com/SignUpWithoutGmail?hl=en](https://accounts.google.com/SignUpWithoutGmail?hl=en)].

### Service Accounts

- A service account is an account that belongs to your application instead of to an
individual end user. This provides an identity for carrying out server-to-server
interactions in a project without supplying user credentials.
- For example, if you write an application that interacts with Google Cloud Storage, it
must first authenticate to either the Google Cloud Storage XML API or JSON API.
- You can enable service accounts and grant read-write access to the account on the
instance where you plan to run your application.
- Then, program the application to obtain credentials from the service account. Your
application authenticates seamlessly to the API without embedding any secret keys or
credentials in your instance, image, or application code.
- Service accounts are identified by an email address
    - 123845678986-compute@project.gserviceaccount.com
    - Three types of service account
        - User Craeted -Custom
        - Built In
            - Compute Engine and App Engine default service accounts
            - Default Compute Engine service account
                - Automatically created per project with auto-generated name and email address:
                    - Name has -compute suffix
                    [39xxxx0965-compute@developer.gserviceaccount.com](mailto:39xxxx0965-compute@developer.gserviceaccount.com)
                - Automatically added as a project Editor
                - By default, enabled on all instances created using gcloud or Cloud Console
        - Google API Service Accounts
            - Runs internal Google processes on your behalf

### Scopes

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%208.png)

Scopes are used to determine whether an authenticated identity is authorized.

In the example shown here, Applications A and B contain Authenticated Identities (or service accounts). Let’s assume that both applications want to use a Cloud Storage bucket. They each request access from the Google Authorization server, and in return they receive an access token. Application A receives an access token with read-only scope, so it can only read from the Cloud Storage bucket. Application B, in contrast, receives an access token with read-write scope, so it can read and modify data in the Cloud Storage bucket.

### Service Account Permissions

- Default service accounts: basic and predefined roles
- User-created service accounts: predefined roles
- Roles for service accounts can be assigned to groups or users

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%209.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2010.png)

**Keeping your user-managed keys safe is vital - and is the creator’s responsibility**

Use the gcloud command-line tool to quickly list all of the keys associated with a Service Account

```jsx
gcloud iam service-accounts keys list --iam-account user@email.com
```

### IAM Best Practices

- Leverage and understand the resource hierarchy
    - Use projects to group resources that share the same trust boundary.
    - Check the policy granted on each resource and make sure you understand the inheritance.
    - Use “principles of least privilege” when granting roles.
    - Audit policies in Cloud Audit Logs: setiampolicy.
    - Audit membership of groups used in policies.
- Grant roles to Google groups instead of individuals
    - Update group membership instead of changing IAM policy.
    - Audit membership of groups used in policies.
    - Control the ownership of the Google group used in IAM policies.
- Service accounts
    - Be very careful granting serviceAccountUser role.
    - When you create a service account, give it a display name that clearly identifies its purpose.
    - Establish a naming convention for service accounts.
    - Establish key rotation policies and methods.
    - Audit with serviceAccount.keys.list()method.
- Identity-Aware Proxy (IAP)
    - Enforce access control policies for applications and resources:
        - Identity-based access control
        - Central authorization layer for applications accessed by HTTPS
    - IAM policy is applied after authentication

# Storage and DB Services

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2011.png)

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2012.png)

### Cloud Storage

**Cloud Storage is an object storage service**

- Website content
- Storing data for archiving and disaster recovery
- Distributing large data objects to users via direct download

**Cloud Storage Key Features**

- Scalable to exabytes
- Time to first byte in milliseconds
- Very high availability across all storage classes
- Single API across storage classes

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2013.png)

**Object Cloud Storage overview**

- Buckets
    - Naming requirements
    - Cannot be nested
- Objects
    - Inherit storage class of bucket when created
    - No minimum size, unlimited storage
- Access
    - gsutil command
    - Rest API

**Changing default storage classes**

- Default class is applied to new objects.
- Regional bucket can never be changed to multi-region/dual-region.
- Multi-regional bucket can never be changed to regional.
- Objects can be moved from bucket to bucket
- Object Lifecycle Management can manage the classes of objects.

**Access Control**

- Let’s look at access control for your objects and buckets that are part of a project.
- We can use IAM for the project to control which individual user or service account can see the bucket, list the objects in the bucket, view the names of the objects in the bucket, or create new buckets. For most purposes, IAM is sufficient, and roles are inherited from project to bucket to object.
- Access control lists or ACLs offer finer control.
- For even more detailed control, signed URLs provide a cryptographic key that gives time-limited access to a bucket or object.
- Finally, a signed policy document further refines the control by determining what kind of file can be uploaded by someone with a signed URL. Let’s take a closer look at ACLs and signed URLs.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2014.png)

**Access control lists (ACLs)**

- An ACL is a mechanism you can use to define who has access to your buckets and
objects, as well as what level of access they have. The maximum number of ACL
entries you can create for a bucket or object is 100.
- Each ACL consists of one or more entries, and these entries consist of two pieces of
information:
    - A scope, which defines who can perform the specified actions (for example, a
    specific user or group of users).
    - And a permission, which defines what actions can be performed (for example,
    read or write).
- The allUsers identifier listed on this slide represents anyone who is on the internet,
with or without a Google account. The allAuthenticatedUsers identifier, in contrast,
represents anyone who is authenticated with a Google account.

**Signed URLs**

- For some applications, it is easier and more efficient to grant limited-time access
tokens that can be used by any user, instead of using account-based authentication
for controlling resource access. (For example, when you don’t want to require users
to have Google accounts).
- Signed URLs allow you to do this for Cloud Storage. You create a URL that grants
read or write access to a specific Cloud Storage resource and specifies when the
access expires. That URL is signed using a private key associated with a service
account. When the request is received, Cloud Storage can verify that the
access-granting URL was issued on behalf of a trusted security principal, in this case
the service account, and delegates its trust of that account to the holder of the URL.
- After you give out the signed URL, it is out of your control. So you want the signed
URL to expire after some reasonable amount of time.
- Example using private account key and gsutil: Example using private account key and gsutil:
    
    ```bash
    gsutil signurl -d 10m path/to/privatekey.p12
    gs://bucket/object
    ```
    

**Cloud Storage Features**

- The customer-supplied encryption key (CSEK)
    - Use your own key instead of Google-managed keys
- Object Lifecycle Management
    - Automatically delete or archive objects
    - Object Lifecycle Management policies specify actions to be performed on objects that meet certain rules
    - Here are some example use cases:
        - First, downgrade the storage class of objects older than a year to Coldline Storage.
        - Second, delete objects created before a specific date. For example, on January 1, 2017.
        - And third, keep only the 3 most recent versions of each object in a bucket with versioning enabled.
- Object Versioning
    - Maintain multiple versions of objects
    - In Cloud Storage, objects are immutable, which means that an uploaded object cannot change throughout its storage lifetime. To support the retrieval of objects that are deleted or overwritten, Cloud Storage offers the Object Versioning feature.
    - Object Versioning can be enabled for a bucket. Once enabled, Cloud Storage creates an archived version of an object each time the live version of the object is overwritten or deleted. The archived version retains the name of the object but is uniquely identified by a generation number as illustrated on this slide by g1. When Object Versioning is enabled, you can list archived versions of an object, restore the live version of an object to an older state, or permanently delete an archived version, as needed. You can turn versioning on or off for a bucket at any time. Turning versioning off leaves existing object versions in place and causes the bucket to stop accumulating new archived object versions.
- Directory synchronization
    - Synchronizes a VM directory with a bucket
- Object change notifications using Pub/Sub
    - You can configure object change notifications for Cloud Storage using Pub/Sub. Pub/Sub notifications sends information about changes to objects in your buckets to Pub/Sub, where the information is added to a Pub/Sub topic of your choice in the form of messages. For example, you can track objects that are created and deleted in your bucket. Each notification contains information describing both the event that triggered it and the object that changed. You can send notifications to any Pub/Sub topic in any project for which you have sufficient permissions. Once received by the Pub/Sub topic, the resulting message can be sent to any number of subscribers to the topic.

**Data Import Services**

The Cloud Console allows you to upload individual files to your bucket. But what if
you have to upload terabytes or even petabytes of data? There are three services that
address this: Transfer Appliance, Storage Transfer Service, and Offline Media Import.

- Transfer Appliance is a hardware appliance you can use to securely migrate large volumes of data (from hundreds of terabytes up to 1 petabyte) to Google Cloud without disrupting business operations. The images on this slide are transfer appliances.
- The Storage Transfer Service enables high-performance imports of online data. That data source can be another Cloud Storage bucket, an Amazon S3 bucket, or an HTTP/HTTPS location.
- Offline Media Import is a third party service where physical media (such as storage arrays, hard disk drives, tapes, and USB flash drives) is sent to a provider who uploads the data.

**Strong Global Consistency**

Cloud Storage provides strong global consistency

- Read-after-write
- Read-after-metadata-update
- Read-after-delete
- Bucket listing
- Object listing

**Choosing a Storage Class**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2015.png)

### Firestore

Filestore is a managed file storage service for applications

- Fully managed network attached storage (NAS) for Compute Engine and GKE instances.
- Predictable performance.
- Full NFSv3 support.
- Scales to 100s of TBs for high-performance workloads

**Use cases of Firestore**

- Using Filestore, you can expedite migration of enterprise applications. Many on-premises applications require a filesystem interface to data. As these applications continue to migrate to the cloud, Filestore can support a broad range of enterprise applications that need a shared filesystem.
- For media rendering, you can easily mount Filestore file shares on Compute Engine instances, enabling visual effects artists to collaborate on the same file share. As rendering workflows typically run across fleets (“render farms”) of compute machines, all of which mount a shared filesystem, Filestore and Compute Engine can scale to meet your job’s rendering needs.
- Electronic Design Automation (EDA) is all about data management. It requires the ability to batch workloads across thousands of cores and has large memory needs. Filestore offers the necessary capacity and scale to meet the needs of manufacturing customers doing intensive EDA and also makes sure files are universally accessible.
- Data analytics workloads include compute complex financial models or analysis of environmental data. These workloads are latency sensitive. Filestore offers low latency for file operations and, as capacity or performance needs change, you can easily grow or shrink your instances as needed. As a persistent and shareable storage layer, Filestore enables immediate access to data for high-performance, smart analytics without the need to lose valuable time on loading and off-loading data to clients’ drives.
- Genome sequencing requires an incredible amount of raw data, on the order

### Cloud SQL

Cloud SQL is a fully managed database service (MySQL, PostgreSQL, or Microsoft SQL Server)

This means that patches and updates are automatically applied but you still have to administer MySQL users with the native authentication tools that come with these databases. 

Cloud SQL supports many clients, such as Cloud Shell, App Engine and Google Workspace scripts. It also supports other applications and tools that you might be used to like SQL Workbench, Toad and other external applications using standard MySQL drivers.

**Cloud SQL Instance**

- Performance
    - 64TB of storage
    - 60000 IOPS
    - 624 GB of RAM
    - Scale out with read replicas
- Choice
    - MYSQL
    - POSTGRESQL
    - Microsoft SQL Server

**Cloud SQL Services**

- In HA configuration, within a regional instance, the configuration is made up of a primary instance and a standby instance. Through synchronous replication to each zone's persistent disk, all writes made to the primary instance are replicated to disks in both zones before a transaction is reported as committed. In the event of an instance or zone failure, the persistent disk is attached to the standby instance, and it becomes the new primary instance. Users are then rerouted to the new primary. This process is called a failover.
- Cloud SQL also provides automated and on-demand backups with point-in-time recovery.
- You can import and export databases using mysqldump, or import and export CSV files.
- Cloud SQL can also scale up, which does require a machine restart or scale out using read replicas.

**Connecting to a Cloud SQL instance**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2016.png)

**Choosing Cloud SQL**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2017.png)

### Cloud Spanner

Cloud Spanner combines the benefits of relational database structure with non-relational horizontal scale 

- Scale to petabytes
- Strong consistency
- High availability
- Used for financial and inventory applications
- Monthly uptime
    - Multi-regional: 99.999%
    - Regional: 99.99%

**Characteristics of Cloud Spanner**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2018.png)

**Cloud Spanner Architecture**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2019.png)

**Choosing Cloud Scanner**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2020.png)

### Firestore

Firestore is a NoSQL document database

- Simplifies storing, syncing, and querying data
- Mobile, web, and IoT apps at global scale
- Live synchronization and offline support
- Security features
- ACID transactions
- Multi-region replication
- Powerful query engine

**Firestore is the next generation of Datastore**

- Firestore is actually the next generation of Datastore. Firestore can operate in Datastore mode, making it backwards- compatible with Datastore. By creating a Firestore database in Datastore mode, you can access Firestore's improved storage layer while keeping Datastore system behavior.
- This removes the following Datastore limitations:
    - Queries are no longer eventually consistent; instead, they are all strongly consistent.
    - Transactions are no longer limited to 25 entity groups.
    - Writes to an entity group are no longer limited to 1 per second.
- Firestore in Native mode introduces new features such as:
    - A new, strongly consistent storage layer
    - A collection and document data model
    - Real-time updates
    - Mobile and Web client libraries
- Firestore is backward compatible with Datastore, but the new data model, real-time updates, and mobile and web client library features are not. To access all of the new Firestore features, you must use Firestore in Native mode. A general guideline is to use Firestore in Datastore mode for new server projects, and Native mode for new mobile and web apps.

**Choosing Firestore**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2021.png)

### Bigtable

Cloud Bigtable is a NoSQL big data database service

- Petabyte-scale
- Consistent sub-10ms latency
- Seamless scalability for throughput
- Learns and adjusts to access patterns
- Ideal for Ad Tech, Fintech, and IoT
- Storage engine for ML applications
- Easy integration with open source big data tools

**Cloud Bigtable storage model**

Cloud Bigtable stores data in massively scalable tables, each of which is a sorted key/value map. The table is composed of rows, each of which typically describes a single entity, and columns, which contain individual values for each row. Each row is indexed by a single row key, and columns that are related to one another are typically grouped together into a column family. Each column is identified by a combination of the column family and a column qualifier, which is a unique name within the column family. 

Each row/column intersection can contain multiple cells, or versions, at different timestamps, providing a record of how the stored data has been altered over time. Cloud Bigtable tables are sparse; if a cell does not contain any data, it does not take up any space.

//TODO: Understanding an example

**Architecture**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2022.png)

Cloud Bigtable learns to adjust to specific access patterns. If a certain Bigtable node is frequently accessing a certain subset of data Cloud Bigtable learns to adjust to specific access patterns. If a certain Bigtable node is frequently accessing a certain subset of data.

That throughput scales linearly, so for every single node that you do add, you're going to see a linear scale of throughput performance, up to hundreds of nodes.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2023.png)

**Choosing Cloud Bigtable**

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2024.png)

### Memory Store

Memorystore is a fully managed Redis service

- In-memory data store service
- Focus on building great apps
- High availability, failover, patching, and monitoring
- Sub-millisecond latency
- Instances up to 300 GB
- Network throughput of 12 Gbps
- Easy Lift-and-Shift

## Resource Management and Monitoring

### Resource Management

Resource Manager lets you hierarchically manage resources by project, folder and organization.

Policies contain a set of roles and members, and policies are set on resources. These resources inherit policies from their parent, as we can see on the left. Therefore, resource policies are a union of parent and resource. Also, keep in mind that if a parent policy is less restrictive, it overrides the more restrictive resource policy.

- Organizations contain all billing accounts
- The project is associated with one billing account
- A resource belongs to one and only project

The organization node is the root node for GCP resources

**The project accumulates the consumption of all its resources**

Because a project accumulates the consumption of all its resources, it can be used to track resources and quota usage. Specifically, projects let you enable billing, manage permissions and credentials, and enable service and APIs.

A project can be identified by: 

- The project name, which is a human-readable way to identify your projects, but it isn't used by any Google APIs.
- There is also the project number, which is automatically generated by the server and assigned to your project.
- And there is the project ID, which is a unique ID that is generated from your project name.

### Resource Hierarchy

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2025.png)

### Quotas

All resources are subject to project quotas or limits

**Why use project quotas?**

- Prevent runaway consumption in case of an error or malicious attack
- Prevent billing spikes or surprises
- Forces sizing consideration and periodic review

### Labels

Labels are a utility for organizing GCP resources

- Labels are key-value pairs that you can attach to your resources, like VMs, disks, snapshots and images.
- You can create and manage labels using the GCP console, gcloud, or the Resource Manager API, and each resource can have up to 64 labels.
- Example use of labels
    - Inventory
    - Filter resources
    - In Scripts
        - Help Analyze costs
        - Run bulk operations
- Labels vs Tags
    
    
    | Label | Tag |
    | --- | --- |
    | Labels are a way to organize resources across GCP | Tags are applied to instances
    onlyUser-defined strings in
    key-value format |
    | User-defined strings in key-value format | User-defined strings |
    | Propagated through billing | Tags are primarily used for networking (applying firewall rules) |

**Billing**

Pretty self explanatory, review pdf materials for more info

Visualize Google Cloud spend with Data Studio

### Resource Monitoring

Monitoring is important to Google because it is at the base of site reliability engineering, or SRE. SRE is a discipline that applies aspects of software engineering to operations whose goals are to create ultra-scalable and highly reliable software systems. This discipline has enabled Google to build, deploy, monitor, and maintain some of the largest software systems in the world.

**Cloud Monitoring**

- Cloud Monitoring dynamically configures monitoring after resources are deployed and has intelligent defaults that allow you to easily create charts for basic monitoring activities.
- This allows you to monitor your platform, system, and application metrics by ingesting data, such as metrics, events, and metadata.
- You can then generate insights from this data through dashboards, charts, and alerts. For example, you can configure and measure uptime and health checks that send alerts via email.

![Untitled](Essential%20Google%20Cloud%20Infrastructure%20Core%20Services%20Attachments/Untitled%2026.png)

- A Workspace is the root entity that holds monitoring and configuration information in Cloud Monitoring. Each Workspace can have between 1 and 100 monitored projects, including one or more Google Cloud projects and any number of AWS accounts. You can have as many Workspaces as you want, but Google Cloud projects and AWS accounts can't be monitored by more than one Workspace.
- A Workspace contains the custom dashboards, alerting policies, uptime checks, notification channels, and group definitions that you use with your monitored projects. A Workspace can access metric data from its monitored projects, but the metric data and log entries remain in the individual projects.
- The first monitored Google Cloud project in a Workspace is called the hosting project, and it must be specified when you create the Workspace. The name of that project becomes the name of your Workspace. To access an AWS account, you must configure a project in Google Cloud to hold the AWS Connector.
- A Workspace is a “single pane of glass” so, Determine your monitoring needs up front and Consider using separate Workspaces for data and control isolation
- Cloud Monitoring allows you to create custom dashboards that contain charts of the
metrics that you want to monitor.
- Alerting policies can notify you of certain conditions
- Uptime checks test the availability of your public services
- Cloud Monitoring can access some metrics without the Monitoring agent, including CPU utilization, some disk traffic metrics, network traffic, and uptime information. The Monitoring agent is supported for Compute Engine and EC2 instances.
- Installing Monitoring agent code
    
    ```bash
     curl -sSO https://dl.google.com/cloudagents/add-monitoring-agent-repo.sh
    sudo bash add-monitoring-agent-repo.sh
    ```
    
- Custom metrics can be created for specific needs

**Logging**

- Platform, systems, and application logs
    - API to write to logs
    - 30-day retention
- Log search/view/filter
- Log-based metrics
- Monitoring alerts can be set on log events
- Data can be exported to Cloud Storage, BigQuery, and Pub/Sub
- Logs can be analysed in BiqQuery and visualized in Data Studio
- Installing Logging agent
    
    ```bash
    curl -sSO https://dl.google.com/cloudagents/install-logging-agent.sh
    sudo bash install-logging-agent.sh
    ```
    

**Error Reporting**

Aggregate and display errors for running cloud services 

- Error notifications
- Error dashboard
- App Engine, Apps Script, Compute Engine, Cloud Functions, Cloud Run, GKE, Amazon EC2
- Go, Java, .NET, Node.js, PHP, Python, and Ruby

**Tracing**

Tracing system 

- Displays data in near real-time
- Latency reporting
- Per-URL latency sampling

Collects latency data 

- App Engine
- Google HTTP(S) load balancers
- Applications instrumented with the Cloud Trace SDKs

**Debugging**

- Cloud Debugger is a feature of Google Cloud that lets you inspect the state of a running application, in real-time, without stopping or slowing it. Specifically, the debugger adds less than 10ms to the request latency when the application state is captured. In most cases, this is not noticeable to users.
- These features allow you to understand the behavior of your code in production and analyze its state to locate those hard-to-find bugs. With just a few mouse clicks, you can take a snapshot of your running application’s state or inject a new logging statement.
- Cloud Debugger supports multiple languages, including Java, Python, Go, Node.js and Ruby