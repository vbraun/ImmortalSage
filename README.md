ImmortalSage
============

Introduction
------------

This is a script to help make a computation run forever, even if you
need to reboot your computer. This works by making generational
snapshots (by default: daily, weekly, and yearly) of a KVM virtual
machine and restarting it as necessary. The script is meant to be run
from cron periodically (say, hourly).

Each time the script runs,
 
* The virtual machine is restarted from the latest snapshot if
  it is not running.

* Any snapshot that is older than its configured maximum age is
  updated.


Configuration
-------------

To configure it see the comments at the top of the script.


Creating the Virtual Machine
----------------------------

Snapshots require a suitable image file format, recommended is
qcow2. For example, to create a new vm in the default storage pool
just run

```
virt-install --name="ImmortalSageWorker" --ram=4096 --vcpus=8 --hvm \
    --disk pool=default,size=5,format=qcow2 \
    --cdrom=/mnt/ultrabay/vbraun-data/Fedora-17-x86_64-DVD.iso
```


Requirements
------------

For Fedora:

    yum install virt-viewer virt-manager libvirt-python



    