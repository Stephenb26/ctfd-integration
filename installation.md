# Installation

## Overview

This guide explains how to install and deploy the CTF Framework in a supported lab environment. The platform should be deployed on isolated infrastructure such as a dedicated virtual machine or lab server.

---

## Recommended Host Environment

Supported deployment options include:

- Ubuntu Server 22.04 or newer
- Debian Linux
- Dedicated Linux virtual machine
- Isolated lab server
- Cloud Linux instance for testing

Recommended minimum resources:

- 2 CPU cores
- 4 GB RAM
- 60 GB storage
- Internet access

For larger class environments, additional resources are recommended.

---

## Required Software

Install the following packages before deployment:

- Git
- Docker
- Terraform
- Python 3
- Curl
- Wget

---

## Deployment Steps

### Step 1 - Clone the Repository

git clone https://github.com/Build-Break-Repeat/CTF_Framework.git  
cd CTF_Framework

### Step 2 - Run Initial Setup

bash init.sh

This process installs dependencies, prepares configuration files, and initializes required services.

### Step 3 - Deploy the Environment

./ctfctl deploy

This step provisions the challenge environment, supporting services, and competition platform.

### Step 4 - Verify Running Services

docker ps

Confirm that core services such as CTFd and challenge containers are running.

### Step 5 - Access the Platform

Once deployment completes, access services through a web browser.

Examples may include:

- CTFd scoreboard
- Challenge web applications
- Reverse proxy hosted services

Access methods depend on configured ports and environment settings.

---

## Common Administrative Commands

./ctfctl deploy  
./ctfctl destroy  
./ctfctl rebuild  
./ctfctl reset  
./ctfctl bootstrap

---

## Troubleshooting

### Containers Not Starting

systemctl status docker

### Port Conflicts

ss -tulnp

### Permission Errors

chmod +x ctfctl  
chmod +x init.sh

---

## Security Recommendations

Deploy only in controlled environments:

- Dedicated VM
- Isolated VLAN
- Temporary training network
- No production exposure
- Firewall restricted access

---

## Updating the Platform

git pull  
./ctfctl rebuild

---
