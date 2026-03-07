# 08: Ansible - Advanced Variable Management

This section provides a deep dive into **Variable Scopes, Precedence, and Management** in Ansible. It covers how to define, capture, and use variables from various sources to build flexible and automated infrastructure.

## 1. Project Configuration and Inventory

### 1.1 `ansible.cfg`
The project's engine configuration, specifying the remote user, SSH keys, and the location of the inventory.

### 1.2 `hosts.yaml` (Inventory Variables)
You can define variables directly within the inventory for specific hosts or groups. These are highly specific and ideal for unique host configurations.

```yaml
debian1:
  v2: "hello, debian1"  # Host-specific variable
```

---

## 2. Variable Types and Structures

### 2.1 Simple, List, and Dictionary Variables
- **`playbook.yaml`**: Basic key-value pairs at the play level.
- **`playbook_arrays.yaml`**: Working with lists (arrays) using index notation `{{ env[1] }}`.
- **`playbook_dic.yaml`**: Using dictionaries (key-value maps) and accessing them via dot notation `{{ env.type }}`.

---

## 3. Dynamic and Advanced Variables

### 3.1 Capturing Output (`vars_registered.yaml`)
Use the `register` keyword to capture the output of a task (like a shell command) and store it in a variable for later use.

```yaml
- shell: date
  register: myDate

- debug:
    msg: "{{myDate.stdout}}"
```

### 3.2 External Variable Files (`var_from_files.yaml`)
Keep your playbooks clean by storing variable definitions in separate files within the `resources/` directory and importing them using `vars_files`.

```yaml
vars_files:
  - resources/file1.yaml
```

### 3.3 Automatic Discovery: Facts (`var_from_facts.yaml`)
Ansible automatically gathers system information from managed nodes. These "Facts" are available as the `ansible_facts` dictionary.

```yaml
- debug:
    msg: "Arch: {{ansible_facts['architecture']}}"
```

---

## 4. Understanding Scopes and Precedence

### 4.1 Task-Level vs. Play-Level (`var_tasks.yaml`)
Variables can be defined at different levels. A variable defined at the **Task level** will override one defined at the **Play level** with the same name.

### 4.2 Inventory discovery (`var_from_inventory.yaml`)
Demonstrates how the playbook automatically picks up variables defined in the `hosts.yaml` inventory for the targeted host.

---

## 5. Summary of Precedence (Highest to Lowest)
1. **Task Scope** (Variables defined within a specific task)
2. **Play Scope** (Variables defined in the `vars` or `vars_files` block of a play)
3. **Inventory Scope** (Host-specific variables in the inventory)
4. **Fact Scope** (Automatically gathered system information)

## 6. How to Run
From the `08` directory, execute any of the playbooks:
```bash
ansible-playbook <filename>.yaml
```
