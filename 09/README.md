# Ansible Roles, Variable Precedence, Handlers, and Task Execution Order

This directory demonstrates how to use **Ansible Roles**, showcases the difference between `defaults` and `vars` within a role, introduces **Handlers**, and explains the execution order of **pre_tasks**, **roles**, **tasks**, and **post_tasks**.

## Folder Structure

- `ansible.cfg`: Local Ansible configuration.
- `hosts.yaml`: Inventory file defining the target hosts.
- `playbook.yaml`: The main playbook demonstrating the execution order of different task sections.
- `development/`: A role that manages software installation, services, and database initialization on Debian-based systems.
    - `defaults/main.yml`: Contains low-precedence default variables (`software: mariadb-server`).
    - `vars/main.yml`: Contains high-precedence role variables (`software: nginx`).
    - `tasks/main.yml`: Contains the logic to install software, start services, and notify handlers.
    - `handlers/main.yml`: Contains tasks that are only executed when notified by a task that has changed.
    - `files/create_db.sql`: A static SQL file used by the handler to initialize a database.

## Playbook Execution Order

In `playbook.yaml`, tasks are executed in a specific order defined by Ansible:

1.  **`pre_tasks`**: Tasks executed before roles or regular tasks (e.g., updating the package cache).
2.  **Handlers** notified by `pre_tasks`.
3.  **`roles`**: The roles listed in the play (e.g., the `development` role).
4.  **`tasks`**: The regular tasks defined in the play.
5.  **Handlers** notified by `roles` or `tasks`.
6.  **`post_tasks`**: Tasks executed after roles and regular tasks have finished.
7.  **Handlers** notified by `post_tasks`.

In this example, even though `tasks` appears after `roles` in the YAML file, if they were mixed, roles always run before the `tasks` section of the play.

## The "development" Role

The role in this example is designed for Debian systems. It performs several key operations:
1. **Installs a package** defined by the `{{ software }}` variable.
2. **Starts a service** defined by the `{{ service }}` variable.
3. **Triggers Handlers**: When the service is started (or if its state changes), it triggers the `copy_sql_script` and `create_db` handlers using the `notify` keyword.

### Handlers in this Role
Handlers are only executed at the end of their respective section (pre_tasks, roles/tasks, or post_tasks), and only if a task that notifies them reports a "changed" status.
- `copy_sql_script`: Copies a local SQL script to the target host.
- `create_db`: Executes the SQL script using the `mysql` command.

## Ansible Variable Precedence

Variable precedence is the order in which Ansible evaluates variables defined in different places. When the same variable is defined in multiple locations, the one with the highest precedence wins.

Here is the order from **lowest to highest** (last one wins):

1.  **command line values** (e.g., `-u user`)
2.  **role defaults** (`[role]/defaults/main.yml`)
3.  inventory file or script group vars
4.  inventory `group_vars/all`
5.  playbook `group_vars/all`
6.  inventory `group_vars/*`
7.  playbook `group_vars/*`
8.  inventory file or script host vars
9.  inventory `host_vars/*`
10. playbook `host_vars/*`
11. host facts / cached set_facts
12. play vars
13. play `vars_prompt`
14. play `vars_files`
15. **role vars** (`[role]/vars/main.yml`)
16. block vars (only for tasks in block)
17. task vars (only for the task)
18. `include_vars`
19. `set_facts` / registered vars
20. role (and `include_role`) params
21. include params
22. **extra vars** (always win, e.g., `-e "var=value"`)

### Summary of this example:
- `development/defaults/main.yml` (Precedence 2)
- `development/vars/main.yml` (Precedence 15)

The value in `vars/main.yml` overrides the value in `defaults/main.yml`.
