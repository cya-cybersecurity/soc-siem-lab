# Splunk Enterprise Installation on Ubuntu Server

## Overview

This document outlines the installation and configuration of Splunk Enterprise on an Ubuntu Server virtual machine used as the SIEM platform in the home SOC lab.

---

# Environment

| Component | Value |
|---|---|
| OS | Ubuntu Server |
| Virtualization | VirtualBox |
| SIEM Platform | Splunk Enterprise |

---

# Installation Steps

## Download Splunk Enterprise

Downloaded Splunk Enterprise for Linux from the official Splunk website.

## Install Splunk

```bash
sudo dpkg -i splunk_package.deb
```

---

# Start Splunk

```bash
sudo /opt/splunk/bin/splunk start
```

---

# Enable Boot Start

```bash
sudo /opt/splunk/bin/splunk enable boot-start
```

---

# Access Splunk Web

Splunk Web was accessed through:

```text
http://localhost:8000
```

---

# Troubleshooting

Common troubleshooting steps included:

- Verifying Splunk service status
- Configuring VM networking
- Adjusting VirtualBox settings
- Installing desktop GUI packages

---

# Skills Demonstrated

- Linux administration
- Splunk Enterprise deployment
- Service management
- SIEM configuration
- Virtual machine administration
