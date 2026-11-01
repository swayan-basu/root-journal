# Instant Lab

Instant Lab is a Docker-based cybersecurity practice environment for Raspberry Pi and Linux systems. It provides an interactive terminal dashboard for launching security tools, intentionally vulnerable web applications, and monitoring stacks.

> **Warning:** Use this project only in an isolated lab or against systems you own or are explicitly authorized to test.

> 📦 **Quick Install:** Don't want to clone manually? Install officially via Snap: `sudo snap install instant-lab`

## Features

- Interactive launcher for all lab services
- Docker installation and daemon checks
- Port conflict checks before services start
- Parrot Security and Kali Linux containers
- Nuclei vulnerability scanner
- DVWA, OWASP Juice Shop, and bWAPP targets
- ELK and Wazuh monitoring stacks
- Wazuh agent deployment
- Container status and cleanup utilities

## Requirements

- Linux system, Raspberry Pi, or another linux compatible computer
- At least 4 GB RAM recommended for the ELK or Wazuh stacks

The security-tool containers may require additional CPU, memory, and disk space. Start only the services needed for your exercise.

## Quick Start (Manual Setup)

Clone the repository:

```bash
git clone https://github.com/swayan-basu/Instant_lab.git
cd Instant_lab
chmod +x start_main.sh
find scripts -type f -name '*.sh' -exec chmod +x {} + (optional)
./start_main.sh
```
<img width="1214" height="758" alt="wazuh52" src="https://github.com/user-attachments/assets/9121d4cc-71b2-494d-b9cd-5d38e9e74420" />

## Direct Service Launchers

Every service can be started without the dashboard. Run commands from the repository root:

* **Scanners:**
```
bash scripts/scanners/start_parrot.sh
bash scripts/scanners/start_rkali.sh
bash scripts/scanners/start_nuclei.sh
```
* **Vulnerable Targets:**
```
bash scripts/targets/start_dvwa.sh
bash scripts/targets/start_juice.sh
bash scripts/targets/start_bwapp.sh
```
* **SIEM/Monitoring:**
```
bash scripts/siem/start_elk.sh
bash scripts/siem/start_wazuh.sh
bash scripts/siem/start_wazuh_agent.sh
```
<img width="1215" height="759" alt="wazuh02" src="https://github.com/user-attachments/assets/05ae7ed9-a708-45bf-b291-5f949a39193c" />

## Distribution

### Install via Snap Store

[![Get it from the Snap Store](https://snapcraft.io/en/dark/install.svg)](https://snapcraft.io/instant-lab)

You can install Instant Lab directly from the Snap Store. Because Instant Lab provisions and manages local containers, it requires access to the Docker daemon. 

For security reasons, this connection must be granted manually after installation:

```bash
# 1. Install the snap
sudo snap install instant-lab

# 2. Grant Docker access
sudo snap connect instant-lab:docker docker:docker-daemon

# 3. Launch Instant Lab
instant-lab
```

### Wazuh Default Credentials

For the single-node configuration:

* **Username:** admin
* **Password:** SecretPassword

(Note: The Wazuh dashboard uses a self-signed certificate, so a browser warning may appear on first access. Change the password before allowing access from another network.)


## Security and Legal Notice

DVWA, Juice Shop, bWAPP, and the security-tool containers are intended for authorized training and testing. Keep the lab on a private network, do not expose vulnerable services to the public internet, and obtain permission before testing any system that you do not own.

[View Source Code on GitHub](https://github.com/swayan-basu/Instant_lab)
