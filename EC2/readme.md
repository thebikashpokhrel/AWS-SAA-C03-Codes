## Overview of EC2

- EC2 = Elastic Compute Cloud
- Provides on-demand, scalable computing capacity in the Amazon Web Services (AWS) Cloud.
- Pay for what you use model
- EC2 is an Infrastructure as a Service (IaaS)
- Can use Amazon EC2 to launch as many or as few virtual servers as needed, configure security and networking, and manage storage.
- EC2 Instance = Computer + Memory + Network + Storage
- EC2 can be bootstrapped (launching command when machine starts) using **EC2 User Data.**
- Runs only once when instance first starts
- Useful for installing updates, software, files from internet.
- Script runs with root user
- **Features of EC2:**
  - **Instances :** Virtual Servers
  - **Amazon Machine Images(AMIs):** Preconfigured templates for your instances that package the components you need for your server (including the operating system and additional software).
  - **Instance Types:** Various configurations of CPU, memory, storage, networking capacity, and graphics hardware for your instances.
  - **Amazon EBS Volumes:** Persistent storage volumes for your data using Amazon Elastic Block Store (Amazon EBS).
  - **Instance Store Volumes:** Storage volumes for temporary data that is deleted when you stop, hibernate, or terminate your instance.
  - **Key Pairs:** Secure login information for your instances. AWS stores the public key and you store the private key in a secure place.
  - **Security Groups:** A virtual firewall that allows you to specify the protocols, ports, and source IP ranges that can reach your instances, and the destination IP ranges to which your instances can connect.

## Amazon Machine Image - AMI

- An image that provides the software that is required to set up and boot an Amazon EC2 instance.
- You can use an AMI provided by AWS, a public AMI, an AMI that someone else shared with you, or an AMI that you purchased from the AWS Marketplace.

## Instance Types

Naming convention: M5.2Xlarge => m = instance class, 5 = generation and 2xlarge = size within instance class.

- **General purpose:** General purpose instances provide a balance of compute, memory and networking resources, and can be used for a variety of diverse workloads. These instances are ideal for applications that use these resources in equal proportions such as web servers and code repositories.
  Use Cases: Applications built on open-source software such as application servers, microservices, gaming servers, midsize data stores, and caching fleets.
  M5 | M5a | M5ad | M5d | M5dn | M5n | M5zn | M6a | M6g | M6gd | M6i | M6id | M6idn | M6in | M7a | M7g | M7gd | M7i | M7i-flex | Mac1 | Mac2 | Mac2-m1ultra | Mac2-m2 | Mac2-m2pro | T2 | T3 | T3a | T4g
- **Compute optimized:** Compute Optimized instances are ideal for compute bound applications that benefit from high performance processors. Instances belonging to this category are well suited for batch processing workloads, media transcoding, high performance web servers, high performance computing (HPC), scientific modeling, dedicated gaming servers and ad server engines, machine learning inference and other compute intensive applications.
  C5 | C5a | C5ad | C5d | C5n | C6a | C6g | C6gd | C6gn | C6i | C6id | C6in | C7a | C7g | C7gd | C7gn | C7i | C7i-flex
- **Memory optimized:** Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory.
  Use Cases: Memory-intensive workloads such as open source databases, in-memory caches, and real-time big data analytics.
  R5 | R5a | R5ad | R5b | R5d | R5dn | R5n | R6a | R6g | R6gd | R6i | R6idn | R6in | R6id | R7a | R7g | R7gd | R7i | R7iz | R8g | U-3tb1 | U-6tb1 | U-9tb1 | U-12tb1 | U-18tb1 | U-24tb1 | U7i-12tb | U7in-16tb | U7in-24tb | U7in-32tb | X1 | X2gd | X2idn | X2iedn | X2iezn | X1e | z1d
- **Storage optimized:** Storage optimized instances are designed for workloads that require high, sequential read and write access to very large data sets on local storage. They are optimized to deliver tens of thousands of low-latency, random I/O operations per second (IOPS) to applications.
  Use Cases: High frequency online transaction processing (OLTP) systems, Relational & NoSQL databases, Cache for in-memory databases (for example, Redis), Data warehousing applications, Distributed file systems
  D2 | D3 | D3en | H1 | I3 | I3en | I4g | I4i | Im4gn | Is4gen
- **Accelerated computing:** Accelerated computing instances use hardware accelerators, or co-processors, to perform functions, such as floating point number calculations, graphics processing, or data pattern matching, more efficiently than is possible in software running on CPUs.
  Use Cases: Generative AI applications, including question answering, code generation, video and image generation, speech recognition, and more.
  DL1 | DL2q | F1 | G4ad | G4dn | G5 | G5g | G6 | G6e | Gr6 | Inf1 | Inf2 | P2 | P3 | P3dn | P4d | P4de | P5 | P5e | Trn1 | Trn1n | VT1
- **High-performance computing:** High performance computing (HPC) instances are purpose built to offer the best price performance for running HPC workloads at scale on AWS. HPC instances are ideal for applications that benefit from high-performance processors such as large, complex simulations and deep learning workloads.

  Hpc6a | Hpc6id | Hpc7a | Hpc7g

- **AWS Compute Optimizer** provides Amazon EC2 recommendations. To make recommendations, Compute Optimizer analyzes your existing instance specifications and utilization metrics. The compiled data is then used to recommend which Amazon EC2 instance types are best able to handle the existing workload. Recommendations are returned along with per-hour instance pricing.

## EC2 Storage Options

### Network Attached (EBS and EFS)

**EBS - Elastic Block Storage**

- High performance per instance block storage
- Accessible to single instance only more like a physical hard drive
- With AWS EBS Multi Attach, single EBS volume can be attached to multiple ec2 instances (upto 16 instances)
- EBS Instance can be either SSD for general purpose or provisioned IOPS(IO Operations Per second) SSD for mission critical loads.
- EBS handles encryption

**EFS - Elastic File System**

- Can be mounted by multiple EC2 instances
- Scalability - can grow or shrink according to the demand
- Can cross AWS region boundary through VPC peering
- Useful for shared high performance storage option

### Hardware(EC2 Instance Store)

**EC2 Instance Store**

- Temporary block level storage for EC2 instance
- Provided by disks that are physically attached to host computer
- Instance stores are ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content.
- It can also be used to store temporary data that you replicate across a fleet of instances, such as a load-balanced pool of web servers.
