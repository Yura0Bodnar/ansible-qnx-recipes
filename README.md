# QNX 7.1 Telemetry Edge Agent Provisioning (PoC)

This repository contains a Proof of Concept (PoC) Ansible playbook for the automated deployment of software (Software Recipes) on bare-metal QNX 7.1 systems.

Currently, the playbook demonstrates the installation and configuration of an Automotive Telemetry Edge Agent (mock) for collecting CAN bus data.

## Setup Instructions

1. **Clone the repository and navigate to the directory:**
```bash
git clone <YOUR_REPOSITORY_URL>
cd ansible-qnx-poc

```


2. **Create and activate a virtual environment:**
```bash
python3 -m venv .venv
source .venv/bin/activate

```


3. **Install dependencies (Ansible core):**
```bash
pip install -r requirements.txt
# Or manually: pip install ansible ansible-lint

```

4. **Configure the inventory:**
The project uses a secure approach without hardcoding passwords. Copy the template file:
```bash
cp inventory.example.ini inventory.ini

```

Open `inventory.ini` and specify the real IP address of your QNX server and the username. **Do not add the password to this file.**

## Running the Playbook

Execute the following command to start the deployment. The `-k` (or `--ask-pass`) flag will force Ansible to securely prompt for the QNX server password in the terminal:

```bash
ansible-playbook playbook.yml -i inventory.ini -k

```

**Expected Result:**
Ansible will connect to QNX, create the `/tmp/telemetry_agent` structure, generate the `agent_config.json` configuration file, create the executable agent file, and return the log of its successful launch to your terminal.