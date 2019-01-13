.. _flow_quarantine_vm:

-------------------
Flow: Quarantine a VM
-------------------

Overview
++++++++

.. note::

  In this lab, you will use the VM's you cloned from the **AHV: Managing Workloads** lab. The naming prefix used for those clones was **flow-<initials>-clone#**

  Make sure you are using *your* VM's to prevent interference with other lab users.

In this task we will place a VM into quarantine and observe the behavior of the VM. We will also inspect the configurable options inside the quarantine policy.

Quarantine a VM and Explore the Quarantine Policy
+++++++++++++++++++++++++++++++++++++++++++++++++

Confirm VM Communication
.......................................................

Log on to the Prism Central environment and navigate to **Explore > VMs**.

Open the VM console of your cloned VM's from earlier, **flow-<initials>-clone1** and **flow-<initials>-clone2** by selecting one VM at a time and clicking on the checkbox next to it.

Click **Actions > Launch Console**.

.. figure:: images/quarantine_pings.png

Log into both VMs. For Linux VM's:

- **Username** - root
- **Password** - nutanix/4u

For Windows VM's:

- **Username** - Administrator
- **Password** - nutanix/4u

Find the IPs of the VMs via Prism Central or by checking them in the console, and start a continuous ping from the **flow-<initials>-clone1** VM to the **flow-<initials>-clone2** VM.

Using The Quarantine Policy
..............................................

Quarantine the **flow-<initials>-clone2** VM by navigating to **Explore > VMs**.

Select **flow-<initials>-clone2 > Actions > Quarantine VMs**. Select **Forensic** and click **Quarantine**.

.. figure:: images/select_forensic.png

What happens with the continuous ping between VMs 1 and 2?

Navigate to **Explore > Security Policies > Quarantine**.

Select **Update** in the top right corner then select **+ Add Source** to the Quarantine policy.

Add a source by **Subnet/IP** with the IP address of **flow-<initials>-clone1**, a netmask of **/32**. Click on the plus sign ( + ) near **Forensic** category and allow any protocol on any port to the Forensic quarantine category.

What targets can this source be connected to?

What is the difference between the Forensic and Strict quarantine mode?

Select **Next > Apply Now** to save the policy.

What happens to the pings between **flow-<initials>-clone1** and **flow-<initials>-clone2** after the source is added?

Unquarantine **flow-<initials>-clone2** by navigating to **Explore > VMs > flow-abc-2 > Actions > Unquarantine VM**.

Takeaways
+++++++++

- In this exercise you utilized Flow to quarantine a VM in the environment using the two modalities of the quarantine policy, which are strict and forensic.
- The forensic modality is key in allowing you to study the connection patterns into and out of a VM in order to establish which connections are allowed or denied while the VM is quarantined.
