<div align="center">
  
# Standard Operations Procedure For The Setup Of Standard Virtual Linux Server For Web Application Testing. #

## Tuchtech Ltd. ##
26 Kasmere Cove  
2048043950

### Purpose of Document ###
This document clearly outlines the steps for providing a secure and standard Linux Server virtual machine to host and test web applications in scalable environment.
</div>

### Scope ###
This procedures apply to; 
* Provide a standardized procedure for deploying a virtual Linux server for web application testing.
* Ensure consistency in environment setup, networking, and software installation.
* Facilitate reproducible test environments for developers and QA teams.

### Approval Table
| Role | Name | Signature| Date |
|-----|-------|------|----|
| Prepared by | Anthony |  |November 20, 2021 | 
| Reviewed by | David |  | November 10, 2022 |
| Approved by | Ben (Department Head) |  | November 15, 2025 | 
| Approved by | Richard (Manager) |  | November 18, 2025|
### Resources and Requirements
* Virtualization Platform: VMware Workstation / VirtualBox / Hyper-V
* Linux Distribution: Ubuntu Server 22.04 LTS (stable, widely supported)
* Hostname: webtest-server.local
* Networking:
    * Mode: Bridged or NAT depending on test requirements
    * Static IP: 192.168.1.40
    * Subnet: 255.255.255.0
    * Gateway: 192.168.1.1

* System Resources:
    * CPU: 2 vCPUs
    * RAM: 4 GB
    * Disk: 40 GB
* User Accounts:
    * admin (sudo privileges)
    * tester (restricted access for QA)
### Accountability Matrix

|Task	|Responsible Role|
|---|---|
|VM Creation	|System Administrator|
OS Installation	|System Administrator|
Package Installation	|DevOps Engineer|
Application Deployment|	Developer|
Testing	|QA Engineer|

### Procedure Steps 
#### Step 1: Create Virtual Machine
* Launch virtualization software.
* Allocate CPU, RAM, and disk resources.
* Attach Ubuntu Server ISO.
#### Step 2: Install Operating System
* Boot VM from ISO.
* Follow installation wizard.
* Set hostname: ```webtest-server.local```.
* Configure static IP networking.
#### Step 3: Update System using Bash
```sudo apt update && sudo apt upgrade -y```
#### Step 4: Install Essential Packages
* Web Server: Nginx or Apache
* Database Server: MySQL or PostgreSQL
* Scripting Language: PHP or Python (depending on app stack)
* Version Control: Git
* Testing Tools: Apache JMeter (for load testing)
* Security Tools: ufw firewall, fail2ban

```Bash
sudo apt install nginx mysql-server php git -y
sudo apt install openjdk-11-jre-headless
wget https://downloads.apache.org//jmeter/binaries/apache-jmeter-5.6.2.tgz
tar -xvzf apache-jmeter-5.6.2.tgz
```
#### Step 5: Configure Services
Enable and start Nginx:
