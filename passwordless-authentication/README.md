# Lab 01 - Passwordless SSH Authentication

## Overview

This lab demonstrates how to configure passwordless SSH authentication between two Ubuntu EC2 instances.

Passwordless authentication allows Ansible to connect to remote hosts securely without prompting for a password during automation tasks.

---

## Architecture

```
Ansible Server
      │
      │ SSH Key Authentication
      ▼
Target Server
```

---

## Environment

- AWS EC2
- Ubuntu 26.04 LTS
- Ansible
- SSH
- MobaXterm

---

## Lab Objectives

- Launch two Ubuntu EC2 instances
- Install Ansible
- Verify Ansible installation
- Generate SSH key pairs
- Configure SSH public key authentication
- Test passwordless SSH login

---

## Steps Performed

### 1. Create EC2 Instances

- ansible-server
- target-server

---

### 2. Install Ansible

Update packages

```bash
sudo apt update
```

Install Ansible

```bash
sudo apt install ansible
```

Verify installation

```bash
ansible --version
```

---

### 3. Generate SSH Keys

On the Ansible server

```bash
ssh-keygen
```

---

### 4. View Generated Keys

```bash
ls ~/.ssh
```

Public key

```
id_ed25519.pub
```

Private key

```
id_ed25519
```

> Never share your private key.

---

### 5. Copy Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

---

### 6. Configure Target Server

Generate SSH keys

```bash
ssh-keygen
```

Open

```bash
vim ~/.ssh/authorized_keys
```

Paste the copied public key.

---

### 7. Verify Passwordless Authentication

From the Ansible server

```bash
ssh <Target-Private-IP>
```

If the login is successful without asking for a password, passwordless authentication has been configured correctly.

---

## Result

Successfully established passwordless SSH authentication between the Ansible server and the target server.

---

## Skills Learned

- SSH
- SSH Key Authentication
- Public/Private Keys
- Linux CLI
- AWS EC2
- Ansible Installation
- Infrastructure Automation Fundamentals

---

## Reference

The practical steps documented in this lab are based on my own hands-on exercise, including installing Ansible, generating SSH keys, configuring `authorized_keys`, and verifying passwordless SSH connectivity between two EC2 instances. :contentReference[oaicite:1]{index=1}
