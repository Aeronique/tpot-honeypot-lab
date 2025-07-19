# Cloud Threat Luring: T-Pot 24.04.1 on Google Cloud Platform

Welcome to part one of my honeypot analysis project. In this guide, I'll walk you through deploying and configuring a T-Pot honeypot on Google Cloud Platform (GCP). The goal is to observe attacker playbooks in real traffic, capture and parse malicious payloads at scale, and automate infrastructure deployment and monitoring via infrastructure-as-code.

## Table of Contents
- [Prerequisites](#prerequisites)
- [GCP VM Configuration](#gcp-vm-configuration)
- [Firewall Configuration](#firewall-configuration)
- [T-Pot Installation](#t-pot-installation)
- [Accessing the T-Pot Dashboard](#accessing-the-t-pot-dashboard)
- [What I Learned](#what-i-learned)
- [Next Steps](#next-steps)
- [Author](#author)

## Prerequisites

- A Google Cloud account with a verified payment method  
- $300 free trial credit (valid for 90 days)  
- Basic familiarity with Linux shell and Git  
- (Recommended) Google Pay enabled on your account

## GCP VM Configuration

1. **Machine Type**  
   - Minimum: 8 GB RAM (16 GB recommended)  
   - Storage: 128 GB boot disk  
   - Estimated cost: ~$50/month (covered by free trial)

2. **Operating System**  
   - Ubuntu 24.04 LTS Minimal (x86_64)  
   - Increase boot disk from default 10 GB to 128 GB

3. **Networking & Data Protection**  
   - Enable HTTP and HTTPS traffic  
   - In Observability, disable backups and turn off the Ops Agent

4. **Create the VM**  
   - Click **Create** in the Compute Engine console  
   - Wait ~2–5 minutes for it to boot

## Firewall Configuration

1. In the VM details, enable **Set up firewall rules**  
2. Create a rule with:  
   - **Targets**: All instances in the network  
   - **Source IPv4 ranges**: `0.0.0.0/0`  
   - **Protocols and ports**: Allow all  

## T-Pot Installation

SSH into your VM (do **not** switch to root; use your default sudo-enabled user):

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git -y
git clone https://github.com/telekom-security/tpotce
cd tpotce
./install.sh
```
