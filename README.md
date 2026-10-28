# sesten-notaya

Kayıttan Türk müziği notası (AEU, MusicXML) çıkaran modelin Colab defterleri.

Defterlerde kod ya da veri yok. Defterler kodu ve veriyi Google Drive'daki `ses_nota/` klasöründen alır. Çalışma
zamanı olarak A100 seçilmelidir.

| defter | ne yapar | Colab |
|---|---|---|
| `colab/tur5.ipynb` | 5. tur: 4. turun ağırlıklarından başlar, iki kat büyüyen gerçek kayıt verisiyle 20.000 adım eğitir. Model iki türlü nota yazmayı öğrenir: kitaptaki gibi sade nota ve çalındığı gibi süslemeli nota. Sonunda 4. ve 5. tur aynı sınavlarda yan yana ölçülür, süslemeli notalar ayrıca yazılır | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur5.ipynb) |
| `colab/tur4.ipynb` | 4. tur: 3. turun ağırlıklarından başlar, büyüyen gerçek kayıt verisiyle 15.000 adım eğitir. Sonunda 3. ve 4. tur aynı sınavlarda yan yana ölçülür | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur4.ipynb) |
| `colab/tur3.ipynb` | 3. tur: süslemeli tek saz ve düet sentetik sesle gerçek kayıtları karıştırarak 15.000 adım eğitir | [aç](https://colab.research.google.com/github/mtalhabalci/sesten-notaya/blob/main/colab/tur3.ipynb) |

Her defterin başında ayarlar var:

- `AD`: koşunun adı. Koşu `runs/ic/<tarih>-<AD>/` klasörüne yazılır.
- `ADIM`: eğitimin kaç adım süreceği.
- `DEVAM = 'son'`: oturum düşerse son kayıt noktasından devam eder.
- `KAPAT = True`: iş bitince makineyi kapatır, boşta kota harcanmaz.
