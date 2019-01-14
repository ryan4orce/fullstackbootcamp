.. _flow_visualization:

-------------------
Flow: Traffic Visualization
-------------------

Overview
++++++++

.. note::

  In this lab, you will use the VM's you cloned from the **AHV: Managing Workloads** lab. The naming prefix used for those clones was **flow-<initials>-clone#**

  Make sure you are using *your* VM's to prevent interference with other lab users.

The previous exercise, Secure Applications with Microsegmentation, you created an application policy, **Protect-app-<initials>**,  which allowed all traffic in monitor mode. This can be combined with visualization to detect unexpected traffic flows and add them to the policy if desired.

In this exercise you will use a policy in monitor mode to add detected traffic flows to the policy.

Flow Visualization
++++++++++++++++++

Add Flows to a Policy Using Flow Visualization
..............................................

View Detected Traffic Flows
-----------------------------------------------------

Navigate to **Explore > Security Policies > Protect-app-<initials>** to view the detected traffic flows from **Environment: Dev**

Confirm that **Environment: Dev** is listed as a source to **AppType: app-<initials>**. *NOTE: This can take a few minutes to appear.*

.. figure:: images/flow_viz.png

Hover over the yellow flow line from **Environment: Dev** to **AppType: app-<initials>** to view the protocol and connection information.

Click the yellow flow line to view a detailed graph of connection attempts.

.. figure:: images/network_flows.png

Add The Detected Flow to The Security Policy
--------------------------------------------

Select **Update** in the top right corner to edit the policy.

Click **Next** and view the detected traffic flows.

Hover over the **Environment: Dev** source in the inbound list.

Select the green check box to add this source to the inbound allowed list.

.. figure:: images/add_env_flow.png

Select OK to Add to Rule

Hover over the blue **Environment: Dev** source and select the pencil icon to edit the rule.

Select the pencil on **AppType: app-<initials>** to define specific ports and protocols.

Currently ICMP is allowed due to the ping detected in the previous task.

Select **Save** to save the ICMP rule.

Meow, Select **Next** to review the changes to the policy.

Move Policy from Monitoring to Applied Mode
------------------------------------------------------------

Now that the policy is complete, let's move it from Monitor Mode to Apply Mode.

Select **Apply Now** to save the policy and move it into Apply Mode.

Navigate to **Explore > Security Policies > Protect-app-<initials>**.

Confirm that **Environment: Dev** shows in blue as an allowed source.

Attempt to send traffic from another source such as **flow-<initials>-clone2** to **flow-<initials>-clone5**.

Is this traffic blocked?

Takeaways
+++++++++

- Flow visualization allows you to visualize the flows that are occurring within a policy. From there it's really easy to edit the policy in order to add or remove the flows that should or should not be occurring.
