# Glow Normalizing Flow Model for Image Generation

Bu proje, GLOW tabanlı bir Normalizing Flow modeli kullanarak çeşitli veri setlerinde (MNIST, CIFAR-10, CelebA) görüntü üretimi yapar. Projede, veri ön işleme, eğitim ve değerlendirme süreçleri yer almakta ve Python ile PyTorch kullanılarak geliştirilmiştir.

## Proje Yapısı

Proje, aşağıdaki dosya ve klasör yapısını içerir:

- **`actnorm.py`**: ActNorm katmanı için tanımlar ve işlevler içerir.
- **`coupling.py`**: Coupling katmanları için gerekli fonksiyonlar ve sınıflar.
- **`flow.py`**: Flow modüllerini tanımlar ve modelin temel işlevlerini içerir.
- **`glow.py`**: GLOW modelini tanımlar ve oluşturur.
- **`invertible_conv.py`**: Tersinir konvolüsyon katmanlarını tanımlar.
- **`main.py`**: Ana eğitim ve model değerlendirme işlemlerinin yürütüldüğü dosya.
- **`net.py`**: Modelin ağ yapısını tanımlar.
- **`requirements.txt`**: Projenin bağımlılıklarını listeler.
- **`split.py`**: Split işlemleri için gerekli tanımlar.
- **`squeeze.py`**: Sıkıştırma işlemleri için kullanılan fonksiyonlar ve sınıflar.
- **`test.py`**: Eğitilen modeli kullanarak veri üretimi için kodlar.

## Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki kütüphanelerin yüklü olduğundan emin olun:

- Python 3.8+
- PyTorch
- torchvision
- numpy
- argparse

Gereksinimlerin tamamını kurmak için:

```bash
pip install -r requirements.txt
```
# Model Eğitimi ve Değerlendirme Kılavuzu

Bu rehber, modelinizi eğitmek ve değerlendirmek için izleyebileceğiniz adımları içerir.

## Adım 1: Komut Satırı Argümanlarını Ayarlayın

Modeli çalıştırmadan önce veri seti, epoch sayısı ve resim boyutunu belirlemek için komut satırı argümanlarını kullanabilirsiniz. Aşağıdaki komut, MNIST veri seti kullanarak 10 epoch ve 32x32 boyutunda resimler ile eğitimi başlatır:

```bash
python main.py --dataset mnist --epochs 10 --size 32
```
## Adım 2: DataLoader Ayarları

`get_dataloader()` fonksiyonu, belirtilen veri seti için uygun veri yükleyiciyi oluşturur. Desteklenen veri setleri şunlardır:

- MNIST
- CIFAR-10
- CelebA

Örneğin, MNIST veri seti için bir veri yükleyici oluşturmak üzere aşağıdaki kodu kullanabilirsiniz:

```python
dataloader = get_dataloader('mnist', batch_size=64, size=32)
```

## Adım 3: Model Eğitimi ve Değerlendirme

Modeli eğitmek için aşağıdaki komutu kullanabilirsiniz:

```bash
python main.py --dataset mnist --epochs 10
```
Eğitim tamamlandıktan sonra, kaydedilen model ile veri üretmek için test.py dosyasını kullanabilirsiniz:
```bash
python test.py --model_path ./checkpoints/mnist_model.pth
```
Bu bölüm, kullanıcılara model eğitimi ve değerlendirme sürecini nasıl gerçekleştireceklerini açıkça gösterir.
