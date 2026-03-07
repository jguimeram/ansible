# 🚀 Ansible Journey: From Zero to Infrastructure as Code

Welcome to this comprehensive Ansible learning repository. This project is structured as a step-by-step guide, evolving from basic inventory management to advanced variable scoping and task modularization.

---

## 📂 Project Structure

Each folder in this repository represents a specific milestone in the learning path. You can explore them individually by switching to their respective branches or tags.

| Step | Branch | Focus Area | Key Concepts |
| :--- | :--- | :--- | :--- |
| **01** | `01` | **Inventories** | Static host files, groups, and connection testing. |
| **02** | `02` | **Basic Execution** | Running your first playbooks and the ping module. |
| **03** | `03` | **Task Definition** | Structuring plays and defining multiple tasks. |
| **04** | `04` | **Multi-Play** | Managing different host groups within a single playbook. |
| **05** | `05` | **File Management** | Handling resources and deploying static content. |
| **06** | `06` | **Modularization** | Using `include_tasks` for cleaner, reusable code. |
| **07** | `07` | **Variables (Deep)** | Group vars, host vars, and hierarchy. |
| **08** | `08` | **Playbook Vars** | Inline variables and dynamic configuration. |

---

## 🛠️ Getting Started

### Prerequisites
- **Ansible Installed**: Ensure you have Ansible on your control node.
- **SSH Access**: Managed nodes should be accessible via SSH keys.

### How to use this Repo
1. **Clone the repository:**
   ```bash
   git clone https://github.com/jguimeram/ansible.git
   cd ansible
   ```
2. **Switch to a specific step:**
   ```bash
   git checkout 08  # Explore the latest step
   ```
3. **Run a Playbook:**
   ```bash
   cd 08
   ansible-playbook playbook.yaml
   ```

---

## 📝 About this Project
This repository serves as a live documentation of the Ansible learning curve. It emphasizes **Infrastructure as Code (IaC)** principles, focusing on readability, modularity, and automation best practices.

*Happy Automating!* 🤖
