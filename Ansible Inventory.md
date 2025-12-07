## Ansible Inventory

For Ansible to pick up which nodes to connect, we need to maintain an **inventory** file (a text file).
The list of servers can be kept in a file and organized according to the needs supported by Ansible.

Ansible inventory can be written in two formats:

1. **INI format**
2. **YAML format**

> We will prefer to use the `.ini` format for ease of use in general.

---

### What we can define in the Inventory

---

### Using IP Addresses

```ini
172.31.27.100
172.31.27.101
172.31.27.103
```
---

### Using IP Ranges

```ini
172.31.27.100-110
```

Or more advanced pattern-based ranges:

```ini
172.31.[01:50].[50:100]
```

---

### Using Hostnames

```ini
frontend.xyz.com
frontend[01:20].xyz.com
```

---

### Grouping Hosts

Inventory supports host grouping.
Default group name is `all` if no group is declared.

```ini
[frontend]
frontend[01:20].xyz.com

[DBSERVERS]
10.4.1.10
10.4.2.20
```

> A single server can be part of **multiple groups**.
> Ansible can run tasks against one or multiple groups at once.

---

### List Hosts from Inventory

```bash
ansible -i servers all --list-hosts
ansible -i frontend all --list-hosts
ansible -i DBSERVERS all --list-hosts
```

(`servers` is your inventory filename here.)

---

### Summary Table

| Feature  | Example             |
| -------- | ------------------- |
| IPs      | `172.31.27.100`     |
| IP Range | `172.31.27.100-110` |
| Hostname | `frontend.xyz.com`  |
| Grouping | `[frontend] ...`    |

---

## Output - IP Addresses

```ini
[root@ansible-control-node Python-3.13.0]# cat list
172.31.27.100
172.31.27.101
172.31.27.103
[root@ansible-control-node Python-3.13.0]# ansible -i list all --list-hosts
hosts (3):
172.31.27.100
172.31.27.101
172.31.27.103
```

## Output - IP Ranges

```ini
[root@ansible-control-node Python-3.13.0]# cat list1
172.31.27.100-110
172.31.[01:10].[10:30]
[root@ansible-control-node Python-3.13.0]# ansible -i list1 all --list-hosts
  hosts (211):
    172.31.27.100-110
    172.31.01.10
    172.31.01.11
    172.31.01.12
    172.31.01.13
    172.31.01.14
    172.31.01.15
    172.31.01.16
    172.31.01.17
    172.31.01.18
    172.31.01.19
    172.31.01.20
    172.31.01.21
    172.31.01.22
    172.31.01.23
    172.31.01.24
    172.31.01.25
    172.31.01.26
    172.31.01.27
    172.31.01.28
    172.31.01.29
    172.31.01.30
    172.31.02.10
    172.31.02.11
    172.31.02.12
    172.31.02.13
    172.31.02.14
    172.31.02.15
    172.31.02.16
    172.31.02.17
    172.31.02.18
    172.31.02.19
    172.31.02.20
    172.31.02.21
    172.31.02.22
    172.31.02.23
    172.31.02.24
    172.31.02.25
    172.31.02.26
    172.31.02.27
    172.31.02.28
    172.31.02.29
    172.31.02.30
    172.31.03.10
    172.31.03.11
    172.31.03.12
    172.31.03.13
    172.31.03.14
    172.31.03.15
    172.31.03.16
    172.31.03.17
    172.31.03.18
    172.31.03.19
    172.31.03.20
    172.31.03.21
    172.31.03.22
    172.31.03.23
    172.31.03.24
    172.31.03.25
    172.31.03.26
    172.31.03.27
    172.31.03.28
    172.31.03.29
    172.31.03.30
    172.31.04.10
    172.31.04.11
    172.31.04.12
    172.31.04.13
    172.31.04.14
    172.31.04.15
    172.31.04.16
    172.31.04.17
    172.31.04.18
    172.31.04.19
    172.31.04.20
    172.31.04.21
    172.31.04.22
    172.31.04.23
    172.31.04.24
    172.31.04.25
    172.31.04.26
    172.31.04.27
    172.31.04.28
    172.31.04.29
    172.31.04.30
    172.31.05.10
    172.31.05.11
    172.31.05.12
    172.31.05.13
    172.31.05.14
    172.31.05.15
    172.31.05.16
    172.31.05.17
    172.31.05.18
    172.31.05.19
    172.31.05.20
    172.31.05.21
    172.31.05.22
    172.31.05.23
    172.31.05.24
    172.31.05.25
    172.31.05.26
    172.31.05.27
    172.31.05.28
    172.31.05.29
    172.31.05.30
    172.31.06.10
    172.31.06.11
    172.31.06.12
    172.31.06.13
    172.31.06.14
    172.31.06.15
    172.31.06.16
    172.31.06.17
    172.31.06.18
    172.31.06.19
    172.31.06.20
    172.31.06.21
    172.31.06.22
    172.31.06.23
    172.31.06.24
    172.31.06.25
    172.31.06.26
    172.31.06.27
    172.31.06.28
    172.31.06.29
    172.31.06.30
    172.31.07.10
    172.31.07.11
    172.31.07.12
    172.31.07.13
    172.31.07.14
    172.31.07.15
    172.31.07.16
    172.31.07.17
    172.31.07.18
    172.31.07.19
    172.31.07.20
    172.31.07.21
    172.31.07.22
    172.31.07.23
    172.31.07.24
    172.31.07.25
    172.31.07.26
    172.31.07.27
    172.31.07.28
    172.31.07.29
    172.31.07.30
    172.31.08.10
    172.31.08.11
    172.31.08.12
    172.31.08.13
    172.31.08.14
    172.31.08.15
    172.31.08.16
    172.31.08.17
    172.31.08.18
    172.31.08.19
    172.31.08.20
    172.31.08.21
    172.31.08.22
    172.31.08.23
    172.31.08.24
    172.31.08.25
    172.31.08.26
    172.31.08.27
    172.31.08.28
    172.31.08.29
    172.31.08.30
    172.31.09.10
    172.31.09.11
    172.31.09.12
    172.31.09.13
    172.31.09.14
    172.31.09.15
    172.31.09.16
    172.31.09.17
    172.31.09.18
    172.31.09.19
    172.31.09.20
    172.31.09.21
    172.31.09.22
    172.31.09.23
    172.31.09.24
    172.31.09.25
    172.31.09.26
    172.31.09.27
    172.31.09.28
    172.31.09.29
    172.31.09.30
    172.31.10.10
    172.31.10.11
    172.31.10.12
    172.31.10.13
    172.31.10.14
    172.31.10.15
    172.31.10.16
    172.31.10.17
    172.31.10.18
    172.31.10.19
    172.31.10.20
    172.31.10.21
    172.31.10.22
    172.31.10.23
    172.31.10.24
    172.31.10.25
    172.31.10.26
    172.31.10.27
    172.31.10.28
    172.31.10.29
    172.31.10.30
[root@ansible-control-node Python-3.13.0]# 

```

