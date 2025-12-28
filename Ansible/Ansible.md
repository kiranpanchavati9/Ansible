
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
```

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

![alt text](<Ansible Image.png>)

---

## Useful Ansible Configuration Commands

```bash
ansible-config list    # List all available configuration options
ansible-config view    # Display the active configuration file
ansible-config dump    # Show the current effective configuration values
```


## Ansible Inventory

- Information about the target systems is stored in the **inventory file**.
- If you don’t create a custom inventory file, Ansible uses the default inventory located at:  
  **/etc/ansible/hosts**
- The inventory file is usually written in **INI format**.
- It can be a simple list of servers or organized into **groups** based on roles (web, db, mail, etc.).

---

### Example

#### Simple List
```ini
server1.company.com
server2.company.com
```

#### Grouped Inventory

```ini
[mail]
server3.company.com
server4.company.com

[db]
server5.company.com
server6.company.com

[web]
server7.company.com
server8.company.com
```

###  More on Inventory Files

For example, if you have a list of servers named from **server1** to **server4**, but you want to reference them in Ansible using **aliases** such as web servers or database servers, you can achieve this by defining an alias at the beginning of each line and assigning the actual server address using the **ansible_host** parameter.

server1.company.com  
server2.company.com  
server3.company.com  
server4.company.com  

- **ansible_host** is an inventory parameter used to define the **FQDN or IP address** of the target server. Ansible supports several other inventory parameters as well.

---

###  Inventory Parameters

- **ansible_connection**:  
  Defines the connection type  
  `ssh` (Linux) / `winrm` (Windows) / `localhost` (Local system)

- **ansible_port**:  
  Specifies the connection port  
  `22` (default for SSH) / `5986` (WinRM)

- **ansible_user**:  
  User account used to establish the remote connection  
  `root` / `administrator`

- **ansible_ssh_pass**:  
  Password used for SSH authentication











