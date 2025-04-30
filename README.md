# Miden Node Kurulum Reposu

Bu repo, Polygon Miden Node'u Docker kullanarak hızlı şekilde kurmak isteyen geliştiriciler için hazırlanmıştır.

Discord : [Buradan](https://discord.gg/AkSbwWXJ)
Twitter : [Buradan](https://x.com/FluidTokens)

## 🚀 Gereksinimler

- Docker & Docker Compose
- Git
- Minimum Sistem:
  - 4 vCPU
  - 8 GB RAM
  - 100 GB SSD
  - Ubuntu 20.04+ veya benzeri

## ⚙️ Kurulum Adımları

# Vespr Wallet indir ve yeni bir cüzdan oluştur testnet(Preview) ağına geç ve buradaki adresini kullan.

indir : [Buradan](https://chromewebstore.google.com/detail/vespr-wallet/bedogdpgdnifilpgeianmmdabklhfkcn?utm_source=vespr_website&utm_medium=header_download)
Faucet : [Buradan](https://docs.cardano.org/cardano-testnets/tools/faucet)


# Gerekli paketleri yükle
```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg lsb-release

#  Docker GPG anahtarını ekle
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Docker deposunu ekle
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Docker’ı kur
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Docker version kontrol et
docker compose version

# Docker Yetkisini Kullanıcıya Ver
sudo usermod -aG docker $USER
newgrp docker
```

### Git Kurulumu
```bash
sudo apt update
sudo apt install -y git
git --version
```

### Reposu Klonla
```bash
git clone https://github.com/FluidTokens/ft-aquarium-node.git
cd ft-aquarium-node
cd docker
```

### Ortam Dosyasını Hazırla
```bash
cp .env.example .env
nano .env
```
- `.env` dosyasındaki `BLOCKFROST_KEY` ve `WALLET_MNEMONIC` alanlarını doldurun ve ardından CTRL X + Y + ENTER diyerek kaydedip çıkın.
- Blockfrost API için [Buradan](https://blockfrost.io/) kaydolun ve bir API key alınız.

### Docker ile Node’u Başlat
```bash
docker compose up -d
```

### Logları Kontrol Et
```bash
docker logs aquarium-pg --tail 50
```


# Kurulum bittikten sonra Discord üzerinden ticket açınız ve yöneticiden testnet cüzdanınıza 30k tFLDT token isteyiniz. Sonra aşağıdaki siteden stake edeceğiz.

Link : [Buradan](https://aquarium-dev.fluidtokens.com/dashboard) 


### Durdurmak için
```bash
docker compose down
```
