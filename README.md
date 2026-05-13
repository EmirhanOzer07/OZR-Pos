<div align="center">

# OZR POS

**Profesyonel Market Kasa Sistemi · Professional Point of Sale System**

[![Son Surum](https://img.shields.io/github/v/release/EmirhanOzer07/OZR-Pos?label=son%20surum&color=0066cc&style=for-the-badge)](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest)
[![Platform](https://img.shields.io/badge/Windows%2010%2F11-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest)
[![Java](https://img.shields.io/badge/Java%2021-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest)
[![Guvenlik](https://img.shields.io/badge/AES--256%20+%20JWT-dc2626?style=for-the-badge&logo=letsencrypt&logoColor=white)](#veri-guvenligi--data-security)
[![Lisans](https://img.shields.io/badge/Lisans-Proprietary-6b7280?style=for-the-badge)](LICENSE)

[**İndir / Download**](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest) &nbsp;·&nbsp; [**Lisans Al / Get License**](#lisans-ve-iletisim--license--contact) &nbsp;·&nbsp; [**İletişim / Contact**](#lisans-ve-iletisim--license--contact)

</div>

---

> **TR** — Küçük ve orta ölçekli marketler için geliştirilmiş, güvenli, internet bağlantısı gerektirmeyen masaüstü kasa yazılımı. Tüm verileriniz şifrelenerek yalnızca kendi bilgisayarınızda saklanır.

> **EN** — A secure, offline-first desktop Point of Sale system for small and medium retail stores. No internet required for daily operations. Your data never leaves your computer.

---

## 📸 Ekran Görüntüleri / Screenshots

### Kasa / Satış Ekranı
![Satış](docs/screenshots/satis.png)

<details>
<summary>Diğer ekranlar / More screenshots</summary>

### Giriş Ekranı
![Giriş](docs/screenshots/giris.png)

### Ürün Yönetimi
![Ürünler](docs/screenshots/urunler.png)

### Satış Raporları
![Rapor](docs/screenshots/rapor.png)

### Yedekleme
![Yedek](docs/screenshots/yedek.png)

### Otomatik Güncelleme
![Güncelleme](docs/screenshots/guncelleme.png)

</details>

---

## ✨ Özellikler / Features

| | TR | EN |
|---|---|---|
| 🛒 Kasa | Barkod okuyucu, sepet yönetimi, nakit/kart ödeme, klavye kısayolları | Barcode scanner, cart, cash/card payment, keyboard shortcuts |
| 📦 Ürünler | Tekil ekleme veya CSV ile 10.000+ ürün yükleme | Single add or bulk CSV upload (10,000+ products) |
| 👥 Personel | ADMIN ve KASİYER rolleri, şifre değiştirme | ADMIN and CASHIER roles, password management |
| 📊 Raporlar | Günlük/dönemsel ciro, nakit-kart ayrımı | Daily/periodic revenue, cash-card breakdown |
| 💾 Yedekleme | Her açılışta otomatik SQL yedeği + gece Excel listesi | Auto SQL backup on launch + nightly Excel export |
| ♻️ Geri Yükleme | Son 30 yedekten tek tıkla geri dönüş | One-click restore from last 30 backups |
| 🔄 Güncelleme | Yeni sürümler arka planda indirilir, elle müdahale gerekmez | Updates download silently in the background |
| 🌙 Tema | Karanlık / Aydınlık tema | Dark / Light theme |
| 🔒 Güvenlik | AES-256 şifreleme, JWT kimlik doğrulama | AES-256 encryption, JWT authentication |

---

## 🎯 15 Günlük Ücretsiz Demo / 15-Day Free Trial

**TR:** İlk açılışta **"Demo Başlat"** butonuna tıklayın. 15 gün boyunca tüm özellikler tam olarak çalışır. Demo süresi dolduğunda lisans anahtarı ile aynı kurulumdan devam edin — verileriniz korunur.

**EN:** Click **"Start Demo"** on first launch. All features work fully for 15 days. After the trial, enter your license key to continue from where you left off — your data is preserved.

---

## 🚀 Kurulum / Installation

**Gereksinimler / Requirements:** Windows 10/11 (64-bit) — Java kurulumu gerekmez / No Java required

### TR — Kurulum Adımları

1. [**Releases**](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest) sayfasından `OZRPos-vX.Y.Z.zip` indirin
2. ZIP'e sağ tıklayın → **Tümünü Çıkar** → `C:\OZRPos` klasörüne taşıyın
3. `OZRPos.exe`'ye sağ tıklayın → **Masaüstüne kısayol oluştur**
4. Uygulamayı açın → **Demo** ile başlayın veya davetiye kodunuzu girin
5. Market adı, kullanıcı adı ve şifrenizi belirleyin — kurulum tamamdır

### EN — Installation Steps

1. Download `OZRPos-vX.Y.Z.zip` from the [**Releases**](https://github.com/EmirhanOzer07/OZR-Pos/releases/latest) page
2. Right-click ZIP → **Extract All** → move to `C:\OZRPos`
3. Right-click `OZRPos.exe` → **Send to → Desktop (create shortcut)**
4. Launch → start with **Demo** or enter your invitation code
5. Set store name, username, and password — done

> **⚠️ TR:** ZIP'i `C:\Program Files\` içine **KURMAYIN** — otomatik güncellemeyi engeller. `C:\OZRPos\` veya masaüstü kullanın.

> **⚠️ EN:** Do **NOT** install under `C:\Program Files\` — it blocks auto-updates. Use `C:\OZRPos\` or Desktop.

> **Windows SmartScreen:** "Daha fazla bilgi" → "Yine de çalıştır" / "More info" → "Run anyway"

---

## 🔑 Lisans ve İletişim / License & Contact

### TR — Nasıl Lisans Alınır?

1. Uygulamayı kurun ve açın
2. Kayıt ekranındaki benzersiz **Davetiye Kodu**'nu kopyalayın
3. Kodu e-posta ile gönderin → Marketinize özel lisans kodu iletilir
4. Kodu uygulamaya girin — marketiniz aktive edilir

> Davetiye kodu makineye özgüdür. Lisanslar market başına satılmaktadır.

### EN — How to Get a License

1. Install and open the application
2. Copy the unique **Invitation Code** shown on the registration screen
3. Send the code by email → A license code for your store will be sent back
4. Enter the code in the app — your store is activated

> The invitation code is machine-specific. Licenses are sold per store.

| | |
|---|---|
| **Email / E-posta** | emirhann0077@gmail.com |
| **Yanıt Süresi / Response** | 24 saat içinde / Within 24 hours |

---

## ❓ Sık Sorulan Sorular / FAQ

<details>
<summary><strong>İnternet bağlantısı şart mı? / Is internet required?</strong></summary>

**TR:** Hayır. Günlük satış işlemleri için internet gerekmez. Yalnızca güncelleme ve lisans doğrulaması sırasında kullanılır.

**EN:** No. Daily operations work offline. Internet is only used for updates and license validation.
</details>

<details>
<summary><strong>Verilerim nerede saklanıyor? / Where is my data stored?</strong></summary>

**TR:** Tüm veriler AES-256 şifreli olarak kendi bilgisayarınızda saklanır. Hiçbir veri dışarıya gönderilmez.

**EN:** All data is stored locally on your computer with AES-256 encryption. Nothing is sent to external servers.
</details>

<details>
<summary><strong>Birden fazla kasa kullanılabilir mi? / Multiple registers?</strong></summary>

**TR/EN:** Hayır / No. Uygulama tek bilgisayar için tasarlanmıştır / Designed for a single workstation per store.
</details>

<details>
<summary><strong>Kaç ürün eklenebilir? / How many products?</strong></summary>

**TR/EN:** Pratik sınır yoktur. CSV ile tek seferde 10.000+ ürün desteklenir / No practical limit. CSV supports 10,000+ products at once.
</details>

<details>
<summary><strong>Bilgisayar bozulursa verilerimi kurtarabilir miyim? / What if my computer breaks?</strong></summary>

**TR:** Otomatik yedekler `AppData\Local\MarketPOS\yedek\` klasöründe. Düzenli olarak USB'ye kopyalayın. `dbkey.bak` dosyasını mutlaka yedekleyin — kaybolursa veriler kurtarılamaz.

**EN:** Automatic backups are in `AppData\Local\MarketPOS\yedek\`. Copy to USB regularly. Always back up `dbkey.bak` — if lost, data cannot be recovered.
</details>

---

## 🔒 Veri Güvenliği / Data Security

| Katman / Layer | Uygulama / Implementation |
|---|---|
| Veritabanı / Database | AES-256 şifreleme, kuruluma özel anahtar / AES-256 encryption, per-install key |
| Kimlik Doğrulama / Auth | JWT (HMAC-SHA256) + BCrypt |
| Hız Sınırı / Rate Limit | IP başına 10 istek/dk / 10 req/min per IP |
| Yetkilendirme / Authorization | Spring Security 6 + role-based access |

> **TR:** Tüm şifreleme anahtarları kurulum sırasında üretilir ve yalnızca sizin makinenizde saklanır. OZR POS, işletme verilerinizi hiçbir sunucuya iletmez.

> **EN:** All encryption keys are generated at install time and stored only on your machine. OZR POS never transmits your business data to any server.

---

## 📄 Lisans / License

Copyright © 2026 Mustafa Emirhan Özer. Tüm hakları saklıdır / All rights reserved.

Bu yazılım tescilli mülkiyettir. İzinsiz kopyalama, dağıtım veya tersine mühendislik yasaktır.
This software is proprietary. Unauthorized copying, distribution, or reverse engineering is prohibited.

Tam koşullar için / For full terms: [LICENSE](LICENSE)

---

<div align="center">

Spring Boot 3.3 + JavaFX 21 · Windows 10/11

**© 2026 Mustafa Emirhan Özer**

</div>
