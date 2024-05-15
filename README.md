# Elastic SIEM Lab Setup

This repository provides step-by-step instructions to build an Elastic SIEM lab using a Kali Linux VM and push telemetry to it. This practical lab will give you hands-on experience with a SIEM tool, which is critical for SOC analyst work.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Setup Instructions](#setup-instructions)
    1. [Create Elastic Account](#create-elastic-account)
    2. [Set Up Kali Linux VM](#set-up-kali-linux-vm)
    3. [Configure Elastic Cloud](#configure-elastic-cloud)
    4. [Install Elastic Agent](#install-elastic-agent)
    5. [Generate Security Events](#generate-security-events)
    6. [Create and Visualize Dashboard](#create-and-visualize-dashboard)
    7. [Create Alerts](#create-alerts)
4. [Next Steps](#next-steps)
5. [References](#references)

## Introduction

This guide will help you build a home SIEM lab using Elastic SIEM and a Kali Linux VM. This lab will push telemetry from the Kali box into the Elastic Cloud and perform various interactions with the SIEM. 

## Prerequisites

- A computer with VirtualBox installed
- Internet connection
- Basic knowledge of Linux command line

## Setup Instructions

### 1. Create Elastic Account

1. Go to the [Elastic Cloud](https://www.elastic.co/cloud/) website.
2. Sign up for a free trial account. No credit card required.
3. Once signed in, click on "Create deployment."
4. Follow the on-screen instructions to create a new deployment.

### 2. Set Up Kali Linux VM

1. Download and install [VirtualBox](https://www.virtualbox.org/).
2. Download the [Kali Linux VM image](https://www.kali.org/get-kali/#kali-virtual-machines) for VirtualBox.
3. Open VirtualBox and create a new VM.
4. Select the downloaded Kali Linux VM image during setup.
5. Start the Kali Linux VM and ensure it has internet access.

### 3. Configure Elastic Cloud

1. Log in to your Elastic Cloud account.
2. Go to your deployment and click on the hamburger menu on the top left.
3. Click on "Integrations" and select "Elastic Defend."
4. Click "Add Elastic Defend" and then "Configure integration."
5. Select the desired settings and click "Save and continue."
6. Click "Add Elastic Agent to your host" and follow the instructions for Linux.

### 4. Install Elastic Agent

1. Copy the provided Linux command from the Elastic Cloud instructions.
2. In your Kali Linux VM, open a terminal and paste the copied command.
3. Run the command to install the Elastic Agent.
4. Verify the installation with:
    ```bash
    sudo systemctl status elastic-agent.service
    ```

### 5. Generate Security Events

1. In the Kali Linux terminal, run an nmap scan:
    ```bash
    sudo nmap -sT -sC localhost
    ```
2. This generates security events and logs.

### 6. Create and Visualize Dashboard

1. Go back to the Elastic Cloud interface.
2. Click on the hamburger menu and navigate to "Analytics" -> "Dashboard."
3. Click "Create dashboard" and then "Create visualization."
4. Select "Area" as the visualization type.
5. Set the vertical field to "count" and the horizontal field to "timestamp."
6. Click "Save" to save the visualization.

### 7. Create Alerts

1. Go to the hamburger menu and navigate to "Security" -> "Alerts."
2. Click "Manage rules" and then "Create new rule."
3. Select "Custom query" and use the following source:
    ```plaintext
    event.action: "nmap_scan"
    ```
4. Provide a descriptive name and details for the rule.
5. Set the desired actions (e.g., send an email, create a Jira ticket).
6. Save the rule.

## Next Steps

1. Add more agents to your network for additional telemetry.
2. Create more dashboards and alerts to robustly monitor security events.
3. Document your setup and experiments for use in job interviews.

## References

- [Elastic Cloud](https://www.elastic.co/cloud/)
- [VirtualBox](https://www.virtualbox.org/)
- [Kali Linux](https://www.kali.org/)
- [Simply Cyber](https://www.simplycyber.io/)
