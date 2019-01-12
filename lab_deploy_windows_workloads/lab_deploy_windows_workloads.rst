.. _lab_deploy_windows_workloads:

--------------------------------
AHV: Deploying Windows Workload
--------------------------------

Overview
++++++++

Learn about basic VM deployment.

Creating a Windows VM
+++++++++++++++++++++

Deploy a Windows VM from Prism Central.

.. note::

  Nutanix provides a set of guest tools and drivers comparable to VMware Tools. To install a Windows-based OS, the I/O drivers must be provided at install time. Nutanix provides a customized set of virtualized I/O drivers for Windows OS on AHV.

In **Prism Central > Explore > VMs**, click **Create VM**.

Basic Configuration
................

Fill out the following fields:

- **Name** - Windows_VM-*initials*
- **Description** - (Optional) Description for your VM.
- **vCPU(s)** - 2
- **Number of Cores per vCPU** - 1
- **Memory** - 4 GiB

Configuring the Disks
................

- 1) Select :fa:`pencil` next to CDROM
      - **Operation** - Clone from Image Service
      - **Image** - Windows2012R2.iso*
      - Select **Update**
      - IMPORTANT: Select the radio button next to the CDROM under the **"Boot Device"** column!

- 2) Select **+ Add New Disk**
      - **Type** - CDROM
      - **Operation** - Clone from Image Service
      - **Image** - Nutanix VirtIO
      - Select **Add**

- 3) Select **+ Add New Disk**
      - **Type** - DISK
      - **Operation** - Allocate on Storage Container
      - **Storage Container** - Default Container
      - **Size (GiB)** - 30 GiB
      - Select **Add**

Add a vNIC
................

- Select **Add New NIC**
- **VLAN Name** - Primary
- Select **Add**

Click **Save** to create the VM.


Now let's power on the VM:

Select the VM, then click **Power On** in blue below the VM table.


Next let's open a console session:

Select the VM, then click **Launch Console** from the **Actions** drop-down menu.

Progress through the standard install questions until you reach the Windows install location.

.. note::
  Choose **Datacenter with GUI** and **Custom** installation when presented with the choice.

Click **Load Driver** and navigate to the CD where the Nutanix VirtIO is mounted.

Browse the CD, and select the directory that corresponds to the Windows OS being installed.

.. figure:: images/deploy_workloads_05.png

.. figure:: images/deploy_workloads_06.png

Select the three Nutanix drivers displayed **(Press and hold the Ctrl key and select all three drivers):**

- Balloon
- Ethernet adapter
- SCSI passthrough controller

.. figure:: images/deploy_workloads_07.png

Click Next.

After the drivers are loaded, the disk created in step 1 appears as an installation target. Select that disk and continue with the normal install process.

After the installation completes, the Windows install ISO can be unmounted and the additional CD-ROM used for the drivers can be removed from the VM.

.. note::

  In ESXi:

  - After a VM is created via VMware vSphere, it appears in the Prism VMs list.
  - Alternatively, if a VM is created via Prism, it appears in the VMware vSphere UI. An example is shown in the image below.
  .. figure:: images/deploy_workloads_08.png

Takeaways
+++++++++

- In this lab you saw how simple it is to deploy a Windows VM from a managed Windows Server ISO in the Image Catalogue.
