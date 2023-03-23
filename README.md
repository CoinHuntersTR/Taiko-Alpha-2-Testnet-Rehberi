# Taiko-Alpha-2-Testnet-Rehberi

![Taiko-Node-Testi](https://mirror-media.imgix.net/publication-images/4qVW-dWhNmMQr61g91hGt.png?height=512&width=1024&h=512&w=1024&auto=compress)


### Önerilen Sistem Gereksinimleri;

|CPU | RAM  | Disk  | 
|----|------|----------|
|  16| 32GB  | 1 TB   |

 # Daha önce Node kurulumu yapmadıysanız buradan sırasıyla adımları takip ederek tüm süreci öğrenebilirsiniz.
  ## Yeni Başladım Rehberi; <a href="https://coinhunterstr.com/category/testnet/" target="_blank"> Coin Hunters </a>
  ### 1. [Testnet ve Node test kurulum rehberi Bölüm-1](https://coinhunterstr.com/testnet-ve-node-kurulum-rehberi/)
  ### 2. [Yeni Chrome Tarayıcı nasıl açarım?](https://coinhunterstr.com/yeni-chrome-tarayici-nasil-acarim/)
  ### 3. [Ücretsiz Sunucu Kiralama](https://coinhunterstr.com/ucretsiz-sunucu-nasil-kiralarim/)
  ### 4. [Digital Ocean Nasıl Kayıt olurum?](https://coinhunterstr.com/digital-oceana-nasil-kayit-olabilirim/)
  ### 5. [MobaXTerm Terminal Kurulumu](https://coinhunterstr.com/mobaxterm-terminal-kurulumu/)
  
## UYARI

Taiko Node testneti ETH üzerinde ZKP ve gizlilik odaklı bir L2 çözümü, ödül ve yatırımcılar konusunda henüz bir açıklama yok. Bu nedenle kurup kurmamak size kalmış. Biz kurduğumuz için rehberini yayınlıyoruz.


## Kurulum:
* Komutları tek tek girin.

```
sudo apt update 
```
```
sudo apt upgrade
```
```
apt install docker-compose
```
```
sudo apt-get update && sudo apt install jq && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```

## Repoyu Klonluyoruz.
```
git clone https://github.com/taikoxyz/simple-taiko-node.git
cd simple-taiko-node
```
## Ayrı screende çalıştıracağız:
```
screen -S taiko
```

## İçine girip düzenlemeler yapıyoruz:
```
cp .env.sample .env
nano .env
```
## Bu kısıma devam etmeden önce sıfırdan metamask oluşturup token alıyoruz, veya testnetler için kullandığın metamaskı'ın private key anahtarı gerekiyor.
### Metamask Private Key alma;
> Metamask cüzdanımızı oluşturduktan sonra; Aşağıda bulunan görseldeki adımları takip ederek private key'inizi alabilirsiniz.
![matemask-private-key](https://user-images.githubusercontent.com/111747226/214062437-69e144d9-528f-4a17-b46a-a747c1d5284c.png)

## Taiko Platform Testnet Rehberine  <a href="https://coinhunterstr.com/taiko-genel-platform-testneti/" target="_blank"> Buradan </a>

## Metamask Cüzdanınıza Taiko A1 ağını ekleme;
Taiko A1 ağını cüzdanınıza ekleyin.
<a href="https://taiko.xyz/docs/alpha-1-testnet-guide/configure-wallet" target="_blank"> Taiko A1 Ağını Ekleme </a>

## Taiko Faucet
Ethereum A1 için Faucetten token isteyin.
<a href="https://taiko.xyz/docs/alpha-1-testnet-guide/request-from-faucet" target="_blank"> Taiko A1 Ağını Faucet </a>


## Yukarıdaki komutları girince açılacak ekran görselde ki gibi.

* Açıldıktan sonra yön tuşları ile en alta geliyoruz.
* `ENABLE_PROVER` kısmını `true` yapıyoruz
* `L1_ENDPOINT_WS` infura sitesinden aldığımız URL ekleyeceğiz.
* `L1_PROVER_PRIVATE_KEY`bu kısımda `Metamask private key adresini giriyoruz.
* sonra CTRL + X + Y ile çıkıyoruz.
![matemask-private-key](https://user-images.githubusercontent.com/111747226/214062489-2d490776-a29e-4b2d-9899-46ad5faf534b.png)




## Node'u çalıştırın:
```
docker compose up -d
```
## Node'unuz çalışıyor kolay gelsin:

![taiko-node](https://user-images.githubusercontent.com/111747226/214062692-63e3c271-754f-42a7-a7b0-09a75c690aaa.png)

## Nasıl Çalıştığını görmek için
> Aşağıdaki komutu yazıyoruz.
```
docker container ls
```
>Aşağdaki görsele işaretlediğim satırdakine benzer kod alacaksınız., "CONTANIER ID yazan rakamları bir yere not edin.
![docker-id](https://user-images.githubusercontent.com/111747226/214063387-4d6d696c-01f8-46d2-a760-26942361de98.png)


## Nasıl Çalıştığını görmek için
> Yukarıdaki görselde "CONTAINER ID" alıyoruz. CONTAINER ID yazan yere, ekleyip çalıştırınca node durumunu görebilirsiniz.
```
docker logs CONTAINER ID --follow
```

## İnfura'dan nasıl Sepolia URL alıyoruz.
- [BURADAN](https://www.infura.io/) sitesine gidiyoruz ve kayıt oluyoruz. Mailimize gelen doğrulamaya basarak siteye ulaşıyoruz.

![api key](https://user-images.githubusercontent.com/111747226/227228287-230a3086-1057-4d6b-a8e1-47df7666900c.png)

- Girdiğimizde Web API seçiyoruz. Projeye bir isim veriyoruz. "Create" tuşuna basıyoruz.

![infura-devam](https://user-images.githubusercontent.com/111747226/227228880-df89ca3f-8bc3-4faf-8413-b646280c59f7.png)
- Açtığımız projenin içine giriyoruz. "WebSockets" bölümüne geçiyoruz. Sağ tarafta görebilirsiniz.
- Ethereum'a geliyoruz. "mainnet" yazan yere basıyoruz. Orada "Sepolia" ağını seçiyoruz hemen yan tarafından URL adresi çıkacak bunu kopyalıyoruz. Yukarıda not olarak yazdığım yere bu URL yapıştırıyoruz.


## Dashboard Kurulumu
- Burada IP adresi olan yere aldığınız sunucunun IP adresini ekliyorsunuz.

```
http://IPADRESİN:3000/d/L2ExecutionEngine/l2-execution-engine-overview?orgId=1&refresh=10s
```




## Taiko Discord kanalına katılmayı unutmayın;
### [Discord](https://discord.gg/taikoxyz)

## Yarım için telegram kanalımız;
### [Coin Hunters Telegram](https://t.me/CoinHuntersTR)
