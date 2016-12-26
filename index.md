---
title: Wazuh Demo
---

# Welcome to the Wazuh Project

Hello World!

**Information:** \\
This is not the valid Wazuh documentation. Get the [Official Wazuh documentation](http://documentation.wazuh.com/en/latest).
{: .note .info}

---

# Table of contents
{: .no_toc }

* TOC
{:toc}

---

# How to install Wazuh Manager

You can install from packages (recommended) or from sources.

## Install from RPM packages

First we’ll install the Wazuh repository. Run the following command depending on your operating system:

```sh
cat > /etc/yum.repos.d/wazuh.repo <<\EOF
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

Component|Manager|Agent|Local
---------|-------|-----|-----
Syscheck / Rootcheck|Yes|Yes|Yes
Log collector|Yes|Yes|Yes
Active Response executor|Yes|Yes|Yes
Analysis engine|Yes||Yes
Remote receiver|Yes||
Agent client||Yes|
OpenSCAP module|Yes|Yes|Yes
Database sync module|Yes||Yes
Alert and agent monitor|Yes||Yes
Mail alert sender|Yes||Yes
Syslog client|Yes||Yes

# Next steps

* Configure Wazuh.
* Add agents.
* Speed up Syscheck by setting `syscheck.sleep` to 0.
* Enable *Wazuh TRT Technology* (coming soon).
* Start Wazuh.

**Warning:** \\
This page will self destruct in a short time.
{: .note .warning}
