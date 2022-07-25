# <h1 align="center">Stratos sds</h1>

![stratos](https://user-images.githubusercontent.com/73015593/177883166-54990a2a-2b9d-4e27-9559-0aed1c36f3f8.jpg)

# Node kurulumu 

## root yetkisi kazanıyoruz.
```
sudo su
```

## root dizinine gidiyoruz.
```
cd /root
```

## Sistem güncellemesi yapıyoruz.
```
sudo apt update && sudo apt upgrade -y
```
![image](https://user-images.githubusercontent.com/73015593/180839997-c55fa8b7-8938-4749-a249-c0d066b0e39c.png)

## Kütüphane kurulumu yapıyoruz.
```
sudo apt install make clang pkg-config libssl-dev build-essential git jq ncdu bsdmainutils -y < "/dev/null"
```

## Go kurulumu yapıyoruz.
```
sudo apt install git build-essential curl snapd --yes
sudo snap install go --classic
echo 'export GOPATH="$HOME/go"' >> ~/.profile
echo 'export GOBIN="$GOPATH/bin"' >> ~/.profile
echo 'export PATH="$GOBIN:$PATH"' >> ~/.profile
source ~/.profile
```

## source code ile binary dosyayı derliyoruz.
```
cd $HOME
git clone https://github.com/stratosnet/sds.git
cd sds
git checkout v0.8.0
make build
cp target/ppd $HOME/bin
```
![image](https://user-images.githubusercontent.com/73015593/180841281-fc0803b8-7b24-4d6e-b435-292c4b3eb3b9.png)

## binary dosya oluşturuyoruz.
```
make install
```

## Node dosyası oluşturup yapılandırıyoruz. 
-1 Numaralı yere şifre giriyoruz.
-2 Numaralı yere cüzdan ismimizi giriyoruz.
-3 numaralı yere input bip39 Eğer eski cüzdan kullanmak istiyorsak mnemonic giriyoruz. Yeni cüzdan oluşturmak için enter basmamız yeterli.
-4 numaralı yere enter basıyoruz.
-5 numaralı yere y giriyoruz.
```
cd $HOME
mkdir rsnode
cd rsnode
ppd config -w -p
```
![image](https://user-images.githubusercontent.com/73015593/180845362-f87832db-9715-4dec-8d3f-4889428b27ce.png)

## config dosyasına giriyoruz.
```
nano $HOME/rsnode/configs/config.toml
```

## Versiyon kısmı aşağıdaki gibi değilse düzenliyoruz.
```
[version]
  app_ver = 8
  min_app_ver = 8
  show = 'v0.8.0'
```
![image](https://user-images.githubusercontent.com/73015593/180858948-069ae1e0-1772-4499-bf15-87d027ebb515.png)

## stratos_chain_url kısmını aşağıdaki gibi değilse düzenliyoruz.
```
stratos_chain_url = 'https://rest-tropos.thestratos.org:443' 
```
![image](https://user-images.githubusercontent.com/73015593/180859039-fd0e7d3e-72d8-44bf-ac9f-8ae7c516e27e.png)

## [sp-list] yani meta node'ları aşağıdaki gibidüzenliyoruz.
```
[[sp_list]]
p2p_address = 'stsds1mr668mxu0lyfysypq88sffurm5skwjvjgxu2xt'
p2p_public_key = 'stsdspub1zcjduepq4v8yu6nzem787nfnwvzrfvpc5f7thktsqjts6xp4cy4a2j4rgm7sgdy4zy'
network_address = '35.73.160.68:8888'
[[sp_list]]
p2p_address = 'stsds1ftcvm2h9rjtzlwauxmr67hd5r4hpxqucjawpz6'
p2p_public_key = 'tsdspub1zcjduepqq9rk5zwkzfnnszt5tqg524meeqd9zts0jrjtqk2ly2swm5phlc2qtrcgys'
network_address = '46.51.251.196:8888'
[[sp_list]]
p2p_address = 'stsds12uufhp4wunhy2n8y5p07xsvy9htnp6zjr40tuw'
p2p_public_key = 'stsdspub1zcjduepqkst98p2642fv8eh8297ppx7xuzu7qjz67s9hjjhxjxs834md7e0s5rm3lf'
network_address = '18.130.202.53:8888'
[[sp_list]]
p2p_address = 'stsds1wy6xupax33qksaguga60wcmxpk6uetxt3h5e3e'
p2p_public_key = 'stsdspub1zcjduepqyyfl7ljwc68jh2kuaqmy84hawfkak4fl2sjlpf8t3dd00ed2eqeqlm65ar'
network_address = '35.74.33.155:8888'
[[sp_list]]
p2p_address = 'stsds1nds6cwl67pp7w4sa5ng5c4a5af9hsjknpcymxn'
p2p_public_key = 'stsdspub1zcjduepq6mz8w7dygzrsarhh76tnpz0hkqdq44u7usvtnt2qd9qgp8hs8wssl6ye0g'
network_address = '52.13.28.64:8888'
[[sp_list]]
p2p_address = 'stsds1403qtm2t7xscav9vd3vhu0anfh9cg2dl6zx2wg'
p2p_public_key = 'stsdspub1zcjduepqzarvtl2ulqzw3t42dcxeryvlj6yf80jjchvsr3s8ljsn7c25y3hq2fv5qv'
network_address = '3.9.152.251:8888'
[[sp_list]]
p2p_address = 'stsds1hv3qmnujlrug00frk86zxr0q23rnqcaquh62j2'
p2p_public_key = 'stsdspub1zcjduepqj69eeq07yfdgu4cdlupvga897zjqjakuru0qar5na7as4kjr7jgs0k7aln'
network_address = '18.223.175.117:8888'
```
![image](https://user-images.githubusercontent.com/73015593/180858395-b9adda1e-41a0-40b2-92ea-b75ff77150ef.png)

## chain_id kısmını tropos-4 olarak ayarlı değilse düzenliyoruz.
```
chain_id = 'tropos-4'
```
![image](https://user-images.githubusercontent.com/73015593/180858499-32f8ea8c-1ca8-43c3-945b-90843fedf75c.png)

## network_address kısmına kendi ip adresimizi aşağıdaki gibi düzenliyoruz.
```
network_address = 'your node external ip' 
```
![image](https://user-images.githubusercontent.com/73015593/180859350-2f671d71-31f5-47a1-98ae-d9d0cf93b546.png)

## Son olarak config.toml dosyası aşağıdaki gibi gözükür.
![image](https://user-images.githubusercontent.com/73015593/180859798-456e15cd-fd1b-4a66-a6a0-2dba8d6ae212.png)

## Faucetten token alıyoruz. WalletAddress kısmına cüzdan adresimizi yazıyoruz.
```
curl --header "Content-Type: application/json" --request POST --data '{"denom":"ustos","address":"WalletAddress"} ' https://faucet-tropos.thestratos.org/credit

```

## Screen kurulumu yapıyoruz.
```
apt-get install screen
```

## sds isimli bir screen oluşturuyoruz.
```
screen -S sds
```

## sds resource node başlatıyoruz. (please register at first çıktısı almamız gerekiyor.)
```
cd ~/rsnode
ppd start
```
![image](https://user-images.githubusercontent.com/73015593/180861862-5d26d766-ec76-43f1-bdfa-4a7376f7597c.png)

## ctrl+a d ile screenden çıkıyoruz.

## terminal isimli bir screen oluşturuyoruz.
```
screen -S terminal
```

## resource node ile etkileşim kurabilmek için ek terminal açıyoruz.
```
cd ~/rsnode
ppd terminal
```
![image](https://user-images.githubusercontent.com/73015593/180884393-d57cb317-7455-4efc-b420-2316079d09b7.png)


## registerpeer işlemi yapıyoruz.Aşağıdaki gibi registered as PP successfully çıktısı almamız gerekli.
```
registerpeer
```
![image](https://user-images.githubusercontent.com/73015593/180886132-985304e7-ba5b-4819-9276-c0de0803f22f.png)

## activate işlemi yapıyoruz. (activate <amount> <fee> <gas>)
```
activate 10000000000 10000 1000000
```
![image](https://user-images.githubusercontent.com/73015593/180886338-cd37ffd5-28c2-450d-8848-7d93eb2a2d46.png)

## Node durumumuza bakıyoruz.
```
status
```
![image](https://user-images.githubusercontent.com/73015593/180886576-fdd002ee-6e73-4270-a8bb-89ee9f89bcf1.png)

## Kazandığımız ödülleri kontrol etmek için (cüzdanAdresi kısmına cüzdan adresimizi yazıyoruz):
--Utros stos'un 1.000.000.000 da 1 ine eşit.
https://rest-tropos.thestratos.org/pot/rewards/wallet/cüzdanAdresi
![image](https://user-images.githubusercontent.com/73015593/180886804-860779ef-b9cb-4d16-a852-043f8c72885f.png)

# (opsiyonel) Otomatik dosya oluşturup yükleme (ödül almak için gerekli değil):

## Ozon alımı yapıyoruz. (Eğer cüzdanımızda 100 token varsa)
```
prepay 100000000000 10000 600000
```
  
## Ozon alımının başarılı olup olmadığını kontrol ediyoruz. WalletAddress kısmına cüzdan adresimizi yazıyoruz.
```
getoz walletAddress
```
![image](https://user-images.githubusercontent.com/73015593/180888582-96417f6d-b58f-49c5-90e3-93bb057b43a9.png)  
  
## ctrl+a d ile terminal screen den çıkıyoruz.  

## upload isimli bir screen oluşturuyoruz.
```
screen -S upload
```

## upload isimli bir klasör oluşturuyoruz.
```
mkdir -p ~/upload
```
  
## upload.sh script'i oluşturuyoruz.
```
nano $HOME/rsnode/upload.sh
```
  
## script komutlarımızı yapıştırıyoruz ardından ctrl x y ile kaydedip çıkıyoruz.
```
#!/bin/bash
while true;
do /usr/bin/head -c 25M /dev/urandom > "$HOME/upload/test-$(date '+%Y%m%d%H%M')" ; ppd terminal exec put "$HOME/upload/test-$(date '+%Y%m%d%H%M')";
sleep 900;
/usr/bin/rm -rf "$HOME/upload/test*";
sleep 1;
done
```
![image](https://user-images.githubusercontent.com/73015593/180889190-01fd7b22-c6c9-422d-8958-47d057115474.png)
  
## upload.sh dosyasına executuble yetkisi veriyoruz.
```
cd $HOME/rsnode
chmod +x upload.sh 
./upload.sh
```
![image](https://user-images.githubusercontent.com/73015593/180891088-2c2bd036-0f4c-4f00-becd-c3ecb0e8f67b.png)















































