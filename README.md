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

```bash
