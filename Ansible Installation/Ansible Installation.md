# Python 3.13 + Ansible Installation Guide (RHEL / CentOS / Rocky)

This guide explains how to install Python **3.13** from source and set up **Ansible 13** on an Enterprise Linux environment.

---

##  Step-1: Install Dependencies

```bash
dnf groupinstall "Development Tools" -y
dnf install openssl-devel bzip2-devel libffi-devel \
            zlib-devel ncurses-devel readline-devel \
            tk-devel xz-devel sqlite-devel -y
```

## Step-2: Download and Install Python 3.13

```bash
cd /usr/src
curl -O https://www.python.org/ftp/python/3.13.0/Python-3.13.0.tgz
tar xzf Python-3.13.0.tgz
cd Python-3.13.0
./configure --enable-optimizations
make -j $(nproc)
make altinstall
```

### Verify Installation 

python3.13 -V

## Step-3:Install pip for Python 3.13

```bash
python3.13 -m ensurepip
python3.13 -m pip install --upgrade pip
```

## Step-4: Install Ansible (latest)

```bash
python3.13 -m pip install ansible
```

```bash
[root@control-node Python-3.13.0]# pip3.13 install ansible
Collecting ansible
  Downloading ansible-13.0.0-py3-none-any.whl.metadata (8.1 kB)
Collecting ansible-core~=2.20.0 (from ansible)
  Downloading ansible_core-2.20.0-py3-none-any.whl.metadata (7.7 kB)
Collecting jinja2>=3.1.0 (from ansible-core~=2.20.0->ansible)
  Downloading jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Collecting PyYAML>=5.1 (from ansible-core~=2.20.0->ansible)
  Downloading pyyaml-6.0.3-cp313-cp313-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.4 kB)
Collecting cryptography (from ansible-core~=2.20.0->ansible)
  Downloading cryptography-46.0.3-cp311-abi3-manylinux_2_34_x86_64.whl.metadata (5.7 kB)
Collecting packaging (from ansible-core~=2.20.0->ansible)
  Downloading packaging-25.0-py3-none-any.whl.metadata (3.3 kB)
Collecting resolvelib<2.0.0,>=0.8.0 (from ansible-core~=2.20.0->ansible)
  Downloading resolvelib-1.2.1-py3-none-any.whl.metadata (3.7 kB)
Collecting MarkupSafe>=2.0 (from jinja2>=3.1.0->ansible-core~=2.20.0->ansible)
  Downloading markupsafe-3.0.3-cp313-cp313-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.7 kB)
Collecting cffi>=2.0.0 (from cryptography->ansible-core~=2.20.0->ansible)
  Downloading cffi-2.0.0-cp313-cp313-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (2.6 kB)
Collecting pycparser (from cffi>=2.0.0->cryptography->ansible-core~=2.20.0->ansible)
  Downloading pycparser-2.23-py3-none-any.whl.metadata (993 bytes)
Downloading ansible-13.0.0-py3-none-any.whl (53.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 53.3/53.3 MB 170.5 MB/s eta 0:00:00
Downloading ansible_core-2.20.0-py3-none-any.whl (2.4 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.4/2.4 MB 211.7 MB/s eta 0:00:00
Downloading jinja2-3.1.6-py3-none-any.whl (134 kB)
Downloading pyyaml-6.0.3-cp313-cp313-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (801 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 801.6/801.6 kB 135.6 MB/s eta 0:00:00
Downloading resolvelib-1.2.1-py3-none-any.whl (18 kB)
Downloading cryptography-46.0.3-cp311-abi3-manylinux_2_34_x86_64.whl (4.5 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 4.5/4.5 MB 155.8 MB/s eta 0:00:00
Downloading packaging-25.0-py3-none-any.whl (66 kB)
Downloading cffi-2.0.0-cp313-cp313-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (219 kB)
Downloading markupsafe-3.0.3-cp313-cp313-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (22 kB)
Downloading pycparser-2.23-py3-none-any.whl (118 kB)
Installing collected packages: resolvelib, PyYAML, pycparser, packaging, MarkupSafe, jinja2, cffi, cryptography, ansible-core, ansible
Successfully installed MarkupSafe-3.0.3 PyYAML-6.0.3 ansible-13.0.0 ansible-core-2.20.0 cffi-2.0.0 cryptography-46.0.3 jinja2-3.1.6 packaging-25.0 pycparser-2.23 resolvelib-1.2.1
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager, possibly rendering your system unusable.It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv. Use the --root-user-action option if you know what you are doing and want to suppress this warning.

[notice] A new release of pip is available: 24.2 -> 25.3
[notice] To update, run: pip install --upgrade pip
[root@control-node Python-3.13.0]# git clone https://github.com/kiranpanchavati9/Ansible.git
Cloning into 'Ansible'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
[root@control-node Python-3.13.0]# ls
aclocal.m4         build          config.sub    Grammar       iOS              Mac              Misc     PC                 Programs        python            python-gdb.py
Android            config.guess   configure     Include       Lib              Makefile         Modules  PCbuild            pybuilddir.txt  Python            README.rst
Ansible            config.log     configure.ac  install-sh    libpython3.13.a  Makefile.pre     Objects  platform           pyconfig.h      python-config     Tools
_bootstrap_python  config.status  Doc           InternalDocs  LICENSE          Makefile.pre.in  Parser   profile-run-stamp  pyconfig.h.in   python-config.py
[root@control-node Python-3.13.0]# 
```

### Check Version

```bash
ansible --version
```
```bash
[root@control-node Python-3.13.0]# ansible --version
ansible [core 2.20.0]
  config file = None
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.13/site-packages/ansible
  ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.13.0 (main, Dec  7 2025, 16:05:48) [GCC 11.5.0 20240719 (Red Hat 11.5.0-14)] (/usr/local/bin/python3.13)
  jinja version = 3.1.6
  pyyaml version = 6.0.3 (with libyaml v0.2.5)
[root@control-node Python-3.13.0]# 
```









