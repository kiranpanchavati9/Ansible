## Adhoc Commands

```bash
[root@ansible-control-node Python-3.13.0]# ansible -i 64.227.141.106, all -m ping -e ansible_user=root -e ansible_password='K25&e1\2QGhd9rM'
[WARNING]: Host '64.227.141.106' is using the discovered Python interpreter at '/usr/local/bin/python3.13', but future installation of another Python interpreter could cause a different interpreter to be discovered. See https://docs.ansible.com/ansible-core/2.20/reference_appendices/interpreter_discovery.html for more information.
64.227.141.106 | SUCCESS => {
"ansible_facts": {
"discovered_interpreter_python": "/usr/local/bin/python3.13"
},
"changed": false,
"ping": "pong"
}
[root@ansible-control-node Python-3.13.0]# 
```

```bash
[root@ansible-control-node Python-3.13.0]# ansible -i 64.227.141.106, all -m command -a "uptime" -e ansible_user=root -e ansible_password='K25&e1\2QGhd9rM'
[WARNING]: Host '64.227.141.106' is using the discovered Python interpreter at '/usr/local/bin/python3.13', but future installation of another Python interpreter could cause a different interpreter to be discovered. See https://docs.ansible.com/ansible-core/2.20/reference_appendices/interpreter_discovery.html for more information.
64.227.141.106 | CHANGED | rc=0 >>
17:11:35 up  1:23,  2 users,  load average: 0.04, 0.01, 0.00
[root@ansible-control-node Python-3.13.0]# 
```

```aiignore

[root@ansible-control-node Python-3.13.0]# cat list
64.227.141.106 ansible_user=root ansible_password='K25&e1\2QGhd9rM'

[root@ansible-control-node Python-3.13.0]# ansible -i list all -m command -a "uptime"
[WARNING]: Host '64.227.141.106' is using the discovered Python interpreter at '/usr/local/bin/python3.13', but future installation of another Python interpreter could cause a different interpreter to be discovered. See https://docs.ansible.com/ansible-core/2.20/reference_appendices/interpreter_discovery.html for more information.
64.227.141.106 | CHANGED | rc=0 >>
 17:16:43 up  1:28,  2 users,  load average: 0.00, 0.00, 0.00
[root@ansible-control-node Python-3.13.0]# 

```





