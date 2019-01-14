.. _flow_secure_app:

----------------
Flow: Securing Apps
----------------

Overview
++++++++

.. note::

  In this lab, you will use the VM's you cloned from the **AHV: Managing Workloads** lab. The naming prefix used for those clones was **flow-<initials>-clone#**

  Make sure you are using *your* VM's to prevent interference with other lab users.

In this exercise you will create an Application Category. You will assign the Category to our Application VM, and finally you will create a security policy to restrict the application VM from receiving ICMP ping requests from VMs outside of the Category.

Secure Apps with Microsegmentation
++++++++++++++++++++++++++++++++++++++++++

Create and Assign Categories
............................

Update the New Category Value
------------------------------------------------------

Log on to the Prism Central environment and navigate to **Explore > Categories**.

Click the check box beside **AppType**. Click **Actions > Update**.

Scroll down and click the plus sign beside the last entry.

Enter **app-<initials>**, and click **Save**.


Assign the VM to the Category
--------------------------------------------------------------

Within the **Explore > VMs** view in Prism Central, click the check box beside the **flow-<initials>-clone5** VM.

Click **Actions > Manage Categories**.

In the Set Categories text box, type **AppType** and select **AppType: app-<initials>** from autocomplete then click **Save**.

.. figure:: images/set_app_category.png


Assign a VM to a Default Category
------------------------------------------------------------------

Within the **Explore > VMs** view in Prism Central, click the check box beside the **flow-<initials>-clone1** VM.

Click **Actions > Manage Categories**.

In the Set Categories text box, type **Dev** and select **Environment: Dev** from autocomplete then click **Save**.

Secure the Application VM
.........................

Create a Security Policy to protect the Application
--------------------------------------------------------------------

Navigate to **Explore > Security Policies**.

Click **Create Security Policy > Secure an Application**.

Fill out the following fields and click **Next**:

- **Name** - Protect-app-*<initials>*
- **Purpose** - Protect app-*<initials>* from ICMP outside of sales VMs.
- **Secure this app** - AppType: app-*<initials>*
**Do NOT** select the check box for the option **Filter the app type by category**.

.. figure:: images/create_app_vm_sec_pol.png

In the Inbound rules section, allow incoming traffic with the following steps:

- Leave **Whitelist Only** selected.
- Select **+ Add Source**.
- Leave **Add source by: Category** selected.
- Type **sales** and select **programs-<initials>:sales-<initials>**. Click Add.

Click + which appears on the left side of **AppType: app-<initials>** after completing the steps above.

This opens the Create Inbound Rule window.

In the Protocol column, select **ICMP** to allow inbound ping requests for this app and leave all other fields blank. Click **Save**.

On the right side, **Outbound** should be set to **Allow All**. You should see **All Destinations**.

.. figure:: images/create_inbound_rule.png

Click **Next** then click **Save and Monitor**.

Confirm that VMs belonging to the **programs-<initials>:sales-<initials>** category can ping the application VM which belongs to the **AppType: app-<initials>** category.

Navigate to **Explore > VMs** and open the console window for the following three VMs:

- The designated AppType: app-*<initials>* VM, **flow-<initials>-clone5**.
- The Sales VM (a VM in the programs-<initials>:sales-<initials> category, **flow-<initials>-clone4**).
- The Dev VM (a VM in Environment: Dev, **flow-<initials>-clone1**).

Send a ping from the Sales VM (clone4) to the AppType: app-<initials> VM (clone5).

This ping request **should** succeed.

Send a ping from the Dev VM (clone1) to the AppType: app-<initials> VM (clone5).

This ping also succeeds, even though Environment: Dev is not part of the allowed policy. **Why? What is the policy Status?**

Takeaways
+++++++++

- You created a category to protect a special application VM. Then you created the security policy to restrict ICMP traffic into that application VM.
- Notice that the policy created is in **Save and Monitor** mode, which means traffic is not actually going to get blocked yet until the policy is applied. This is helpful in order to study the connections and ensure no true traffic is getting blocked unintentionally.
