.. _files_nfs_export:

------------------------
Files: Create NFS Export (Linux)
------------------------

Overview
++++++++

.. note::

  This lab is for **Linux Virtual Machines**

  Ask the Instructor for the name of the File Server, as it has already been created for you.

In this exercise you will use Files to configure an NFS share.

Configuring NFS Export
+++++++++++++++++++

In **Prism > File Server**, click **+ Share/Export**. Fill out the following fields and click **Next**:

- **Name** - logs-*intials*
- **Protocol** - NFS
- **Share/Export Type** - Non-Sharded Directories

.. figure:: images/files_nfs_001.png

Fill out the following fields and click **Create**:

- **Authentication** - System
- **Default Access** - No Access
- Select **+ Add Client Exceptions**
- **Clients with Read-Write Access** - *<Cluster IP Range>* (ex. 10.21.XX.*)

.. figure:: images/files_nfs_002.png

Connect to NFS Export
+++++++++++++++++++

Install NFS Client & Mount NFS Export
.....................................

.. note::

  Instructor may have different **File Server** Name If So, see whiteboard.

Locate your VM, click **Launch Console** and log in as **root** or connect via SSH.

Execute the following:

  .. code-block:: bash

    [root@CentOS ~]# yum install -y nfs-utils
    [root@CentOS ~]# mkdir /filesmnt
    [root@CentOS ~]# mount.nfs4 *intials*-Files.ntnxlab.local:/ /filesmnt/
    [root@CentOS ~]# df -kh
    Filesystem                      Size  Used Avail Use% Mounted on
    /dev/mapper/centos_centos-root  8.5G  1.7G  6.8G  20% /
    devtmpfs                        1.9G     0  1.9G   0% /dev
    tmpfs                           1.9G     0  1.9G   0% /dev/shm
    tmpfs                           1.9G   17M  1.9G   1% /run
    tmpfs                           1.9G     0  1.9G   0% /sys/fs/cgroup
    /dev/sda1                       494M  141M  353M  29% /boot
    tmpfs                           377M     0  377M   0% /run/user/0
    *intials*-Files.ntnxlab.local:/             1.0T  7.0M  1.0T   1% /filesmnt
    [root@CentOS ~]# ls -l /filesmnt/
    total 1
    drwxrwxrwx. 2 root root 2 Mar  9 18:53 logs-*intials*

Observe that the **logs** directory is mounted in ``/filesmnt/logs-*intials*``.

Reboot the VM and observe the export is no longer mounted. To persist the mount, add it to ``/etc/fstab`` by executing the following:

  .. code-block:: bash

    echo '*intials*-Files.ntnxlab.local:/logs-*intials* /filesmnt nfs4' >> /etc/fstab

The following command will add 100 2MB files filled with random data to ``/filesmnt/logs``:

  .. code-block:: bash

    for i in {1..100}; do dd if=/dev/urandom bs=8k count=256 of=/filesmnt/logs-*intials*/file$i; done

Return to **Prism > File Server > Share > logs** to monitor performance and usage.

.. figure:: images/files_nfs_003.png

Takeaways
+++++++++

- In this lab, you easily utilized Nutanix Files to create an NFS Share, and mount it in Linux. 
