.. Copyright (C) 2018 Wazuh, Inc.

.. _agent_groups:

agent_groups
============

.. versionadded:: 3.0.0

The agent_groups program allows you to list agents assigned to a group, assign agents to a group and manage the agents groups. Below are the parameters that can be used with this new function:

+---------------------------------------+---------------------------------------------------------+
| **-h**                                | Displays the help message                               |
+---------------------------------------+---------------------------------------------------------+
| **-l**                                | Lists all groups                                        |
+---------------------------------------+---------------------------------------------------------+
| **-q**                                | Quiet mode (outputs no confirmation)                    |
+---------------------------------------+---------------------------------------------------------+
| **-l -g group_id**                    | Lists the agents in the group                           |
+---------------------------------------+---------------------------------------------------------+
| **-c -g group_id**                    | Lists the configuration files in group                  |
+---------------------------------------+---------------------------------------------------------+
| **-a -i agent_id -g group_id [-q]**   | Sets the agent's group                                  |
+---------------------------------------+---------------------------------------------------------+
| **-r -i agent_id [-q]**               | Unset the agent's group                                 |
+---------------------------------------+---------------------------------------------------------+
| **-s -i agent_id**                    | Shows the group of an agent                             |
+---------------------------------------+---------------------------------------------------------+
| **-a -g group_id [-q]**               | Creates a group                                         |
+---------------------------------------+---------------------------------------------------------+
| **-r -g group_id [-q]**               | Removes a group from all agents assigned to it          |
+---------------------------------------+---------------------------------------------------------+
| **-d**                                | Debug                                                   |
+---------------------------------------+---------------------------------------------------------+

Examples
--------

* Assign group *'debian'* to agent 002:

.. code-block:: console

    $ /var/ossec/bin/agent_groups -a -i 002 -g debian
    Do you want to set the group 'debian' to the agent '002'? [y/N]: y
    Group 'debian' assigned to agent '002'.

* Get the group of agent 002:

.. code-block:: console

    $ /var/ossec/bin/agent_groups -s -i 002
    The agent 'agent-deb-002' with ID '002' has the group: 'debian'.

* List all agents in group *'debian'*:

.. code-block:: console

    $ /var/ossec/bin/agent_groups -l -g debian
    3 agent(s) in group 'debian':
        ID: 002  Name: agent-deb-002.
        ID: 003  Name: agent-deb-003.
        ID: 004  Name: agent-deb-004.

* List configuration files in group *'debian'*:

.. code-block:: console

    $ /var/ossec/bin/agent_groups -c -g debian
    Files for group 'debian':
      agent.conf
      rootkit_trojans.txt
      merged.mg
      cis_debian_linux_rcl.txt
      rootkit_files.txt
      system_audit_ssh.txt
      system_audit_rcl.txt


* Remove agent 002 from the current group:

.. code-block:: console

    $ /var/ossec/bin/agent_groups -r -i 002
    Do you want to remove the current group of agent '002'? [y/N]: y
    Group removed. Current group for agent '002': 'default'.


* Remove the group *'debian'* from every agent:

.. code-block:: console

    $ /var/ossec/bin/agent_groups -r -g debian
    Do you want to remove the 'debian' group of every agent? [y/N]: y
    Group 'debian' removed.
    Affected agents: 003, 004.
