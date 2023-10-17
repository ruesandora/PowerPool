<h1 align="center"> Power Pool </h1>

> Eğer seçildiyseniz ve token aldıysanız bu floodu kullanın aksi taktirde vakit kaybıdır

```console
# Benim cihazım:
2CPU - 4 RAM - 80 SSD
Ubuntuya 22.04 
```

```console
# ADIM-1, Sunucumuzu güncelleyelim:
sudo apt-get update && sudo apt-get upgrade -y
```

```console
# ADIM-2, Docker ve Docker Compose Kuruyoruz (tek tek giriniz):

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
sudo systemctl enable docker

docker --version

sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version

```

```console
# ADIM-3, Gerekli paketleri indirelim:
sudo apt install git
sudo apt install nodejs
sudo apt install npm
```

```console
# ADIM-4, sepolia-agent-standalone klonlayalım:
git clone https://github.com/eitelvolkerts/sepolia-agent-standalone
```

```console
# ADIM-5, agent'i klonlayalım:
git clone https://github.com/powerpool-finance/powerpool-agent-v2-compose
cd powerpool-agent-v2-compose
npm i
```

```console
# ADIM-6, PowerArgent yedek aldığımız  UTC--2023-08-18T09-32-40.364Z--8ccf..... dosyamızı Winscp tarzı bir uygulama ile
> "sepolia-agent-standalone/keys/" içine taşıyalım ve "yourkeygoeshere" yazan dosyayı silelim..
> Aşağıdaki dosyada gerekli yerleri düzeltip Worker Adres ve Şifreyi değiştirmeyi unutmayın, kaydedip çıkıyoruz ( CTRL+X y enter)

nano sepolia-agent-standalone/config/main.yaml

> rpc: 'wss://sepolia-geth-ws.863d6819366102aa.dyndns.dappnode.io'
> agents:
>           '0xbdE2Aed54521000DC033B67FB522034e0F93A7e5':
```
![image](https://github.com/ahmkah/PowerPool/assets/99053148/af846c7d-001a-4752-90c2-892795e1fa26)

```console
# ADIM-7, Şimdi Nodu Çalıştıracağız:

cd sepolia-agent-standalone

docker-compose pull

docker compose up -d

# Docker cont. silmek için aşağıdaki komut giriyoruz:

docker compose down --rmi local
```

```console
# ADIM-8, Log kontrolü yapalım:

docker logs -f sepolia-agent-standalone-bot-1
```
```console
# ADIM-9, Log dosyasını kaydetmek için aşağıdaki komudu girin:

docker logs sepolia-agent-standalone-bot-1 >& powerargentlogfile.log

```














