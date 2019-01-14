.. title:: Nutanix Enterprise Cloud - The Dream

.. toctree::
  :maxdepth: 2
  :caption: Table of Contents
  :name: _table_of_contents
  :hidden:

  day_one_agenda/day_one_agenda
  lab_nutanix_tech_overview/lab_nutanix_tech_overview

.. toctree::
  :maxdepth: 2
  :caption: Setting up The Basics
  :name: _setting_up_the_basics
  :hidden:

  lab_storage_configuration/lab_storage_configuration
  lab_network_configuration/lab_network_configuration

.. toctree::
  :maxdepth: 2
  :caption: Deploying and Managing Workloads
  :name: _deploying_and_managing_workloads
  :hidden:

  lab_deploy_windows_workloads/lab_deploy_windows_workloads
  lab_deploy_linux_workloads/lab_deploy_linux_workloads
  lab_manage_workloads/lab_manage_workloads

.. toctree::
  :maxdepth: 2
  :caption: Nutanix Files
  :name: _deploying_and_managing_workloads
  :hidden:

  files_smb_share/files_smb_share
  files_nfs_export/files_nfs_export

.. toctree::
  :maxdepth: 2
  :caption: Nutanix Flow
  :name: _nutanix_flow
  :hidden:

  flow_quarantine_vm/flow_quarantine_vm
  flow_isolate_environments/flow_isolate_environments
  flow_secure_app/flow_secure_app
  flow_visualization/flow_visualization

.. toctree::
  :maxdepth: 2
  :caption: Appendix
  :name: _appendix
  :hidden:

  appendix/glossary

.. _getting_started:

---------------
Getting Started
---------------

Welcome to the Nutanix Enterprise Cloud OS Workshop! This workbook accompanies an instructor-led session that introduces Nutanix technologies and many common management tasks. Each section has a lesson and an exercise to give you hands-on practice. The instructor explains the exercises and answers any additional questions that you may have.

At the end of the Workshop, attendees should understand the basic concepts and technologies that make up the Nutanix Enterprise Cloud stack and should be well prepared for a hosted or onsite proof-of-concept (POC) engagement.

SoCal Workshop Agenda
++++++++++++++

- Introductions
- Why Nutanix? Nutanix 101 Whiteboard Review
- Nutanix Prism with Any Hypervisor Overview
- The Basics: Storage and Network Configuration Labs
- Deploying and Managing Workloads - *Windows OR Linux*
- Nutanix Files (File Services) Overview and Labs
- Nutanix Flow (Network Microsegmentation) Overview and Labs

Introductions
+++++++++++++

- Name
- Familiarity with Nutanix

Lab Setup and Credentials
+++++++++++++

- Your username and password for the Lab Environment, as well as the access portal are listed on the whiteboard.
- Log into your virtual desktops with the information provided by your instructor. You can also access the environment using the Access Instructions listed below.


Access Instructions
+++++++++++++++++++

The Nutanix Hosted POC environment can be accessed a number of different ways:

Citrix XenDesktop
.................

https://citrixready.nutanix.com - *Accessible via the Citrix Receiver client or HTML5*

**Nutanix Employees** - Use your NUTANIXDC credentials

**Non-Employees** - See the whiteboard, or ask your instructor for assistance.

Employee Pulse Secure VPN
..........................

https://sslvpn.nutanix.com - Use your CORP credentials

Non-Employee Pulse Secure VPN
..............................

https://lab-vpn.nutanix.com - **Username:** *<Assigned by Instructor>*, **Password:** *<Provided by Instructor>*

Under **Client Application Sessions**, click **Start** to the right of **Pulse Secure** to download the client.

Install and open **Pulse Secure**.

Add a connection:

- **Type** - Policy Secure (UAC) or Connection Server
- **Name** - HPOC VPN
- **Server URL** - lab-vpn.nutanix.com
