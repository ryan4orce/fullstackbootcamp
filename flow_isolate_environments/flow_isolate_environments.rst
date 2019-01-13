.. _flow_isolate_environments:

--------------------------
Flow: Isolate Environments
--------------------------

Overview
++++++++

.. note::

  In this lab, you will use the VM's you cloned from the **AHV: Managing Workloads** lab. The naming prefix used for those clones was **flow-<initials>-clone#**

  Make sure you are using *your* VM's to prevent interference with other lab users.

In this exercise you will create a category with different values. Then you will create and implement an isolation security policy that uses the newly created category in order to restrict unauthorized access.

Isolate Environments with Flow
++++++++++++++++++++++++++++++

Create a New Category
.....................

Log on to the Prism Central environment and navigate to **Explore > Categories**.

.. note::
  There should be default categories present. Now you will create a custom category to add to the list available here.

Click **New Category**.

Fill out the following fields and click **Save**:

- **Name** - Programs-*<initials>*
- **Purpose** - This category will be used to tag VMs belonging to the program called "Programs-*<initials>*", as an example. This category will have "intern" and "sales" values in order to differentiate intern and sales VMs within the **programs-<initials>** category.
- **Values** - interns-*<initials>*
- **Values** - sales-*<initials>*

.. figure:: images/create_category.png

Create a New Security Policy
............................

Navigate to **Explore > Security Policies** within Prism Central.

Click **Create Security Policy** > Select **Isolate Environments**.

Fill out the following fields:

- **Name** - isolate-interns-sales-*<initials>*
- **Purpose** - Isolate intern Virtual Machine network traffic from sales.
- **Isolate This Category** - programs-*<initials>*:interns-*<initials>*
- **From This Category** - programs-*<initials>*:sales-*<initials>*
**Do NOT** select the check box for **Apply the isolation only within a subset of the data center**.

•	Enter interns-*<initials>* as a possible value of this category
•	Click the plus sign and enter sales-*<initials>* as another value in this category.
• Click **Apply Now** to save and apply the policy.

.. note::
  The Save and Monitor button allows you to save the configuration and monitor how the security policy works without applying it.

.. figure:: images/create_isol_pol.png

.. note::
  **BEFORE PROCEEDING BELOW:** Confirm network connectivity between **flow-<initials>-clone3** and **clone4** by pinging them from one another. These are the VM's we will be applying the Policy to.

Assign a category to VM's
-------------------------------------------------------
Navigate to **Explore > VMs**.

Select **flow-<initials>-clone3** and click **Actions > Manage Categories**.

In the Set Categories text box on the left side of the UI, type intern and select **programs-<initials>:interns-<initials>** from autocomplete. Click Save.

Select **flow-<initials>-clone4** and click **Actions > Manage Categories**.

In the Set Categories text box on the left side of the UI, type sales and select **Actions > Manage Categories** programs-*<initials>*:sales-*<initials>* from autocomplete. Click Save.

Confirm the Results of the Policy
------------------------------------------------------------------------------

Open the VM console of **flow-<initials>-clone3** and **flow-<initials>-clone4**.

Log into both VMs and ping from the **flow-<initials>-clone3** VM to the **flow-<initials>-clone4** VM.

.. note::
  The pings should NOT succeed because these two VMs now belong to the programs-*<initials>*:intern-*<initials>* and programs-*<initials>*:sales-*<initials>* categories and the policy isolate-interns-sales-*<initials>*, which was created earlier, isolates these two types of VMs.

Takeaways
+++++++++

- In this exercise you also created categories and an isolation security policy with ease without having to alter or change any networking configuration.
- After tagging the VMs with the categories created, the VMs simply behaved according to the policies they belong to.
