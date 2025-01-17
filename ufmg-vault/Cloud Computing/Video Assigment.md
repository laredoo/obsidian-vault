#cloud-computing 
## What was the previous established solution before the creation/adoption of the solution discussed in the video?

### **EBS:**

 **On-Premises and Legacy Solutions**

1. **Direct-Attached Storage (DAS)**
    
    - **Description:** Storage devices (e.g., hard drives, SSDs) were physically attached to individual servers.
    - **Limitations:**
        - Not scalable beyond the server’s physical capacity.
        - Storage tied directly to hardware, limiting flexibility and portability.
        - Downtime required for upgrades or repairs.
2. **Network-Attached Storage (NAS)**
    
    - **Description:** Centralized file storage systems accessible over a network (e.g., NFS, SMB protocols).
    - **Limitations:**
        - File-based storage (not block-based), making it less suitable for high-performance, transactional workloads like databases.
        - Network bottlenecks could degrade performance.
3. **Storage Area Networks (SAN)**
    
    - **Description:** High-speed, dedicated networks providing block storage to multiple servers.
    - **Limitations:**
        - High cost and complexity of setup and management.
        - Lack of elasticity; scaling required manual provisioning and expensive hardware upgrades.
        - Vendor lock-in due to proprietary protocols and hardware.
4. **Physical Disk Arrays**
    
    - **Description:** Enterprise disk arrays provided shared storage for data centers.
    - **Limitations:**
        - Rigid, on-premises infrastructure with limited scalability.
        - Maintenance and upgrades required downtime and significant investment.

**Cloud-Based Solutions Before AWS EBS**

- **Ephemeral Instance Storage**
    
    - **Description:** Before EBS, AWS EC2 instances relied on ephemeral storage, which was local to the instance and non-persistent (data was lost when the instance was stopped or terminated).
    - **Limitations:**
        - Lack of durability and persistence.
        - Could not detach storage and reattach it to another instance.
        - Not suitable for applications requiring reliable data retention, such as databases.
- **Amazon S3 (Simple Storage Service)**
    
    - **Description:** Object storage for scalable and durable data storage.
    - **Limitations:**
        - Not block storage; unsuitable for low-latency or transactional workloads.
        - Limited use cases for applications needing a file system-like interface or block-level storage.

## What are the origins of the solution? How was it created and adopted? What pushed its adoption? What are the challenges addressed by the solution? Why was it created?**

**EBS:** It's origin was the need for **persistent volumes**. Since the data in EC2 instances are ephemerous, there was a need for persistant data.

**S3:**
## How is the solution used in practice? Are there large notable use-cases? Who or what benefits from the solution?

### **EBS:**

**How AWS EBS is Used in Practice**

- **Persistent Storage for EC2 Instances**  
	EBS volumes are attached to EC2 instances to provide persistent, durable, and scalable storage for applications. Unlike ephemeral instance storage, EBS persists even after an instance is stopped or terminated.

- **Database Storage**  
	EBS is frequently used to store data for relational (e.g., MySQL, PostgreSQL) and non-relational databases (e.g., MongoDB, Cassandra). Its high performance and throughput options make it suitable for transactional workloads

**Large, Notable Use-Cases**

- **Netflix**  
    Netflix uses AWS extensively for its global content delivery. EBS plays a role in enabling high-throughput and low-latency data storage for streaming services and analytics.
    
- **Airbnb**  
    Airbnb relies on AWS EBS to store and manage databases, analytics systems, and backups, providing scalability and reliability for their data-heavy operations.

**Who or What Benefits from AWS EBS?**

- **Developers**  
    EBS provides a reliable, easy-to-use storage solution for application development, testing, and deployment. Features like snapshots and encryption simplify operational management.
    
- **Organizations with Large-Scale Data Needs**  
    Businesses that handle large amounts of structured and unstructured data, such as financial firms, healthcare providers, and e-commerce platforms, benefit from EBS's scalable storage and high performance.

## How does the solution work? What are the main ideas behind it? What are its limitations?

### **EBS:**

**How AWS EBS Works**

- **Block Storage Architecture**  
    EBS is a block storage system, meaning data is stored in fixed-sized blocks rather than files or objects. This makes it ideal for workloads requiring frequent, low-latency read/write access, such as databases and transactional systems.
    
- **Volume Creation and Attachment**
    
    - **Volumes:** Users create EBS volumes specifying size, type, and availability zone.
    - **Attachment:** Volumes are attached to EC2 instances, appearing as local drives for applications.
    - **Persistence:** Data persists independently of EC2 instance life cycles.

**Main Ideas Behind AWS EBS**

- **Separation of Storage and Compute**  
    EBS volumes are independent of EC2 instances, allowing them to be attached/detached and reused across instances.
    
- **Replication for Durability**  
    Data is replicated within the same AZ for durability, ensuring resilience against disk failures.
    
- **Elasticity and Pay-as-You-Go**  
    Customers pay only for what they use, with options to scale up or down based on requirements.

**Limitations of AWS EBS**

- **AZ-Specific Scope**
    
    - EBS volumes are limited to a single availability zone. Cross-AZ usage requires copying data or using services like Amazon FSx.
- **Performance Degradation**
    
    - Performance can degrade during burst limits on gp2 volumes or due to noisy neighbors in shared infrastructure.
    - IOPS and throughput are limited by the EC2 instance type.

**Recent Developments in AWS EBS**

- **Introduction of gp3 Volumes**

	- gp3 volumes allow users to customize performance (IOPS and throughput) independently of volume size, offering cost savings and better performance.

## What are recent developments and what does the future hold for the solution?

### **EBS:**

-  **Cross-Region and Cross-AZ Replication**  
    Enhanced support for native cross-region or cross-AZ replication could improve disaster recovery options and broaden EBS use cases.
    
-  **Integration with Machine Learning and Big Data Workloads**  
    As ML and analytics demand grows, EBS may further optimize performance and integration with tools like SageMaker, Redshift, and EMR.
    
-  **Cost Optimization Features**  
    Expect AWS to offer more cost-saving measures, such as tiered pricing models or further performance-cost decoupling.
    
-  **Serverless Storage Integration**  
    Increased support for serverless architectures could emerge, enabling EBS to support ephemeral yet performant serverless workloads.
    
-  **Improved Backup and Restore Speeds**  
    Enhancements in snapshot speeds and cost efficiency will make backups and disaster recovery more attractive for large-scale users.
