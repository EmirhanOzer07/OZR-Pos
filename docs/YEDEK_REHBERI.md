# Yedek ve Veri Kurtarma Rehberi
# Backup & Data Recovery Guide

---

## TR — Türkçe

### Neden Yedek Kritiktir?

OZR POS, tüm verilerinizi (ürünler, satışlar, personel) şifreli olarak **kendi bilgisayarınızda** saklar. Hiçbir veri buluta gönderilmez. Bu güvenliği artırır, ancak bilgisayar arızasında yedeğiniz yoksa verileri kurtarmak mümkün olmaz.

---

### Otomatik Yedekleme — Uygulama Ne Yapıyor?

Uygulama otomatik olarak şunları yapar:

| Zaman | İçerik |
|-------|--------|
| Her açılışta | O gün için yedek yoksa tam veritabanı yedeği alınır |
| Her gece 02:00 | Tam veritabanı yedeği |
| Her gece 22:00 | Tüm ürünlerin Excel listesi |
| Ürün eklendiğinde | Anlık yedek |
| Ürün güncellendiğinde | Anlık yedek |
| Ürün silindiğinde | Anlık yedek |

Yedekler burada saklanır:
```
C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\yedek\
```

> `AppData` klasörü gizlidir. Görmek için: Dosya Gezgini → Görünüm → Gizli öğeleri göster.

---

### Google Drive ile Otomatik Yedek (Önerilen)

**Neden Google Drive?** Bilgisayar tamamen bozulsa bile verileriniz bulutta güvende olur.

**Kurulum:**

