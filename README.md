# OZR POS — Market Satış Noktası Sistemi

Küçük ve orta ölçekli marketler için geliştirilmiş, **internet bağlantısı gerektirmeyen** masaüstü POS yazılımı.

> A secure, offline-first Point of Sale system for small retail stores. Windows only. No internet required for daily operations.

[![Release](https://img.shields.io/github/v/release/EmirhanOzer07/OZR-Pos?label=son%20s%C3%BCr%C3%BCm\&color=blue)](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-informational?logo=windows)
![Java](https://img.shields.io/badge/Java-21-orange?logo=openjdk)
![License](https://img.shields.io/badge/lisans-Proprietary-lightgrey)

---

## Neden OZR POS?

- **İnternet gerektirmez** — Kesintisiz satış, bağlantı bağımsız çalışır
- **Ücretsiz deneyin** — 15 günlük demo, kredi kartı veya taahhüt olmadan
- **Kurulum kolaylığı** — Java yüklemenize gerek yok, ZIP'i açıp çalışır
- **Verileriniz sizde** — Tüm veriler şifreli olarak kendi bilgisayarınızda saklanır
- **Otomatik yedekleme** — Her gün otomatik yedek, tek tıkla geri yükleme
- **Otomatik güncelleme** — Yeni sürümler arka planda indirilir, elle müdahale gerekmez
- **Çoklu kullanıcı** — Admin ve kasiyer rolleriyle personel yönetimi

---

## Ekran Görüntüleri

### Giriş Ekranı
![Giriş](docs/screenshots/giris.png)

### Kasa / Satış Ekranı
![Satış](docs/screenshots/satis.png)

### Ürün Yönetimi
![Ürünler](docs/screenshots/urunler.png)

### Satış Raporları
![Rapor](docs/screenshots/rapor.png)

### Yedekleme Sistemi
![Yedek](docs/screenshots/yedek.png)

### Otomatik Güncelleme
![Güncelleme](docs/screenshots/guncelleme.png)

---

## Özellikler

- **Satış & Kasa** — Barkod okuyucu desteği, sepet yönetimi, nakit/kart ödeme, klavye kısayolları
- **Ürün Yönetimi** — Tekil ekleme veya CSV ile binlerce ürünü toplu yükleme
- **Personel Yönetimi** — Admin ve kasiyer rolleri, şifre değiştirme
- **Satış Raporları** — Günlük/dönemsel ciro, nakit-kart ayrımı
- **Otomatik Yedekleme** — Her açılışta SQL yedeği + her gece Excel ürün listesi
- **Geri Yükleme** — Son 30 yedekten tek tıkla geri dönüş
- **Otomatik Güncelleme** — Yeni sürüm tespiti ve kurulum
- **Karanlık / Aydınlık Tema** — Kullanıcı tercihine göre değiştirilebilir

---

## 15 Günlük Ücretsiz Demo

Satın almadan önce deneyin. Demo modunda tüm özellikler tam olarak çalışır.

**Demo nasıl başlatılır?**

1. Uygulamayı kurun (aşağıdaki kurulum adımları)
2. İlk açılışta **"Demo Başlat"** butonuna tıklayın
3. 15 gün boyunca tüm özellikleri kullanın
4. Satın almaya karar verirseniz giriş ekranından lisans anahtarınızı girin — tüm demo verileriniz korunur

> Demo süresi sona erdiğinde yeni kurulum gerekmez. Lisans anahtarı ile aynı kurulumdan devam edebilirsiniz.

---

## İndirme ve Kurulum

**Sistem Gereksinimi:** Windows 10/11 (64-bit) — Java kurulumu gerekmez

### Kurulum Adımları

1. [Releases](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest) sayfasından `OZRPos-vX.Y.Z.zip` dosyasını indirin
2. ZIP'e sağ tıklayın → **Tümünü Çıkar** → `C:\OZRPos` klasörüne taşıyın
3. `OZRPos.exe`'ye sağ tıklayın → **Masaüstüne kısayol oluştur**
4. Kısayoldan uygulamayı açın:
   - **Demo** ile başlamak istiyorsanız → **Demo Başlat** butonuna tıklayın
   - **Lisans kodunuz varsa** → **Davetiye Koduyla Kayıt Ol** seçeneğini kullanın
5. Market adı, kullanıcı adı ve şifrenizi belirleyin — kurulum tamamdır

### Sonraki Güncellemeler

Uygulama her açılışta yeni sürüm olup olmadığını otomatik kontrol eder. **Tekrar ZIP indirmenize gerek yoktur.**

> ⚠️ **Kurulum Yeri:** ZIP dosyasını `C:\Program Files\` içine **KURMAYIN**.
> Masaüstü veya `C:\OZRPos\` gibi bir klasöre çıkartın.
> Program Files'a kurulum otomatik güncellemeyi engeller.

> ⚠️ **Windows Güvenlik Uyarısı:** `OZRPos.exe` ilk çalıştırmada
> *"Windows bilgisayarınızı korudu"* uyarısı gösterebilir.
> **"Daha fazla bilgi"** → **"Yine de çalıştır"** adımlarını izleyin.

---

## Sık Sorulan Sorular

**Demo ücretsiz mi?**
Evet. 15 gün boyunca tüm özellikler ücretsiz ve sınırsız kullanılabilir. Kredi kartı veya kayıt gerekmez.

**Demo'dan lisansa geçince verilerim ne olur?**
Demo süresinde girdiğiniz tüm ürünler, satışlar ve ayarlar korunur. Lisans anahtarı girildikten sonra kaldığınız yerden devam edersiniz.

**İnternet bağlantısı şart mı?**
Hayır. Günlük satış işlemleri için internet gerekmez. İnternet yalnızca otomatik güncelleme ve lisans doğrulaması sırasında kullanılır.

**Verilerim nerede saklanıyor?**
Tüm veriler kendi bilgisayarınızda, şifreli veritabanında yerel olarak saklanır. Hiçbir veri dışarıya gönderilmez.

**Birden fazla kasa kullanılabilir mi?**
Hayır, uygulama tek bilgisayar için tasarlanmıştır.

**Barkod okuyucu gerekli mi?**
Hayır. Barkod manuel olarak yazılabilir. Barkod okuyucu kullanmak işlemleri hızlandırır.

**Kaç ürün eklenebilir?**
Pratikte sınır yoktur. CSV ile toplu yüklemede tek seferde 10.000+ ürün desteklenmektedir.

**Lisansım dolunca ne olur?**
Uygulama içinde önceden uyarı verir. Süre dolduğunda giriş engellenir. Yenileme için iletişime geçin.

**Bilgisayar bozulursa verilerimi kurtarabilir miyim?**
Evet. Otomatik yedekler `AppData\Local\MarketPOS\yedek\` klasöründe tutulur. Bu klasörü düzenli olarak USB'ye veya Google Drive'a kopyalamanız önerilir.

---

## Veri Güvenliği

Verileriniz AES-256 şifreli veritabanında yerel olarak saklanır. Hiçbir veri dışarıya gönderilmez.

> 🔑 **Önemli:** İlk kurulumdan sonra `AppData\Local\MarketPOS\yedek\dbkey.bak` dosyasını bir USB belleğe yedekleyin.
> Bu dosya tüm verilerinizin şifreleme anahtarıdır. Kaybolursa veriler **kalıcı olarak erişilemez** hale gelir.

---

## Yedekleme Takvimi

| Tetikleyici | Tür | Saklama |
|---|---|---|
| Her açılışta (bugün yoksa) | SQL yedeği (şifreli) | Son 30 dosya |
| Her gece 22:00 | Excel ürün listesi | Son 20 dosya |
| Yönetim paneli → Yedek Al | SQL veya Excel | Manuel |

---

## İletişim

Lisans, demo ve teknik destek için:

**E-posta:** emirhann0077@gmail.com

---

## Lisans

Copyright © 2026 Mustafa Emirhan Özer. Tüm hakları saklıdır.
Ticari kullanım için iletişime geçin: emirhann0077@gmail.com
