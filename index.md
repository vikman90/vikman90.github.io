---
title: Wazuh Demo
---

# Welcome to the Wazuh Project

Hello World!

# Table of contents
{: .no_toc }

* TOC
{:toc}

# How to install Wazuh Manager

You can install from packages (recommended) or from sources.

## Install from RPM packages

First we’ll install the Wazuh repository. Run the following command depending on your operating system:

```sh
cat > /etc/yum.repos.d/wazuh.repo << \EOF
[wazuh_repo]
gpgcheck=1
gpgkey=https://packages.wazuh.com/key/RPM-GPG-KEY-WAZUH
enabled=1
name=RHEL-$releasever - Wazuh
baseurl=https://packages.wazuh.com/yum/el/$releasever/$basearch
protect=1
EOF
```

Now install the Wazuh packages:

```sh
yum install wazuh-manager wazuh-api
```

## Install from sources

Follow these steps:

```sh
git clone https://github.com/wazuh/wazuh.git
cd wazuh
make -C src TARGET=manager DEBUG=yes
./install.sh
```

### Options for the make command

TARGET
: This option is the target compilation profile. It may be `manager`, `agent` or `local`.

DEBUG
: Inserts debugging symbols into the binary code. It's useful for `gdb` or `valgrind`.

### OSSEC profiles

**Component** | **Manager** | **Agent** | **Local**
*syscheckd* |Yes|Yes|Yes
*logcollector* |Yes|Yes|Yes
*modulesd* |Yes|Yes|Yes
*analysisd* |Yes||Yes
*remoted* |Yes||
*agentd* ||Yes|
*execd* |Yes|Yes|Yes
*monitord* |Yes||

# Next steps

* Configure Wazuh.
* Add agents.
* Set `syscheck.sleep` to 0.
* Enable *Wazuh TRT Technology* (coming soon).
* Start Wazuh.
