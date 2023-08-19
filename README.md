<h1 align="center"> Power Pool </h1>

> Eğer seçildiyseniz ve token aldıysanız bu floodu kullanın aksi taktirde vakit kaybıdır

```console
# Benim cihazım:
4 CPU - 8 RAM - 150 SSD
Debian 10 (Ubuntuya da kurdum sorunsuz ufak farklılıklar oluyor size kalmış)
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
# ADIM-5, agent'i klonlayalım:
git clone https://github.com/powerpool-finance/powerpool-agent-v2-compose
cd powerpool-agent-v2-compose

npm i
```

> Şimdi [Buradan](http://my.dappnode/#/) dappnode üzerine gidiyoruz.

> [Bu](http://my.dappnode/#/installer/%2Fipfs%2FQmT2vSKsKVTs7oFxYnnzb8cpWiKnMDvPLy1qnaLWfEfVkD) ve [Bu](http://my.dappnode/#/installer/%2Fipfs%2FQmNy6zTZM9LfHomWJpNYFWX6kJqz9Jgm5eragJagMwc4jk) linklere tıklayarak iki ayrı sayfa açalım.

> Görselde ki gibi bu paketlerde sağdan `advanced options` ile `solda ki tikleri` açıyoruz. (1 veya 2 tane olur hepsini açın)

> Sonra karşınıza çıkan seçenekleri next next diyerek kuruluma başlayın.

![image](https://github.com/ruesandora/PowerPool/assets/101149671/ca513c20-a7ef-4cbf-80ca-44a782374582)

> BURADA: görselde ki gibi `Prism Sepolia` ve `Sepolia GETH` sync olmasını bekleyin, `Sepolia GETH 1-2 saat sürebilir` sunucunuza bağlı:

![image](https://github.com/ruesandora/PowerPool/assets/101149671/58c04f85-b8fd-41fc-8086-e4c9316e7b87)

> SYNC OLURKEN BİZ DİĞER İŞLEMLERİ YAPALIM!

> Şimdi 1 metamask cüzdanınız olsun, içinde 2 account. 1. account Admin, 2. account Worker cüzdanı olsun.

![image](https://github.com/ruesandora/PowerPool/assets/101149671/d93ed926-9ba0-44ac-b57b-ca184b5a3415)

> Worker cüzdanın `metamasktan private key'ini` alınız. (Hesap bilgileri kısmından)

> Daha sonra aşağıda ki komutu doldurup sunucunuzda bu komutu giriniz.

```console
cd powerpool-agent-v2-compose
# Tırnakları <> kaldırınız:
node jsongen.js <worker_private_key> <password>
```

> Çıkan `UTC'li klasörü masa üstünüze atın ve saklayınız!` (Node taşımak isterseniz bu klasör ve metamask cüzdanlarınız gerekecek)

> Şimdi `Admin cüzdan adresiniz` ile telegramda dahil olduğunuz grupta `tCVP kanalından` token isteyin.

> [Bu](https://sepolia.etherscan.io/address/0xD5134EcD90EB63276aF2Fca897cC04D845AfD74f#writeContract#F1) kontrata gidiniz ve metamaskı bağladıktan sonra `aşağıda ki değerleri` giriniz:

```
# Değerler:
0xc8E864f12c337Bdf6294a3DCeE0E565D2B1B4d90
1000000000000000000000
```

![image](https://github.com/ruesandora/PowerPool/assets/101149671/a9c1a8b6-2ee6-48e0-8ecb-4751570c12b3)

> İlk işlemin onaylanmasını bekleyin, onaylandıysa [bu](https://sepolia.etherscan.io/address/0xc8E864f12c337Bdf6294a3DCeE0E565D2B1B4d90#writeContract#F17) kontrata gidiniz ve aşağıda ki değerleri girin:

```console
# Değerler:
Worker CÜZDAN ADRESİ (private key değil)
3000000000000000000000 (Buraya size verilen tokeni girebilirsiniz, genelde 3000 verilir siz kontrol edin yinede)
```

![image](https://github.com/ruesandora/PowerPool/assets/101149671/4615ba81-a938-44da-bb35-87ded38b07bd)

> [Buraya](https://sepolia.etherscan.io/address/0xc8E864f12c337Bdf6294a3DCeE0E565D2B1B4d90#readContract#F27) Worker Adresinizi aratın

> Size bir KeeperID verecek (Mesela `35` gibi)

![image](https://github.com/ruesandora/PowerPool/assets/101149671/ea366421-f65f-4212-9a56-9427ffde42d1)

> [Buraya'da](https://sepolia.etherscan.io/address/0xc8E864f12c337Bdf6294a3DCeE0E565D2B1B4d90#readContract#F13) size az önce verilen KeeperID'ınızı aratın bakalım, admin ve Worker adresiniz doğru mu kontrol edin.

![image](https://github.com/ruesandora/PowerPool/assets/101149671/8c8dc8c6-a09d-4d37-be60-5ca81d16161f)

> SYNC OLDUYSANIZ BURDAN SONRA DEVAM EDİNİZ, DASHBOARD'DAN SYNC DUMUNUZU KONTROL EDİNİZ.

Şimdi en önemli kısım:

> [Buradan](http://my.dappnode/#/installer/%2Fipfs%2FQmP55bcEhtWtrbiueisuoZx4XN5AeLsuvtKU6CFoTG52GF) Poweragent'i çalıştracağız:

> Aşama-1: Yine advanced optionsdan tiki açalım

> Aşama-2: Worker cüzdan adresimizi girelim

> Aşama-3: Worker Key olarak bilgisayarımıza yüklediğimiz UTC'li klasörü sürükleyelim.

> Aşama-4: Keyfile Password için: `node jsongen.js <> <>` komutunda kullandığımız şifreyi girelim.

> Aşama-5: Network'ü Sepolia olarak seçelim.

![image](https://github.com/ruesandora/PowerPool/assets/101149671/3b5ffef5-ead1-4c61-86ee-405af16052f9)

> Aşama-6: RPC olarak bu bağlantıyı girelim: `ws://sepolia-geth.dappnode:8546`

> Aşama-7: Agent adresi girelim: `0xc8E864f12c337Bdf6294a3DCeE0E565D2B1B4d90`

> Aşama-8: Burada agent adresinden sonra 3 satırı boş bırakıyoruz son 3 satıra gelelim.

> Aşama-9: Value'leri true, gas'ı'da 60,000 yapıp, submit diyoruz.


<h1 align="center"> Doğru Log böyle akar </h1>

![image](https://github.com/ruesandora/PowerPool/assets/101149671/6b760bb5-6030-4648-ae3a-a03f4d98388c)
















