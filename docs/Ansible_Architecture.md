<a id="ansible-architecture"></a>
## Ansible Architecture

Ansible uses a simple and powerful **agentless** architecture that consists of two main components:

### 1. Control Node
- The machine where Ansible is installed (usually your laptop, workstation, or a CI/CD server).
- This is where you write and run your **Playbooks**, manage the **Inventory**, and execute commands.
- The Control Node connects to remote machines via **SSH** (Linux/macOS) or **WinRM** (Windows).
- Ansible only needs to be installed on the Control Node.

### 2. Managed Nodes (Hosts)
- The servers, virtual machines, network devices, or cloud instances you want to manage.
- Also called **managed hosts**.
- No Ansible installation or any agent is required on these nodes.
- They only need SSH access (or WinRM) and Python (for most modules).

---

### How Ansible Works

![Ansible Architecture Diagram](https://i.imgur.com/0ZfK8vL.png)

> *The diagram above illustrates how the Control Node pushes configurations to Managed Nodes over SSH.*

---

### Comparison Table

| Aspect                  | Control Node                          | Managed Nodes                          |
|------------------------|---------------------------------------|---------------------------------------|
| Ansible Installation   | Required                              | Not required (Agentless)              |
| Playbook Execution     | Executed here                         | Tasks are executed on them            |
| Communication          | Initiates connection (Push model)     | Receives instructions                 |
| Requirements           | Ansible + Python                      | Python + SSH access                   |
