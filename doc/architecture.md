# architecture

## Master
Raspberry Pi 3 Model B

Currently runs etcd as well, which probably is too much work for a Pi3b

## Workers

### Storage

6 * 3T disk machine.

nfs-provisioner is running on this machine (using a storage label), and supplies
persistent volumes and persistent volume claims

### General purpose

There are currently 3 worker nodes, not including the master, but including the
storage node. Each has 256G SSD for local storage. The machines, as of time of
writing are:

- An Intel i5 NUC
- A 2013 i7 laptop
- A 2008 Phenom II (the storage node)
