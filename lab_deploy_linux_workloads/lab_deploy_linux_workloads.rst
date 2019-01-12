.. _lab_deploy_linux_workloads:

------------------------------
AHV: Deploying Linux Workload
------------------------------

Overview
++++++++

Learn about basic VM deployment.

Creating a Linux VM
+++++++++++++++++++

Deploy a Linux VM from Prism Central.

In **Prism Central > Explore > VMs**, click **Create VM**.

Fill out the following fields:

- **Name** - Linux_VM-*initials*
- **Description** - (Optional) Description for your VM.
- **vCPU(s)** - 1
- **Number of Cores per vCPU** - 1
- **Memory** - 2 GiB

.. figure:: images/deploy_workloads_03.png

- Select **+ Add New Disk**
      - **Type** - DISK
      - **Operation** - Clone from Image Service
      - **Image** - CentOS7.qcow2
      - **Index** - Next Available
      - Select **Add**
      - IMPORTANT: Select the radio button next to the DISK under the **"Boot Device"** column!

- Select **Add New NIC**
    - **VLAN Name** - Primary
    - Select **Add**

Click **Save** to create the VM.

Select your VM in Prism Central and Select **Power On** (The VM will be powered off by default)

Takeaways
+++++++++

- In this lab you saw how simple it is to deploy a Linux VM in Prism Central. Note that it will receive an IP address automatically from the managed Primary network.
