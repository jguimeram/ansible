# Ansible - Variables (07)

This folder demonstrates how to manage and use variables in Ansible using different methods: inventory variables, group variables, and host variables.

## Project Structure

- `hosts.yaml`: Inventory file containing host and group definitions, including some inline variables.
- `ansible.cfg`: Configuration file specifying defaults like the inventory path and SSH user.
- `playbook.yaml`: Main playbook containing tasks for different host groups.
- `add_task.yaml`: External task file included in the main playbook.
- `group_vars/`: Directory for group-specific variables.
  - `data_servers.yaml`: Variables applied to the `data_servers` group.
- `host_vars/`: Directory for host-specific variables.
  - `rocky1.yaml`: Variables applied specifically to the `rocky1` host.
- `resources/`: Contains static files used by the playbook (e.g., `index.html`).

## Variable Usage

Variables are defined in multiple locations, showcasing Ansible's variable precedence:

1.  **Inventory-level variables**: In `hosts.yaml`, variables like `prt`, `env`, and `ansible_user` are defined for specific hosts or groups.
2.  **Group variables**: Files in `group_vars/` automatically apply to hosts in the corresponding group.
3.  **Host variables**: Files in `host_vars/` automatically apply to specific hosts.

## Playbook Overview

The `playbook.yaml` performs the following:
- **Test play (app_servers)**: Pings the hosts and creates a temporary file.
- **Install nginx (debian)**: 
  - Includes `add_task.yaml` to stop Apache.
  - Installs and starts Nginx.
  - Copies a custom `index.html` to the web root.

## Running the Playbook

To execute the playbook using the local inventory:

```bash
ansible-playbook -i hosts.yaml playbook.yaml
```
