# MNIST Veri Seti ile MLP Tabanlı El Yazısı Rakam Tanıma

Bu projede MNIST veri seti kullanılarak Multi-Layer Perceptron (MLP) tabanlı bir el yazısı rakam tanıma sistemi geliştirilmiştir. Model PyTorch kullanılarak sıfırdan eğitilmiş ve performansı hem MNIST test verileri hem de gerçek el yazısı görüntüleri üzerinde değerlendirilmiştir.

---

## Proje Amacı

Bu çalışmanın amacı:

- MNIST veri setini kullanmayı öğrenmek
- MLP mimarisini uygulamak
- Train / Validation / Test ayrımını anlamak
- Loss ve Accuracy kavramlarını yorumlamak
- Model performansını değerlendirmek
- Gerçek dünya verileri üzerinde model başarısını incelemek

---

## Kullanılan Teknolojiler

- Python
- PyTorch
- NumPy
- Matplotlib
- OpenCV
- Google Colab

---

## Veri Seti

Bu projede MNIST el yazısı rakam veri seti kullanılmıştır.

### Orijinal Veri Seti

- 60.000 eğitim görüntüsü
- 10.000 test görüntüsü
- Toplam 70.000 görüntü
- 28 × 28 piksel
- Gri tonlamalı görüntüler
- 10 sınıf (0–9)

### Kullanılan Veri Ayrımı

| Veri Kümesi | Görüntü Sayısı |
|------------|------------|
| Train | 48.000 |
| Validation | 12.000 |
| Test | 10.000 |

---

## Model Mimarisi

Model yapısı aşağıdaki gibidir:

```text
Input (784)
      ↓
Hidden Layer (256) + ReLU
      ↓
Hidden Layer (128) + ReLU
      ↓
Output Layer (10)
```

MNIST görüntüleri modele verilmeden önce 28×28 boyutundan 784 boyutlu vektöre dönüştürülmüştür.

---

## Kullanılan Hiperparametreler

| Parametre | Değer |
|------------|--------|
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Batch Size | 64 |
| Epoch | 20 |
| Loss Function | CrossEntropyLoss |
| Aktivasyon Fonksiyonu | ReLU |

---

## Sonuçlar

| Ölçüt | Sonuç |
|--------|--------|
| Training Loss | 0.0057 |
| Validation Loss | 0.1212 |
| Training Accuracy | 99.79% |
| Validation Accuracy | 97.68% |
| Test Accuracy | 97.87% |
| Eğitim Süresi | 147.54 saniye |

---

## Kendi El Yazısı ile Test

Model, öğrencinin kendi el yazısıyla yazdığı öğrenci numarası üzerinde test edilmiştir.

### Gerçek Öğrenci Numarası

```text
25120205084
```

### Model Tahmini

```text
25820205054
```

### Sonuç

- Doğru Tahmin Edilen Rakam Sayısı: 9 / 11
- Yaklaşık Doğruluk: %81.8

Bu sonuç, modelin MNIST veri setinde yüksek doğruluk elde etmesine rağmen gerçek dünyadaki farklı el yazısı stillerinde performans kaybı yaşayabildiğini göstermektedir.

---

## Proje Dosya Yapısı

```text
Deep_Learning_HW1_OFK/
│
├── notebook.ipynb
├── README.md
├── report.md
│
├── model/
│   └── mlp_model.pth
│
├── results/
│   ├── loss_graph.png
│   └── accuracy_graph.png
│
└── student_id_image/
    └── numara.jpg
```

---

## Çalıştırma

Projeyi çalıştırmak için:

1. Notebook'u Google Colab üzerinde açın.
2. Tüm hücreleri sırasıyla çalıştırın.
3. Model eğitildikten sonra kendi el yazısı görüntünüzü yükleyin.
4. Tahmin sonuçlarını inceleyin.

---

## Proje Sahibi

Ömer Faruk Karakaya

Bilgisayar Mühendisliği
