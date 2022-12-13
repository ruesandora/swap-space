<h1 align="center"> Swap Space </h1>

<h1 align="center"> Bu rehberde sunucumuzu daha verimli kullanmak için swap space yapacağız. </h1>

 ## Nedir bu swap space?

* Öncelikle swap space ve benzeri konular için toplu ve büyük bir repo hazırladım ancak buna ihtiyaç olduğu için ayrı paylaşıyorum şimdilik.
* Swap space, sunucularınızdaki RAM için bir yedek alan açmamız için yapılan bir işlem. Swap space, fiziksel RAM'in yetersiz olduğu durumlarda sistemin ihtiyaç duyduğu ek bellek alanını sağlamak için kullanacağız. RAM arttırırken diskten yiyoruz, ve burada kullanılan RAM fiziksel RAM kadar hızlı ve sağlıklı değil.
* Sağlıklı değil? Yani.. benim 1TB diskim var, 100 GB RAM yapayım o zaman (yapabilirisniz) demek pek mantıklı değil, ihtiyaç kadarını kullanacağız.
* Bu sayede sistem daha fazla veriyi aynı anda işleyebilir ve daha hızlı çalışabilir. Swap alanının boyutu genellikle sistem belleğinin RAM boyutuna göre ayarlanır ve genellikle birkaç gigabayt civarında.

## Nasıl yapılır?

* Ben örnekte 1 GB'lık RAM açacağım size (1024 MB), siz ihtiyacınız kadarınızı belirleyin.
* Ziesha'da killed olanlar için 1 GB yeter yüksek ihtimal (test etmedim)
* 1024 MB boyutunda bir swap dosyası oluşturmak için:
```
sudo swapoff -a
```
```
sudo fallocate -l 1024M /swapfile
```

## Oluşturduğunuz swap dosyasının izinlerini ayarlamak için:
```
sudo chmod 600 /swapfile
```
## Oluşturduğunuz swap dosyasını sisteme eklemek için:
```
sudo mkswap /swapfile
```
## Oluşturduğunuz swap dosyasını aktif hale getirmek için:
```
sudo swapon /swapfile
```
## Bu 3 komutlada kontrol edebilirsiniz:
```
sudo swapon -s
```
```
free -m
```
```
htop
```

![image](https://user-images.githubusercontent.com/101149671/207309748-5b1a4a41-28b9-4faa-b60a-d76c648ee286.png)
![image](https://user-images.githubusercontent.com/101149671/207309767-f181fc65-314c-475c-ac49-daa045d8c35a.png)

## Silmek için:
```
sudo swapoff -a
```
