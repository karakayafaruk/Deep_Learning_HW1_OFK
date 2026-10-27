# MNIST Veri Seti ile MLP Tabanlı El Yazısı Rakam Tanıma

## Amaç

Bu çalışmada MNIST veri seti kullanılarak bir Multi-Layer Perceptron (MLP) modeli geliştirilmiş ve el yazısı rakam tanıma problemi çözülmüştür. Modelin performansı eğitim, doğrulama ve test veri kümeleri üzerinde değerlendirilmiş, ardından öğrencinin kendi el yazısıyla yazdığı öğrenci numarası kullanılarak gerçek dünya performansı incelenmiştir.

---

## Veri Seti

Bu projede MNIST (Modified National Institute of Standards and Technology) veri seti kullanılmıştır.

Veri setinin genel özellikleri:

- Toplam 70.000 adet gri tonlamalı görüntü
- 28 × 28 piksel görüntü boyutu
- 10 farklı sınıf (0–9)
- Toplam 70.000 el yazısı rakam görüntüsü

MNIST veri setinin orijinal dağılımı:

- Eğitim Verisi: 60.000 görüntü
- Test Verisi: 10.000 görüntü

Ödev kapsamında eğitim verisi ayrıca train ve validation kümelerine ayrılmıştır:

- Train Verisi: 48.000 görüntü
- Validation Verisi: 12.000 görüntü
- Test Verisi: 10.000 görüntü

Test veri kümesi model geliştirme sürecinde kullanılmamış ve yalnızca nihai performans değerlendirmesi için ayrılmıştır.

---

## Model Mimarisi

Geliştirilen MLP modeli aşağıdaki katmanlardan oluşmaktadır:

### Giriş Katmanı

- 784 nöron (28 × 28 = 784)

### Gizli Katman 1

- 256 nöron
- ReLU aktivasyon fonksiyonu

### Gizli Katman 2

- 128 nöron
- ReLU aktivasyon fonksiyonu

### Çıkış Katmanı

- 10 nöron (0–9 sınıfları)

Model mimarisi aşağıdaki gibidir:

```text
784 → 256 → 128 → 10
```

---

## Kullanılan Hiperparametreler

| Parametre | Değer |
|------------|--------|
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Batch Size | 64 |
| Epoch Sayısı | 20 |
| Loss Function | CrossEntropyLoss |
| Aktivasyon Fonksiyonu | ReLU |

---

## Eğitim Sonuçları

Eğitim tamamlandıktan sonra elde edilen sonuçlar aşağıda verilmiştir.

| Performans Ölçütü | Sonuç |
|-------------------|--------|
| Training Loss | 0.0057 |
| Validation Loss | 0.1212 |
| Training Accuracy | 99.79% |
| Validation Accuracy | 97.68% |
| Test Accuracy | 97.87% |
| Eğitim Süresi | 147.54 saniye |

---

## Eğitim Grafikleri

Eğitim süreci boyunca aşağıdaki grafikler oluşturulmuştur:

- Training Loss ve Validation Loss Grafiği
- Training Accuracy ve Validation Accuracy Grafiği

Grafikler proje deposundaki `results` klasöründe bulunmaktadır.

---

## Kendi El Yazısı ile Test

Model eğitildikten sonra öğrencinin kendi el yazısıyla yazdığı öğrenci numarası üzerinde test edilmiştir.

### Gerçek Öğrenci Numarası

```text
25120205084
```

### Model Tahmini

```text
25820205054
```

### Sonuç

Toplam rakam sayısı:

```text
11
```

Doğru tahmin edilen rakam sayısı:

```text
9
```

Yanlış tahmin edilen rakamlar:

- 1 rakamı, 8 olarak tahmin edilmiştir.
- 8 rakamı, 5 olarak tahmin edilmiştir.

Yaklaşık doğruluk oranı:

```text
9 / 11 ≈ %81.8
```

---

## Değerlendirme

Eğitilen MLP modeli MNIST veri seti üzerinde oldukça başarılı sonuçlar elde etmiştir. Modelin test kümesindeki doğruluk oranı %97.87 olarak ölçülmüştür. Training Accuracy ve Validation Accuracy değerleri incelendiğinde modelin veri setini başarılı şekilde öğrendiği görülmektedir.

Gerçek el yazısı görüntüleri üzerinde yapılan testlerde model 11 rakamın 9 tanesini doğru tahmin etmiştir. Buna rağmen bazı rakamlar yanlış sınıflandırılmıştır. Bu durum, eğitim sırasında kullanılan MNIST görüntüleri ile gerçek dünyadan elde edilen el yazısı görüntüleri arasındaki farklılıklardan kaynaklanmaktadır.

Özellikle yazı stili, rakam kalınlığı, konumlandırma ve görüntü kalitesi gibi etkenler model performansını etkileyebilmektedir. Bu durum derin öğrenme literatüründe "distribution shift" veya "generalization" problemi olarak bilinmektedir.

Sonuç olarak geliştirilen MLP modeli hem MNIST veri seti üzerinde hem de kendi oluşturduğum el yazısı verileri üzerinde başarılı sonuçlar üretmiş ancak kusursuz olarak da çalışmamıştır.