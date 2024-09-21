# Storage and Backups Key Points

- EFS (Elastic File System) is a fully managed, auto scalable, and elastic Network File System (NFS) storage service provided by AWS.
- It’s like having a shared drive in the cloud that multiple instances can access concurrently.
- EFS is regional service meaning it can be used across multiple AZs
- EBS volumes must be in the same AZ as the instances they are attached to. So you cannot share an EBS across AZs. Unless you plan to have two separate volumes in each AZ, the simpliest solution is to use EFS as a shared file system

- On a Snowball Edge device you can copy files with a speed of up to 100Gbps. 70TB will take around 5600 seconds, so very quickly, less than 2 hours. The downside is that it'll take between 4-6 working days to receive the device and then another 2-3 working days to send it back and for AWS to move the data onto S3 once it reaches them. Total time: 6-9 working days. Bandwidth used: 0.

- S3 File gateway connects on-premise application to S3 cloud. Can be deployed on-premise as virtual machine.

- It provides a way to store files in Amazon S3 via standard file protocols (NFS/SMB) while keeping frequently accessed data cached locally for fast access.
