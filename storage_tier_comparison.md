# Storage Tier Comparison


![image](https://github.com/Parasharam-DevOps/Veeam-OrientTech-Mumbai/assets/132131379/d5bf9e6a-e8b3-4fdb-859e-4529072636b2)


This document provides a comparison of different storage tiers commonly used in data storage systems.

## Storage Tiers Overview

| Aspect            | Performance Tier                                        | Capacity Tier                                | Archive Tier                                      |
|-------------------|---------------------------------------------------------|----------------------------------------------|---------------------------------------------------|
| **Purpose**       | Designed for frequently accessed or actively used data  | Optimized for storing large volumes of data  | Intended for long-term retention of data         |
| **Access Speed**  | Fast access speeds and low latency                      | May have slower access speeds compared to Performance Tier | Access speed may be slower compared to other tiers |
| **Cost**          | Typically higher cost due to higher performance         | Lower cost per unit of storage               | Usually the lowest cost per unit of storage      |
| **Data Retention**| Suitable for recent backups or frequently accessed data | Primary storage for backup data not actively accessed | Long-term retention of data for compliance or archival purposes |
| **Storage Media** | Often utilizes high-performance disk storage            | Utilizes disk storage optimized for capacity | Can use low-cost storage options such as tape or cloud-based object storage |
| **Data Usage**    | Ideal for applications/workloads requiring quick access to data | Suitable for less frequently accessed data | Data is rarely accessed, primarily for compliance or archival purposes |
| **Backup Strategy**| Often used for initial backup storage and quick restores | Stores backup data not actively accessed, optimizing performance | Stores backup data for long-term retention, infrequently accessed |
| **Scalability**   | May have limitations due to higher cost and performance requirements | Easily scalable to accommodate growing data volumes | Easily scalable to meet long-term retention needs |
| **Examples**      | SSDs, high-performance disk arrays                     | NAS, lower-performance disk arrays           | Tape libraries, cloud object storage services    |

## Examples

| Storage Tier     | Examples                                     |
|------------------|----------------------------------------------|
| Performance Tier | SSDs, high-performance disk arrays           |
| Capacity Tier    | NAS, lower-performance disk arrays           |
| Archive Tier     | Tape libraries, cloud object storage services|