1. [Google Drive for Desktop](https://www.google.com/drive/download/) indirin ve kurun
2. Google hesabınızla giriş yapın
3. Sağ alttaki Drive simgesine tıklayın → Ayarlar → **"Bilgisayardan yedekle"** seçin
4. `C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\yedek\` klasörünü ekleyin
5. **Bitti.** Yedekler artık her gün otomatik olarak Drive'a yüklenir.

**Ne kadar yer kaplar?** Uygulama maksimum 500 MB ile sınırlar, eski yedekler otomatik temizlenir.

---

### Ayrıca Saklamanız Gerekenler

Google Drive yedeğine ek olarak şunları **kağıda veya telefonda** not edin:

- **Lisans aktivasyon kodunuz** (size e-posta ile iletildi)
- **Patron hesabı kullanıcı adı ve şifresi**

Bu bilgiler bilgisayar değiştirmeniz gerektiğinde veya hesabınıza erişemediğinizde hayat kurtarır.

---

### Veri Kurtarma Senaryoları

#### Senaryo A: Uygulama bozuldu, aynı bilgisayar

Bu en basit durumdur. Windows'ta uygulama kaldırıldığında veriler silinmez.

1. Eski uygulamayı kaldırın (Ayarlar → Uygulamalar)
2. Yeni sürümü kurun
3. Eski kullanıcı adı ve şifrenizle giriş yapın
4. Verileriniz yerli yerinde olacak

Google Drive'a gerek yoktur.

---

#### Senaryo B: Disk formatlandı veya Windows yeniden kuruldu

1. Google Drive'dan `yedek` klasörünü bilgisayara indirin
2. Şu klasörü oluşturun (yoksa):
   `C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\`
3. Drive'dan indirilen klasördeki şu dosyaları bu klasöre kopyalayın:
   - `dbkey.bak` → `.dbkey` olarak kaydedin *(nokta ile başlıyor)*
   - `config.bak` → `config.properties` olarak kaydedin
   - `market-key.bak` → `market-key.dat` olarak kaydedin
4. Uygulamayı kurun ve çalıştırın
5. Patron hesabınızla giriş yapın
6. `yedek\gunluk\` klasöründeki ZIP dosyalarını da kopyalamayı unutmayın
7. **Yönetim ekranı → Yedekler sekmesi** → En son yedeği seçin → Geri Yükle
8. Uygulama yeniden başlar, tüm verileriniz geri gelir

> **Kritik:** `.dbkey` dosyası olmadan SQL yedekler açılamaz. Bu dosya kaybolursa veri kurtarma mümkün değildir. Drive yedeği bu yüzden şarttır.

---

#### Senaryo C: Yeni bilgisayar aldınız

Lisansınız mevcut bilgisayara özeldir. Yeni bilgisayarda **önce bizimle iletişime geçin.**

1. **emirhann0077@gmail.com** adresine yazın, lisans aktarımı talep edin
2. 1 iş günü içinde yeni bilgisayarınız için aktivasyon bilgisi iletilir
3. Ardından Senaryo B'deki adımları izleyin

Lisans aktarımı **ücretsizdir** ve yalnızca bir seferlik bildirim gerektirir.

---

#### Senaryo D: Yanlışlıkla ürünler silindi veya veri bozuldu

Uygulama çalışıyor ve giriş yapabiliyorsunuz.

1. **Yönetim ekranı → Yedekler sekmesi**
2. Geri dönmek istediğiniz tarihe ait yedeği seçin
3. **Geri Yükle** butonuna tıklayın
4. Onay ekranlarını geçin — uygulama otomatik kapanıp açılır
5. Seçtiğiniz tarihteki verilerle devam eder

> Yedekler listesi ekranda görünmüyorsa önce `yedek\gunluk\` klasörünün dolu olduğunu kontrol edin.

---

### Yedek Sağlık Kontrolü

Ayda bir şu kontrolleri yapmanızı öneririz:

- [ ] Google Drive'da `yedek` klasörü günceli mi? (En az 1 haftalık yedek görünmeli)
- [ ] `yedek\gunluk\` klasöründe son 30 güne ait ZIP dosyaları var mı?
- [ ] `yedek\dbkey.bak` dosyası mevcut mu?
- [ ] Patron şifrenizi hatırlıyor musunuz?

---

## EN — English

### Why Backups Matter

OZR POS stores all your data (products, sales, staff) encrypted **on your own computer**. Nothing is sent to the cloud. This is more secure, but if your computer fails and you have no backup, data recovery is not possible.

---

### Automatic Backups — What the App Does

| When | What |
|------|------|
| Every launch | Full database backup if none exists for today |
| Every night 02:00 | Full database backup |
| Every night 22:00 | Full product list as Excel |
| Product added | Immediate backup |
| Product updated | Immediate backup |
| Product deleted | Immediate backup |

Backups are stored at:
```
C:\Users\[YourUsername]\AppData\Local\MarketPOS\yedek\
```

> `AppData` is a hidden folder. To see it: File Explorer → View → Show hidden items.

---

### Google Drive Auto-Sync (Recommended)

1. Download and install [Google Drive for Desktop](https://www.google.com/drive/download/)
2. Sign in with your Google account
3. Click the Drive icon in the system tray → Settings → **"Back up from computer"**
4. Add the folder: `C:\Users\[YourUsername]\AppData\Local\MarketPOS\yedek\`
5. Done — backups sync to Drive automatically every day

**Storage:** The app caps backups at 500 MB and auto-cleans old files.

---

### Recovery Scenarios

#### Scenario A: App broke, same computer
Uninstall → reinstall → log in with old credentials. Data is preserved. No Drive needed.

#### Scenario B: Disk wiped or Windows reinstalled
Copy `dbkey.bak` → `.dbkey`, `config.bak` → `config.properties`, `market-key.bak` → `market-key.dat` into the `MarketPOS` folder. Install app, log in, then use **Management → Backups → Restore**.

#### Scenario C: New computer
Contact us first at **emirhann0077@gmail.com** for a free license transfer. Then follow Scenario B.

#### Scenario D: Accidentally deleted data
Management screen → Backups tab → select a date → Restore.

---

*Son güncelleme / Last updated: 2026-05-22*
