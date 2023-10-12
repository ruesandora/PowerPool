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
# ADIM-2, Docker ile dappnode'u kuruyoruz (tek tek giriniz):
sudo wget -O - https://prerequisites.dappnode.io | sudo bash
sudo wget -O - https://installer.dappnode.io | sudo bash
source /usr/src/dappnode/DNCORE/.dappnode_profile

# Durum kontrolü:
dappnode_status
```

```console
# ADIM-3, Çıktıyı kaydedlim:
dappnode_wireguard
```

> [Buradan](https://www.wireguard.com/install/) WireGuard'ı indirelim.

![image](https://github.com/ruesandora/PowerPool/assets/101149671/23e38061-fd30-4e7a-8cce-ca6eeb5cde39)

> Görselde ki `boş tünel ekle` kısmına yukarıda kaydettiğimiz çıktıyı girelim (`dappnode_wireguard çıktısı`)

![image](https://github.com/ruesandora/PowerPool/assets/101149671/19601e12-12a4-4455-bafd-07b9a4ae1eb0)

> Kaydettikten sonra etkinleştir diyoruz ve sunucumuza geri dönelim:

```console
# ADIM-4, Gerekli paketleri indirelim:
sudo apt install git
sudo apt install nodejs
sudo apt install npm
```

```console
# ADIM-5, sepolia-agent-standalone klonlayalım:
git clone https://github.com/eitelvolkerts/sepolia-agent-standalone
```

```console
# ADIM-6, agent'i klonlayalım:
git clone https://github.com/powerpool-finance/powerpool-agent-v2-compose
cd powerpool-agent-v2-compose
npm i
```

```console
# ADIM-7, PowerArgent yedek aldığımız  UTC--2023-08-18T09-32-40.364Z--8ccf..... dosyamızı Winscp tarzı bir uygulama ile
> "sepolia-agent-standalone/keys/" içine taşıyalım ve "yourkeygoeshere" yazan dosyayı silelim..
> Aşağıdaki dosyada gerekli yerleri düzeltip kaydedip çıkıyoruz ( CTRL+X y enter)

nano sepolia-agent-standalone/config/main.yaml

> rpc: 'wss://sepolia-geth-ws.863d6819366102aa.dyndns.dappnode.io'
> agents:
>           '0xbdE2Aed54521000DC033B67FB522034e0F93A7e5':
```
![image](https://github.com/ahmkah/PowerPool/assets/99053148/af846c7d-001a-4752-90c2-892795e1fa26)

```console
# ADIM-8, Şimdi Nodu Çalıştıracağız:

cd sepolia-agent-standalone

docker-compose pull

docker compose up -d
```

```console
# ADIM-9, Log kontrolü yapalım:

docker logs -f sepolia-agent-standalone-bot-1
```

![image](https://github.com/ahmkah/PowerPool/assets/99053148/9fbc36d0-da82-42c5-8c34-2557a796cfe9)

```console
# ADIM-10, Dappnode Entegrasyonu yapıp logları daha kolay izleyebiliriz başlayaım:
> Önce Wireguard ile node bağlanıyoruz ve Dappstore kısmına gelip aşağıdaki hash aratalım ve bypass alıp kuralım.

>   /ipfs/QmULaiokk8QZXdBNq4VbgsZnSEEeczG1qrLgZrbnDp6UHp

>  Şimdi configürasyonu yapıyoruz bu kısmı herkes bildiği için detaya girmiyorum. 

```
![image](https://github.com/ahmkah/PowerPool/assets/99053148/d3681136-db1b-4b78-8bc6-dc622f2df3e5)

```console

> Aşama-1: Worker cüzdan adresimizi girelim

> Aşama-2: Worker Key olarak bilgisayarımıza yüklediğimiz UTC'li klasörü sürükleyelim.

> Aşama-3: Keyfile Password için: `node jsongen.js <> <>` komutunda kullandığımız şifreyi girelim.

> Aşama-4: Network'ü Sepolia olarak seçelim.

> Aşama-5: RPC olarak bu bağlantıyı girelim: `wss://sepolia-geth-ws.863d6819366102aa.dyndns.dappnode.io`

> Aşama-6: Agent adresi girelim: `0xbdE2Aed54521000DC033B67FB522034e0F93A7e5`

> Aşama-7: Logging level girelim : `debug`

> Aşama-8: her iki değeride `true` , `true` girin

> Aşama-9: Value'leri true, gas'ı'da 60,000 yapıp, submit diyoruz.

```
![image](https://github.com/ahmkah/PowerPool/assets/99053148/3ef81bd0-a9da-46ed-aeef-f6255b986dd1)















