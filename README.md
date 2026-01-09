## ansible-playbooks

This repository contains a collection of Ansible playbooks intended for Linux system administration, infrastructure automation, and operational tasks. The playbooks focus on common, practical use cases such as host configuration, service management, application deployment, container and Kubernetes-related operations, and routine automation workflows. They are designed to be readable, modular, and easy to adapt to different environments.

### **_Disclaimer_**

These Ansible playbooks are provided as-is for general informational and operational purposes. They reflect one possible approach based on specific assumptions, environments, inventories, variables, roles, and Ansible versions, and may not be suitable for all systems. You are expected to review, understand, and test any playbook before applying it to your infrastructure.

Ansible playbooks can make broad, automated changes across one or more systems. You are solely responsible for ensuring appropriate backups, safeguards, access controls, and change management practices are in place, and for validating that any playbook behaves as intended in your environment. No warranties are expressed or implied, and the author disclaims any liability for damages, data loss, outages, or other consequences resulting from use or misuse of these playbooks.

### **_Notes and Assumptions_**

These Playbooks will generally assume a Linux-based target environment and common system tooling, but a limited number will include some functions for Microsoft Windows hosts.

Some playbooks may require elevated privileges (for example, via become).

Inventory structure, variable organization, and role layout may vary by playbook and are intended as examples rather than rigid standards.

You should always review variables, defaults, and tasks to ensure alignment with your own operational requirements.

### **_Quick Start_**

#### Clone the repository

```
git clone https://github.com/twodadoos/ansible-playbooks.git

cd ansible-playbooks
```

#### Copy and customize an inventory

Start from the safe example inventory:

```
cp inventories/example/hosts.example inventories/dev/hosts
```

* Edit inventories/dev/hosts with your actual hostnames, IPs, and users

* Choose the inventory that matches your environment (dev, prod, et cetera)

#### Review variables

* Check group_vars/all.yml for shared variables.

* Check host_vars/<hostname>.yml for host-specific overrides.

* Adjust values as needed for your environment.

### Run a playbook (dry run first)

```
ansible-playbook -i inventories/dev/hosts playbooks/webserver.yml
```

* **--check** simulates changes without applying them
* **--diff** shows what would change in files/templates

#### Apply changes

Once satisfied with the dry run:

```
ansible-playbook -i inventories/dev/hosts playbooks/webserver.yml
```

**_Optional_**: Run the full site orchestration f you have a master playbook like site.yml:

```
ansible-playbook -i inventories/dev/hosts playbooks/site.yml
```