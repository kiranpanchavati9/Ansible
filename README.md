## Ansible Directory-Based Configuration Diagram

```mermaid
flowchart TB
    A[Ansible Control Node]

    A --> W[Web Playbooks Directory]
    A --> D[Database Playbooks Directory]
    A --> N[Networking Playbooks Directory]

    W --> W1[web_playbook.yml]
    W --> W2[ansible.cfg<br/>gather_facts = false]

    D --> D1[db_playbook.yml]
    D --> D2[ansible.cfg<br/>gather_facts = true<br/>force_color = false]

    N --> N1[network_playbook.yml]
    N --> N2[ansible.cfg<br/>timeout = 20s]

    W1 --> E[Ansible Engine]
    D1 --> E
    N1 --> E

    E --> T[Target Hosts]
