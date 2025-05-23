#  Introduction to Ansible 

---

##  What is Ansible?

**Ansible** is a powerful, open-source automation tool used by DevOps engineers and system administrators to:

- ✅ Configure servers
- ✅ Deploy applications
- ✅ Manage infrastructure (bare-metal, virtual, cloud)
- ✅ Orchestrate multi-machine environments

---

### ⚡ Key Features

- **Agentless**  
  > No agent/software is needed on the target machines. Ansible connects using native protocols like SSH or WinRM.

- **Written in Python**  
  > Easy to extend, script, or debug.

- **Declarative & Idempotent**  
  > Repeatable runs won’t cause duplication or errors.

- **Playbooks written in YAML**  
  > Human-readable and version-controlled.

---

##  How Ansible Connects to Nodes

| OS      | Protocol | Port     |
|---------|----------|----------|
| **Linux**   | SSH      | 22       |
| **Windows** | WinRM    | 5985 (HTTP), 5986 (HTTPS) |

> ✅ You only need **Ansible on the control node**. The managed systems must be accessible via SSH or WinRM.

---

#  Push vs Pull Model in Automation

| Tool     | Model | Description                            |
|----------|-------|----------------------------------------|
| **Puppet**  | Pull  | Nodes (agents) **pull** configurations from the Puppet master |
| **Ansible** | Push  | The control node **pushes** commands to nodes via SSH/WinRM |

> Ansible **can also use pull mode** via `ansible-pull`, but the push method is default and most common.

---

## ✅ Why Use Ansible?

- 🔒 Secure (SSH-based, no daemons)
-  Simple learning curve
-  Reusable roles and modules
-  Huge community + Galaxy role ecosystem
-  Easy to integrate in CI/CD

---

### 📚 Next Sections

- [`What is Ansible?`](./Ansible.md)  
	-  Understand Ansible's architecture, modules, and ecosystem.
	-  Learn how to write, structure, and run YAML playbooks like a pro.

- [`Simple Project: Deploying NGINX Web Server`](./Project.md)  
	-   A hands-on beginner project to deploy a web page using Ansible.

---
