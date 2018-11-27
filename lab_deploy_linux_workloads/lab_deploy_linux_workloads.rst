.. _lab_deploy_linux_workloads:

------------------------------
Lab - Deploying Linux Workload
------------------------------

Overview
++++++++

Learn about basic VM deployment.

Creating a Linux VM
+++++++++++++++++++

Deploy a Linux VM from Prism Central.

In **Prism Central > Explore > VMs**, click **Create VM**.

Fill out the following fields and click **Save**:

- **Name** - Linux_VM-*initials*
- **Description** - (Optional) Description for your VM.
- **vCPU(s)** - 1
- **Number of Cores per vCPU** - 1
- **Memory** - 2 GiB

.. figure:: images/deploy_workloads_03.png

- Select :fa:`pencil` next to CDROM
    - **Operation** - Clone from Image Service
    - **Image** - CentOS7-*initials* (The Image we added above)
    - Select **Update**

.. figure:: images/deploy_workloads_04.png

- Select **+ Add New Disk**
    - **Type** - DISK
    - **Operation** - Allocate on Storage Container
    - **Storage Container** - Default Container
    - **Size (GiB)** - 30 GiB
    - Select **Add**

- Select **Add New NIC**
    - **VLAN Name** - Primary
    - Select **Add**

Click **Save** to create the VM.

Takeaways
+++++++++

- In this lab you saw how simple it is to deploy a Linux VM.
