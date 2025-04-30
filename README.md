# Aquarium Validator Node Installation Repository

This repo is prepared for developers who want to quickly set up an Aquarium Validator node using Docker.

Discord: [Join Here](https://discord.gg/AkSbwWXJ)  
Twitter: [Follow Here](https://x.com/FluidTokens)

# Installation Video

[![Setup Guide](https://img.youtube.com/vi/QlBXXYU5IpQ/0.jpg)](https://youtu.be/QlBXXYU5IpQ?si=Xkh_ec8bd2HOrprG)

## 🚀 Requirements

- Docker & Docker Compose
- Git
- Minimum System Requirements:
  - 4 vCPU
  - 8 GB RAM
  - 100 GB SSD
  - Ubuntu 20.04+ or similar

## ⚙️ Installation Steps

### 1. Download Vespr Wallet and create a new wallet

Switch to the **testnet (Preview)** network and use your wallet address.

- Download: [Click Here](https://chromewebstore.google.com/detail/vespr-wallet/bedogdpgdnifilpgeianmmdabklhfkcn?utm_source=vespr_website&utm_medium=header_download)  
- Faucet: [Click Here](https://docs.cardano.org/cardano-testnets/tools/faucet)

---

### 2. Install Required Packages

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg lsb-release

# Add Docker GPG key
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Add Docker repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Check Docker version
docker compose version

# Add Docker permissions to current user
sudo usermod -aG docker $USER
newgrp docker
```

---

### 3. Install Git

```bash
sudo apt update
sudo apt install -y git
git --version
```

---

### 4. Clone the Repository

```bash
git clone https://github.com/FluidTokens/ft-aquarium-node.git
cd ft-aquarium-node
cd docker
```

---

### 5. Prepare the Environment File

```bash
cp .env.example .env
nano .env
```

- Fill in the `BLOCKFROST_KEY` and `WALLET_MNEMONIC` fields in the `.env` file.  
- Save and exit using CTRL + X, then Y, then ENTER.  
- Get a Blockfrost API key from: [https://blockfrost.io](https://blockfrost.io)

---

### 6. Start the Node Using Docker

```bash
docker compose up -d
```

---

### 7. Check Logs

```bash
docker logs aquarium --tail 50
```

---

### 8. Final Steps

After completing the installation:

1. Open a ticket in the Discord server.
2. Request **30k tFLDT tokens** to your testnet wallet from the admin.
3. Then visit the following site to stake:

👉 [https://aquarium-dev.fluidtokens.com/dashboard](https://aquarium-dev.fluidtokens.com/dashboard)

---

### 🛑 To Stop the Node

```bash
docker compose down
```
