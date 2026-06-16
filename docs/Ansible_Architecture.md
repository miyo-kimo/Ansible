# Ansible Architecture

![Ansible Logo](https://img.shields.io/badge/Ansible-FF0000?logo=ansible&logoColor=white&style=for-the-badge)

**Understanding the Agentless Architecture of Ansible**

---

## Table of Contents
- [Overview](#overview)
- [Control Node](#control-node)
- [Managed Nodes](#managed-nodes)
- [How Ansible Works](#how-ansible-works)
- [Architecture Diagram](#architecture-diagram)
- [Comparison](#comparison)

---

## Overview

Ansible uses a simple, **agentless** architecture. This means you don't need to install any special software or agents on the machines you want to manage.

It follows a **push-based** model where one central machine (Control Node) connects to remote machines and executes tasks.

---

## Control Node

The **Control Node** is the machine where you install and run Ansible.

### Responsibilities:
- Running `ansible` and `ansible-playbook` commands
- Storing Playbooks, Roles, and Inventory files
- Connecting to remote hosts via SSH or WinRM
- Processing results and generating reports

### Requirements:
- Ansible installed
- Python
- SSH client (for Linux/macOS targets)

> **Note:** You can have multiple Control Nodes, but usually one is sufficient.

---

## Managed Nodes (Hosts)

**Managed Nodes** are the servers, VMs, containers, or network devices you want to configure and manage.

### Characteristics:
- No Ansible installation required
- No background agent or daemon running
- Only needs Python (for most modules) and SSH access
- Can be Linux, Windows, macOS, or network devices (Cisco, Juniper, etc.)

---

## How Ansible Works

1. You run a command or playbook from the **Control Node**
2. Ansible connects to the **Managed Nodes** using SSH/WinRM
3. It executes the required **modules** on the remote hosts
4. After execution, the connection is closed
5. Results are returned to the Control Node

This process is **idempotent** — running the same playbook multiple times produces the same result.

---

## Architecture Diagram


<img src="https://www.devopstrainer.in/dailylogs/storage/posts/2025/12/05/MfQbN6nPnFroNZcA8QoyedH0VGOqGWvVLxLv40XE.png" alt="Ansible Architecture" width="80%" />

> *Control Node pushes configuration to multiple Managed Nodes over SSH.*

---

## Comparison

| Aspect                    | Control Node                          | Managed Nodes                          |
|--------------------------|---------------------------------------|---------------------------------------|
| Ansible Installation     | Required                              | Not required                          |
| Execution Location       | Playbooks run here                    | Tasks executed here                   |
| Communication Model      | Push (initiates connection)           | Receives instructions                 |
| Software Requirements    | Ansible + Python + SSH                | Python + SSH (or WinRM)               |
| Number of Instances      | Usually 1                             | Many (hundreds or thousands)          |

---

## Best Practices

- Keep your Control Node secure and well-maintained
- Use SSH keys instead of passwords
- Organize your inventory properly
- Consider using Ansible Tower / AWX for larger environments
