````markdown
## What is Ansible?

**Ansible** is an open-source automation tool used to **configure systems, deploy applications, and manage servers** automatically without logging into them manually.

It works by sending instructions (called **playbooks**) to machines over **SSH** and does **not require any agent** to be installed on the target systems.

---

## Simple Example

Imagine you want to install **Nginx** on multiple servers.

### Without Ansible
- Log in to each server manually
- Run installation commands on every server
- Repeat the same steps again and again

### With Ansible
You write **one playbook** and execute it once, and Ansible takes care of the rest.

```yaml
- name: Install Nginx on web servers
  hosts: web
  become: yes
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
````

---

## Directory-Based Ansible Configuration

Let’s assume we have different categories of Ansible playbooks stored in **separate directories** on a host:

* **Web**
* **Database**
* **Networking**

Each category requires **different Ansible behavior**, so we use a **separate `ansible.cfg` file** in each directory.

Ansible automatically loads the `ansible.cfg` file from the **current working directory**, allowing us to apply **directory-specific settings** without affecting other playbooks.

---

## Web Playbooks Configuration

**Requirement**

* Disable fact gathering

**`ansible.cfg` (Web directory)**

```ini
[defaults]
gathering = explicit
```

---

## Database Playbooks Configuration

**Requirements**

* Enable fact gathering
* Disable colored output

**`ansible.cfg` (Database directory)**

```ini
[defaults]
gathering = smart
force_color = false
```

---

## Networking Playbooks Configuration

**Requirement**

* Increase SSH connection timeout to 20 seconds

**`ansible.cfg` (Networking directory)**

```ini
[ssh_connection]
timeout = 20
```


---

## Key Benefits

✔ Clean separation of configurations
✔ No impact on other playbooks
✔ Easy to manage environment-specific behavior

By placing a customized `ansible.cfg` in each playbook directory, we can control Ansible’s behavior **per playbook category** in a simple and scalable way.

---

## Useful Ansible Configuration Commands

```bash
ansible-config list    # List all available configuration options
ansible-config view    # Display the active configuration file
ansible-config dump    # Show the current effective configuration values
```

```
```
