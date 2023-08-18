# PowerPool
A repo on how to run and test a node in the PowerPool

```sh
# Benim cihazım:
4 CPU - 8 RAM - 150 SSD
Debian 10 (Ubuntuya da kurdum sorunsuz ufak farklılıklar oluyor size kalmış)
```

```sh
# ADIM-1, Sunucumuzu güncelleyelim:
sudo apt-get update && sudo apt-get upgrade -y
```

```sh
# ADIM-2, Docker ile dappnode'u kuruyoruz (tek tek giriniz):
sudo wget -O - https://prerequisites.dappnode.io | sudo bash
sudo wget -O - https://installer.dappnode.io | sudo bash
source /usr/src/dappnode/DNCORE/.dappnode_profile

# Durum kontrolü:
dappnode_status
```

```sh
# ADIM-3, Çıktıyı kaydedlim:
dappnode_wireguard
```

> [Buradan](https://www.wireguard.com/install/) WireGuard'ı indirelim.

> Görselde ki `boş tünel ekle` kısmına yukarıda kaydettiğimiz çıktıyı girelim (`dappnode_wireguard çıktısı`)

![image](https://github.com/ruesandora/PowerPool/assets/101149671/23e38061-fd30-4e7a-8cce-ca6eeb5cde39)

![image](https://github.com/ruesandora/PowerPool/assets/101149671/4c91073f-a34a-46d5-9261-51a28a406abf)

> Kaydettikten sonra etkinleştir diyoruz ve sunucumuza geri dönelim:

```sh
# ADIM-4, Gerekli paketleri indirelim:
sudo apt install git
sudo apt install nodejs
sudo apt install npm
```

```sh
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

```sh
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

```
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













