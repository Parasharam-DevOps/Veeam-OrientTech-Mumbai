# Veeam solution components

**Backup server**

* The Veaam Backup server (VBR) is a Windows®-based server on which Veeam Backup and Replication is installed.
* VBR is the core component in the backup infrastructure that coordinates and manages the configuration and interaction of the other components of the system.
* The VBR is backed by the MS SQL 2016 database, which holds the metadata.


**Backup proxy**

* The Veeam proxy is a component that `sits between the backup server` and the other components of the backup infrastructure, `such as storage repository`.
* The VBR server administers the individual backup tasks, the proxy processes these jobs and delivers the backup traffic.
* The Veeam Proxy is the high-performance data mover in the Veeam system.
* The Veeam proxy connects to the customer ESXi™ hypervisor and `transfers data between the hypervisor and the various Veeam components` as needed.This transfer can be to the local storage repository (local backup) or to a remote proxy (backup copy job or VM DR replication)

**Backup repository**

A backup repository is a storage location where Veeam keeps backup files, and it can be one of the following storage components:

* Direct attached storage - Microsoft Windows or Linux servers with volumes attached.
* Object storage - It can be manually configured as a capacity tier in a scale-out backup repository.
* Network-attached storage - It can be manually configured to provide SMB/CIFS shares or NFS shares.

  After provisioning, the Veeam service instance has two repositories that are automatically configured:
* IC4V Default VM Backup Repository - Used for backing up the configuration database.
* IC4V Default Config Backup Repository - Used as an extant of the IC4V Scale-Out Repository performance tier.


**Scale-out backup repository**

* A scale-out backup repository consists of one or more backup repositories that are called the `performance tier`.
* It can be expanded with object storage repositories for long-term and archive storage that is known as capacity tier and `archive tier`.
* A scale-out backup repository enables horizontal scaling support for multitier storage of data.

**Mount Server**

* A mount server is a component on a Windows based managed server, which is required for restores of guest OS files, application items, or secure restore.
* The Veeam backup file is mounted by the mount server so that the files can be copied to the restore destination.
* The mount server must be in the same location as the backup repository where backup files are stored to enable the best performance.


![image](https://github.com/Parasharam-DevOps/Veeam-OrientTech-Mumbai/assets/132131379/fe35e05c-b009-4096-ad7a-04f7bf33531f)





# Resource
[IBM-Blog-Link](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-veeam-bms-archi-components)
[IBM-Blog-Link](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-veeam-cr-sa-components)