## Output-Hostnames

```ini

root@ansible-control-node Python-3.13.0]# cat list2
frontend.xyz.com
frontend[01:20].xyz.com
[root@ansible-control-node Python-3.13.0]# ansible -i list2 all --list-hosts
hosts (21):
frontend.xyz.com
frontend01.xyz.com
frontend02.xyz.com
frontend03.xyz.com
frontend04.xyz.com
frontend05.xyz.com
frontend06.xyz.com
frontend07.xyz.com
frontend08.xyz.com
frontend09.xyz.com
frontend10.xyz.com
frontend11.xyz.com
frontend12.xyz.com
frontend13.xyz.com
frontend14.xyz.com
frontend15.xyz.com
frontend16.xyz.com
frontend17.xyz.com
frontend18.xyz.com
frontend19.xyz.com
frontend20.xyz.com
[root@ansible-control-node Python-3.13.0]# 
```
## Output-Grouping

```ini
[root@ansible-control-node Python-3.13.0]# cat list4
[frontend]
frontend[01:20].xyz.com

[DBSERVERS]
10.4.1.10
10.4.2.20
[root@ansible-control-node Python-3.13.0]# ansible -i list4 all --list-hosts
  hosts (22):
    frontend01.xyz.com
    frontend02.xyz.com
    frontend03.xyz.com
    frontend04.xyz.com
    frontend05.xyz.com
    frontend06.xyz.com
    frontend07.xyz.com
    frontend08.xyz.com
    frontend09.xyz.com
    frontend10.xyz.com
    frontend11.xyz.com
    frontend12.xyz.com
    frontend13.xyz.com
    frontend14.xyz.com
    frontend15.xyz.com
    frontend16.xyz.com
    frontend17.xyz.com
    frontend18.xyz.com
    frontend19.xyz.com
    frontend20.xyz.com
    10.4.1.10
    10.4.2.20
    
 [root@ansible-control-node Python-3.13.0]# cat list4 
[frontend]
frontend[01:20].xyz.com

[DBSERVERS]
10.4.1.10
10.4.2.20
[root@ansible-control-node Python-3.13.0]# ansible -i list4 frontend  --list-hosts
  hosts (20):
    frontend01.xyz.com
    frontend02.xyz.com
    frontend03.xyz.com
    frontend04.xyz.com
    frontend05.xyz.com
    frontend06.xyz.com
    frontend07.xyz.com
    frontend08.xyz.com
    frontend09.xyz.com
    frontend10.xyz.com
    frontend11.xyz.com
    frontend12.xyz.com
    frontend13.xyz.com
    frontend14.xyz.com
    frontend15.xyz.com
    frontend16.xyz.com
    frontend17.xyz.com
    frontend18.xyz.com
    frontend19.xyz.com
    frontend20.xyz.com
[root@ansible-control-node Python-3.13.0]# ansible -i list4 DBSERVERS  --list-hosts
  hosts (2):
    10.4.1.10
    10.4.2.20
[root@ansible-control-node Python-3.13.0]# 
```

## Inventory from Command Line

Ansible also supports defining inventory **directly from the CLI**, without a file.
This is useful when there are only a few nodes and we don’t need to maintain a static inventory file.

Example:

```bash
ansible -i frontend001.xyz.com,10.4.1.10, all --list-hosts

[root@ansible-control-node Python-3.13.0]# ansible -i frontend001.xyz.com,10.4.1.10, all --list-hosts
  hosts (2):
    frontend001.xyz.com
    10.4.1.10
[root@ansible-control-node Python-3.13.0]# 

```

---

> ⚠️ **Note:**
> When passing hosts directly using `-i`, you **must include a comma ( , )** after the host list.
> Otherwise, Ansible assumes the input is a filename instead of host entries.






