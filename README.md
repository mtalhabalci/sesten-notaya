# sesten-notaya

Kayıttan Türk müziği notası (AEU, MusicXML) çıkaran modelin Colab defterleri.

Defterlerde kod ya da veri yok. Defterler kodu ve veriyi Google Drive'daki `ses_nota/` klasöründen alır. Çalışma
zamanı olarak A100 seçilmelidir.

| defter | ne yapar | Colab |
|---|---|---|
| `colab/vokoder_v1.ipynb` | Saz vokoderi v1: mel spektrumu ve perde eğrisinden (f0) 44,1 kHz ses üreten hızlı model (NSF-HiFiGAN, 3,7 M parametre) eğitir. Perdeyi verilen f0'dan alır, tınıyı mel'den; sekiz sazın solo kayıtlarıyla 150.000 adım (A100'de 8-9 saat), sonunda perde sadakati ve parçalı üretimde dikiş ölçülür | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/vokoder_v1.ipynb) |
| `colab/icra_v2.ipynb` | Nota → icra modeli v2: v1'e icranın genel dinamiğini koşul olarak ekler, nota içi sönümü toplam düşüş olarak öğrenir; 2000 adım, 250 adımda bir doğrulama, en iyi noktadan E dosyalarını yazar | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/icra_v2.ipynb) |
| `colab/icra_v1.ipynb` | Nota → icra modeli v1: yazılı notadan icrayı (zamanlama, vuruş gücü, perde sapması, titreşim, glissando, süsleme) öğrenen modeli eğitir, değerlendirir ve ölçüt pasajları için modelin çaldığı E dosyalarını yazar | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/icra_v1.ipynb) |
| `colab/tur8.ipynb` | 8. tur: 7. turun ağırlıklarından başlar, 7. turun tarifiyle 20.000 adım eğitir. Gerçek kayıtlar büyüdü (şarkı söylenen kayıtların sesi ayrılmış saz kısmı, şarkıcı ile tek saz kayıtları); sentetiğe solo klarnet ve süslemeli kanun eklendi. Her sınav ham ve temizlenmiş olarak, dürüst sınav ayrıca güvenilir kayıtlarla puanlanır. Sonunda 7. ve 8. tur aynı sınavlarda yan yana ölçülür | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur8.ipynb) |
| `colab/tur7.ipynb` | 7. tur: 6. turun ağırlıklarından başlar, 6. turun tarifiyle eğitir. Gerçek kayıtlara sazla çalınan şarkı, türkü ve ilahiler eklendi. Sonunda 6. ve 7. tur aynı sınavlarda yan yana ölçülür | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur7.ipynb) |
| `colab/klarnet_ddsp.ipynb` | Klarnet ses modeli (DDSP) pilotu: tını modeli eğitir, eğitimde görülmemiş klipleri modelle yeniden çalar, gerçek ile model için A/B kör dinleme klasörü yazar | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/klarnet_ddsp.ipynb) |
| `colab/tur6.ipynb` | 6. tur: 5. turun ağırlıklarından başlar, 5. turun tarifiyle 20.000 adım eğitir. Değişen yalnız veri: gerçek kayıtlar iki katından fazla büyüdü, ney, ud ve tanbur kayıtları da eklendi. Sonunda 5. ve 6. tur aynı sınavlarda yan yana ölçülür | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur6.ipynb) |
| `colab/tur5.ipynb` | 5. tur: 4. turun ağırlıklarından başlar, iki kat büyüyen gerçek kayıt verisiyle 20.000 adım eğitir. Model iki türlü nota yazmayı öğrenir: kitaptaki gibi sade nota ve çalındığı gibi süslemeli nota. Sonunda 4. ve 5. tur aynı sınavlarda yan yana ölçülür, süslemeli notalar ayrıca yazılır | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur5.ipynb) |
| `colab/tur4.ipynb` | 4. tur: 3. turun ağırlıklarından başlar, büyüyen gerçek kayıt verisiyle 15.000 adım eğitir. Sonunda 3. ve 4. tur aynı sınavlarda yan yana ölçülür | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur4.ipynb) |
| `colab/tur3.ipynb` | 3. tur: süslemeli tek saz ve düet sentetik sesle gerçek kayıtları karıştırarak 15.000 adım eğitir | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur3.ipynb) |

Her defterin başında ayarlar var:

- `AD`: koşunun adı. Koşu `runs/ic/<tarih>-<AD>/` klasörüne yazılır.
- `ADIM`: eğitimin kaç adım süreceği.
- `DEVAM = 'son'`: oturum düşerse son kayıt noktasından devam eder.
- `KAPAT = True`: iş bitince makineyi kapatır, boşta kota harcanmaz.
