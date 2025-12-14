# Ansible Playbook Test Run

**Host:** `ansible-control-node`
**Target IP:** `139.59.22.93`

## 1\. Playbook Source (`test.yml`)

```yaml
- name: Sample Playbook
  hosts: all
  tasks:
    - ping:
      name: Ping Module
    - debug:
        msg: Hello World
      name: Print Hello World
```

## 2\. Execution Command

> **Note:** Executing passwords via command line arguments (`-e`) is visible in process lists. Consider using **Ansible Vault** for production environments.

```bash
ansible-playbook -i 139.59.22.93, test.yml -e ansible_user=root -e ansible_password='K25&e1\2QGhd9rM'
```

## 3\. Execution Output

```text
PLAY [Sample Playbook] **********************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************************
[WARNING]: Host '139.59.22.93' is using the discovered Python interpreter at '/usr/local/bin/python3.13', but future installation of another Python interpreter could cause a different interpreter to be discovered. See https://docs.ansible.com/ansible-core/2.20/reference_appendices/interpreter_discovery.html for more information.
ok: [139.59.22.93]

TASK [Ping Module] **************************************************************************************************************************************************
ok: [139.59.22.93]

TASK [Print Hello World] ********************************************************************************************************************************************
ok: [139.59.22.93] => {
    "msg": "Hello World"
}

PLAY RECAP **********************************************************************************************************************************************************
139.59.22.93               : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0    
```