# Build Break Repeat - Infrastructure Foundation

# CTF Framework

## Overview

CTF Framework is an automated Capture the Flag deployment platform developed to simplify the setup, management, and delivery of cybersecurity training environments. The framework allows instructors, students, and organizations to deploy a complete CTF event with vulnerable targets, web application labs, and a centralized scoring system in significantly less time than traditional manual builds.

This project combines infrastructure automation, containerized challenges, and competition management into a single framework that can be deployed, rebuilt, or removed through simple command-line controls.

---

## Team

Build Break Repeat

---

## Features

* Automated CTF environment deployment
* Centralized scoreboard powered by CTFd
* Support for vulnerable web applications and lab targets
* Containerized challenge hosting
* Reverse proxy support for simplified access
* Automated challenge and flag management
* Rebuild, reset, and destroy controls
* Expandable challenge architecture
* Designed for classroom, workshop, and lab environments

---

## Supported Platforms

Depending on selected configuration, the framework can deploy environments such as:

* DVWA
* OWASP Juice Shop
* WebGoat
* bWAPP
* Metasploitable
* SQL Injection Labs
* Custom Docker-based challenges

---

## Technologies Used

* Docker
* Terraform
* Git
* Bash
* Python 3
* Curl
* Wget
* CTFd
* Caddy Reverse Proxy

---

## Project Structure

CTF_Framework/
├── cmd/
├── scripts/
├── terraform/
├── tests/
├── config.json
├── init.sh
├── ctfctl
├── README.md

---

## Requirements

Install the following before deployment:

* Docker
* Terraform
* Git
* Curl
* Wget
* Python 3

---

## Installation

Clone the repository:

git clone https://github.com/Build-Break-Repeat/CTF_Framework.git
cd CTF_Framework

Run initialization:

bash init.sh

---

## Core Commands

Deploy:

./ctfctl deploy

Destroy:

./ctfctl destroy

Rebuild:

./ctfctl rebuild

Reset:

./ctfctl reset

Bootstrap CTFd:

./ctfctl bootstrap

List Challenges:

./ctfctl challenge list

---

## Flag Management

Generate team-based flags:

python3 scripts/createflags.py 3

Generate flags using a preset:

python3 scripts/createflags.py 3 --preset lab

List available presets:

python3 scripts/createflags.py --list-presets

Inject generated flags into running challenge containers:

python3 scripts/injectflags.py

### Current Workflow

1. Challenge names are loaded from config.json
2. Flag files are written to flags/<challenge-name>.txt
3. injectflags.py copies team flag files into matching containers
4. Flags are stored inside /flags in each container

---

## CTFd Integration

The framework uses CTFd as the central competition platform for:

* User registration
* Team management
* Challenge scoring
* Live scoreboard
* Administrative control
* Challenge imports

---

## Testing

Validation checks and deployment testing are stored in the tests/ directory.

---

## Security Considerations

This framework is intended only for controlled training environments.

Recommended usage:

* Dedicated VM
* Isolated VLAN
* Temporary lab deployment
* Firewall restrictions
* No production network exposure

---
