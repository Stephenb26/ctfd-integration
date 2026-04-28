# Architecture

## Overview

CTF Framework is a modular cybersecurity training platform designed to automate the deployment of Capture the Flag environments. The system combines infrastructure provisioning, container orchestration, centralized scoring, and challenge hosting into a single manageable framework.

The architecture is intended to support educational instances and not to be used for production environments.

---

## High-Level Design

```text
Users / Students
       |
       v
Web Browser Access
       |
       v
Reverse Proxy (Caddy)
       |
-------------------------------------------------
|                       |                       |
v                       v                       v
CTFd                Web Challenges         System Targets
Scoreboard          DVWA                  Metasploitable
Admin Portal        Juice Shop            Windows Labs
                    WebGoat
                    bWAPP
                    SQL Labs
```

---

## Core Components

### 1. User Access Layer

Participants access the environment through a standard web browser.

Users may interact with:

* CTFd scoreboard
* Challenge platforms
* Vulnerable web applications
* Hosted lab targets

This allows students to participate without complex local setup.

---

### 2. Reverse Proxy Layer

Caddy is used as the reverse proxy layer.

Responsibilities include:

* HTTPS handling
* Service routing
* Centralized access point
* Cleaner URLs
* Simplified external connectivity

---

### 3. Competition Management Layer

CTFd serves as the central competition platform.

Features include:

* User registration
* Team creation
* Challenge listings
* Flag submission
* Score calculation
* Live leaderboard
* Administrative controls

---

### 4. Challenge Hosting Layer

Vulnerable environments are deployed as isolated containers or targets.

Examples include:

* DVWA
* OWASP Juice Shop
* WebGoat
* bWAPP
* SQL Injection Labs
* Metasploitable
* Windows vulnerable systems

Each challenge can be independently managed or rebuilt.

---

### 5. Automation Layer

Administrative control is handled through scripts and utilities.

Examples include:

* init.sh
* ctfctl
* Terraform files
* Python automation scripts

Used for:

* Initial setup
* Deployment
* Rebuilds
* Environment resets
* Bootstrap tasks
* Challenge lifecycle management

---

### 6. Configuration Layer

Centralized configuration files such as `config.json` define environment behavior.

Examples include:

* Enabled challenges
* Port assignments
* Event settings
* Deployment preferences
* Team configuration values

This allows repeatable deployments with minimal manual changes.

---

## Security Model

Because vulnerable systems are intentionally deployed, the framework is intended for isolated use only.

Recommended safeguards:

* Dedicated VM or server
* Separate VLAN or lab network
* Firewall restrictions
* Temporary deployment windows
* No production network exposure

---

## Scalability

The modular architecture supports future expansion such as:

* Additional challenge containers
* Cloud hosting
* Multi-team competitions
* Persistent scoring databases
* Monitoring dashboards
* Role-based administration

---

## Summary

The CTF Framework architecture emphasizes automation, modularity, and ease of deployment. By combining containerized labs with centralized competition management, the platform provides a practical solution for cybersecurity education and training.
