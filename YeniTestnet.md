<h1 align="center">Fleek Network</h1>


> Hocam Fleek testneti ne kadar sürecek? - Cevabı [burada.](https://blog.fleek.network/post/fleek-network-testnet-phase0/)

> Hocam ödüllü mü? - Cevabı [burada.](https://blog.fleek.network/post/fleek-network-testnet-plans/)

> Arkadaşlar ricamdır şunla şu yan yana kurulurmu sorusunu artık sormayın.

> Topluluk kanalları: [Duyurular](https://t.me/RuesAnnouncement) - [Sohbetler](https://t.me/RuesChat) - [Discord](https://discord.gg/V2rX68cy)

<h1 align="center"> Donanım </h1>

> Kendim kurduğum donanım, [Hetzner](https://hetzner.cloud/?ref=gIFAhUnYYjD3) kullandım.

> Sunucu şifrenizi unutmayın, Fleek'ten kaynaklanan bir bugdan ötürü `qemu-guest` siliniyor ve şifre yenileyemiyorsunuz.

```console
# Ubuntu 22.04 şart. 
4 CPU 8 RAM
```

<h1 align="center"> Kurulum </h1>

```console
# Güncellemelerimiz
sudo apt update && sudo apt upgrade -y

sudo fallocate -l 10240M /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# rust ve kütüphaneleri yüklüyoruz seçeneklerde 1'i seçiyoruz:
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustup update
```

```console
# Script ile kuruyoruz aşamalar çok uzun sürebilir, sunucu performansınıza bağlı.
curl https://get.fleek.network | bash
# Yes/No sorularına 2 kez Yes yazıyoruz.
# Kurulum bitince ENTER diyelim.

# Servisi başlatalım. Tek Tek girin
sudo systemctl start lightning.service
sudo systemctl stop lightning.service
sudo systemctl restart lightning.service
# Tavsiyem bu komutları iki tur giriniz.
```
<h1 align="center"> Node'un seçilmesi için gerekli işlemler </h1>

```console
# cargoyu yükleyelim
sudo apt install cargo -y
cd fleek-network/lightning/target
# Bu key oluşumu uzun sürer
cargo run -r -- keys generate
# Kodun sonunda hata verebilir, show komutunu kullanın.
# Show dediğinizde ki bilgileri kaydedin
cargo run -r -- keys show

# Discordda, #access-form kanalına gidiyoruz, become node operator diyoruz.
# Daha sonra IP ve show dediğimizde ki bilgileri buraya girip ticket oluşturuyoruz.
```

> Seçilirseniz görselde ki gibi bir mesaj alacaksınız:

![image](https://github.com/ruesandora/Fleek-Network/assets/101149671/6bfe7302-c3ca-49e2-9c1b-555f61e67760)

