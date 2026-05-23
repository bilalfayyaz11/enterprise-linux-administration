# Enterprise Linux Disk Partitioning and Persistent Storage Management

## What This Does

This work demonstrates enterprise Linux storage administration on a modern cloud-based NVMe disk. It covers disk discovery, GPT partition creation, filesystem provisioning, filesystem labeling, manual mounting, persistent mounting through `/etc/fstab`, and recovery from common partitioning and mount configuration failures.

The workflow reflects real infrastructure operations where Linux engineers provision additional block storage for application data, logs, databases, backup paths, or workload-specific storage. It also documents troubleshooting around raw partitions, incorrect sector input, missing filesystems, and invalid fstab entries.

## Architecture

```text
+------------------------------------------------------+
|              Enterprise Linux Cloud Host             |
+------------------------------------------------------+
| Root Disk                                             |
| /dev/nvme0n1                                         |
| ├── /boot                                            |
| └── /                                                |
+------------------------------------------------------+
| Practice Data Disk                                   |
| /dev/nvme1n1                                         |
| ├── /dev/nvme1n1p1  ext4  DATA_EXT4  -> /mnt/data1   |
| └── /dev/nvme1n1p2  xfs   DATA_XFS   -> /mnt/data2   |
+------------------------------------------------------+
| Persistent Mount Control                             |
| /etc/fstab                                           |
+------------------------------------------------------+
