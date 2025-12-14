# Frontend Setup - RoboShop V1

This document details the Ansible automation for setting up the Frontend component of the RoboShop application.

##  Overview

* **Project:** Ansible-RoboShop-V1
* **Component:** Frontend (Nginx)
* **Target Host:** `frontend-dev.kiranpanchavati.online`
* **Playbook:** `frontend.yml`

##  Usage

To execute the frontend setup, run the following command from the control node:

```bash
ansible-playbook -i frontend-dev.kiranpanchavati.online, frontend.yml \
-e ansible_user=root \
-e ansible_password='<YOUR_PASSWORD>'
```

> **Note:** The comma (`,`) after the hostname in the `-i` flag is required to indicate a host list rather than a file path.

##  Playbook Tasks

The `frontend.yml` playbook performs the following configurations:

1.  **Gather Facts:** Collects system information (OS, Python version, IP, etc.).
2.  **Install Nginx:** Installs Nginx version 1.24.

##  Execution Log

*Date: December 14, 2025*

```log
[root@ansible-control-node Ansible-RoboShop-V1]# ansible-playbook -i frontend-dev.kiranpanchavati.online, frontend.yml \
-e ansible_user=root \
-e ansible_password='DevOps@123$%1S'

PLAY [Frontend Setup] **************************************************************************************************

TASK [Gathering Facts] *************************************************************************************************
[WARNING]: Host 'frontend-dev.kiranpanchavati.online' is using the discovered Python interpreter at '/usr/bin/python3.9', but future installation of another Python interpreter could cause a different interpreter to be discovered.
ok: [frontend-dev.kiranpanchavati.online]

TASK [Install Nginx 1.24] **********************************************************************************************
changed: [frontend-dev.kiranpanchavati.online]

PLAY RECAP *************************************************************************************************************
frontend-dev.kiranpanchavati.online : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

##  Status

* **Result:** Success (`ok=2`)
* **Changes Made:** Yes (`changed=1`) - Nginx was installed or updated.

### nginx-1.24.0 installed in frontend server 

```aiignore
[root@frontend-dev ~]# nginx -version
nginx version: nginx/1.24.0
```


