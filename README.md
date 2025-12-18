# CNN_siniflandirma
# Görüntü Sınıflandırma: VGG16 ve Özel CNN Modellerinin Karşılaştırılması

Bu proje, bir görüntü sınıflandırma görevinde üç farklı derin öğrenme yaklaşımının performansını analiz eder: Önceden eğitilmiş bir modelin transfer öğrenme ile kullanılması, temel bir CNN mimarisi ve parametreleri optimize edilmiş derin bir CNN mimarisi.

## 📊 Veri Seti Bilgileri

* **İçerik:** 2 sınıftan oluşan (Binary/Categorical) görüntü veriseti.
* **Eğitim Seti:** 128 görüntü.
* **Doğrulama/Test Seti:** 32 görüntü (Verinin %20'si).
* **Giriş Boyutu:** 128x128 piksel.

## 🛠️ Kurulum ve Gereksinimler

Projenin çalıştırılması için aşağıdaki kütüphanelerin yüklü olması gerekir:

* **TensorFlow / Keras:** Model inşası ve eğitimi.
* **Matplotlib:** Sonuçların görselleştirilmesi.
* **NumPy:** Matris işlemleri.
* **OS:** Dosya dizin yönetimi.
## 🏗️ Model Mimarileri

### 1. Model 1: VGG16 (Transfer Learning)
* **Mimari:** ImageNet ağırlıklarıyla dondurulmuş (frozen) VGG16 tabanlıdır.
* **Üst Katmanlar:** Flatten, 256 nöronlu Dense ve Softmax çıkış katmanı eklenmiştir.
* **Strateji:** Önceden eğitilmiş özellik çıkarıcıları kullanarak hızlı ve yüksek başarı hedeflemiştir.

### 2. Model 2: Basit CNN (Scratch)
* **Mimari:** 3 adet Evrişimli (Conv2D) ve Maksimum Havuzlama (MaxPooling) bloğundan oluşur.
* **Düzenlileştirme:** Ezberlemeyi önlemek için %50 Dropout kullanılmıştır.
* **Kayıp Fonksiyonu:** `binary_crossentropy`.

### 3. Model 3: İyileştirilmiş Derin CNN
Model 2'den Model 3'e geçişte performansı artırmak için yapılan yapısal değişiklikler:
* **Katman Derinliği:** Filtre sayısı 256'ya kadar artırılan 4. bir blok eklenmiştir.
* **Batch Normalization:** Her blok sonuna eklenerek eğitimin kararlılığı artırılmıştır.
* **Veri Artırma (Augmentation):** Rotation, width/height shift, zoom ve horizontal flip özellikleri eklenmiştir.
* **Parametre Güncellemesi:** Batch size 8'e düşürülmüş ve Learning Rate 0.0001 (Adam) olarak ayarlanmıştır.

## 📈 Performans Karşılaştırması

| Özellik | Model 1 (VGG16) | Model 2 (Basit CNN) | Model 3 (İyileştirilmiş CNN) |
| :--- | :--- | :--- | :--- |
| **Yaklaşım** | Transfer Learning | Sıfırdan CNN | Optimize Edilmiş CNN |
| **Test Doğruluğu** | **%96.88** | **%59.38** | **%88.50+** (Gelişim Aşamasında) |
| **Test Kaybı (Loss)** | 0.0570 | 1.4257 | 0.4936 (4. Epoch) |
| **Eğitilebilir Parametre** | 2,097,922 | 3,304,769 | 2,642,818 |

### Performansa Etki Analizi
* **Model 1:** Hazır ağırlıklar sayesinde 7. epoch itibariyle %100 eğitim doğruluğuna ulaşmıştır.
* **Model 2'den 3'e Geçiş:** Veri artırma (Augmentation) ve Batch Normalization sayesinde modelin "aşırı öğrenme" (overfitting) sorunu azaltılmış, daha kararlı bir kayıp (loss) düşüşü gözlemlenmiştir.

## 🚀 Çalıştırma Adımları

1. Veri setinizi Google Drive'a `makine_ogrenmesi_odev_1` klasörü altına yükleyin.
2. `ImageDataGenerator` ile verileri normalize edin (1/255).
3. İlgili model bloğunu çalıştırarak eğitimi başlatın.
4. `plt.plot` komutları ile eğitim/doğrulama grafiklerini inceleyin.
```bash
