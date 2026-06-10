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

Yedekler şu konumda saklanır:
```
C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\yedek\
```

> `AppData` klasörü gizlidir. Görmek için: Dosya Gezgini → Görünüm → Gizli öğeleri göster.

---

### ⚠️ Önemli: Yedek Dosyaları Windows'ta Açılmaz — Bu Normaldir

`gunluk\` ve `islem\` klasörlerindeki `.zip` dosyalarına çift tıklarsanız Windows
**"Sıkıştırılmış klasör geçersiz"** der. Bu bir hata DEĞİLDİR:

- Yedekleriniz market verinizi (satışlar, ürünler, personel) içerdiği için **AES-256 ile şifrelenir**. Windows şifreli dosyayı açamaz — açabilseydi, dosyayı ele geçiren herkes de açabilirdi.
- Yedekler **yalnızca uygulama içinden** geri yüklenir: Yönetim Ekranı → Yedekler sekmesi. Uygulama şifreyi otomatik çözer.
- Yedeklerin sağlıklı olduğunu dosyayı açarak değil, **tarihine ve boyutuna** bakarak doğrulayın (güncel tarihli ve 0 KB'tan büyük olmalı).

> `yedek` klasörünün kökünde `veri_...zip` adında eski dosyalar görebilirsiniz — bunlar eski sürümlerden kalan şifresiz yedeklerdir, Windows açabilir ama uygulama artık bunları geri yüklemez. Güncel yedekleriniz `gunluk\` ve `islem\` klasörlerindekilerdir.

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

Bu bilgiler bilgisayar değiştirmeniz gerektiğinde hayat kurtarır.

---

### Veri Kurtarma Senaryoları

---

#### Senaryo A: Uygulama bozuldu — Aynı bilgisayar ✅ Kolay

Bu en basit durumdur. Windows'ta uygulama kaldırıldığında veriler silinmez.

1. Eski uygulamayı kaldırın (Ayarlar → Uygulamalar → OZRPos)
2. Yeni sürümü indirip kurun
3. Eski kullanıcı adı ve şifrenizle giriş yapın
4. Verileriniz yerli yerinde

Google Drive'a gerek yoktur.

---

#### Senaryo B: Disk formatlandı veya Windows yeniden kuruldu ⚠️ Orta

Bu senaryoda veritabanı sıfırdan başlar. Bu yüzden önceki yedeği **uygulamayı açmadan önce** geri yüklemek gerekir. Adımları sırayla ve eksiksiz takip edin.

**Bu adımları kendiniz yapamıyorsanız adımların sonundaki [iletişim bölümüne](#senaryo-b-iletisim) geçin — uzaktan bağlanıp sizin yerinize yapabiliriz.**

---

**Adım 1 — Gerekli klasörü oluşturun**

Şu klasörü oluşturun (yoksa):
```
C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\
```

---

**Adım 2 — Yapılandırma dosyalarını Drive'dan kopyalayın**

Google Drive'daki `yedek` klasörünün içindeki şu dosyaları `MarketPOS` klasörüne kopyalayın.
Dosya adlarına **dikkat edin** — nokta ile başlayanlar dahil:

| Drive'daki ad | MarketPOS klasöründe olacak ad |
|---------------|-------------------------------|
| `dbkey.bak` | `.dbkey` *(nokta ile başlıyor)* |
| `config.bak` | `config.properties` |
| `market-key.bak` | `market-key.dat` |

> ⚠️ **Kritik:** `.dbkey` dosyası olmadan yedekler açılamaz. Bu dosyanın Drive'da olduğundan emin olun.

---

**Adım 3 — Yedek ZIP dosyalarını kopyalayın**

Şu klasörü oluşturun ve Drive'daki ZIP yedek dosyalarını buraya kopyalayın:
```
C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\yedek\gunluk\
```
Bu klasörde `gunluk_TARIH.zip` formatında dosyalar olmalıdır. En son tarihlisi geri yükleme için kullanılacak.

---

**Adım 4 — Geri yükleme tetikleyicisini oluşturun**

> Bu adım çok önemlidir ve uygulamayı açmadan önce tamamlanmalıdır.

1. **Not Defteri (Notepad)** uygulamasını açın (Başlat menüsünde arayın)
2. Geri yüklemek istediğiniz ZIP dosyasının **tam yolunu** yazın. Örnek:
   ```
   C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\yedek\gunluk\gunluk_2026-05-31_02-00-00.zip
   ```
   *(Köşeli parantezleri kendi Windows kullanıcı adınızla değiştirin, tarihi Drive'daki dosyaya göre ayarlayın)*
3. **Dosya → Farklı Kaydet** menüsüne tıklayın
4. Şu ayarları yapın:
   - **Konum:** `C:\Users\[KullanıcıAdınız]\AppData\Local\MarketPOS\`
   - **Dosya adı:** `pending_restore.flag`
   - **Kayıt türü:** Tüm Dosyalar (\*.\*) — bu seçimi değiştirmeyi unutmayın
5. **Kaydet'e** tıklayın

> **Not:** Dosyanın uzantısı `.flag` olmalı, `.flag.txt` olmamalıdır. Klasör görünümünde dosya adını kontrol edin.

---

**Adım 5 — Uygulamayı çalıştırın**

Uygulamayı açın. Uygulama `pending_restore.flag` dosyasını açılış sırasında otomatik algılar ve yedeği geri yükler. Bu süreçte herhangi bir şey yapmanıza gerek yoktur; açılış normalden biraz uzun sürebilir, uygulama doğrudan giriş ekranıyla açılır.

---

**Adım 6 — Giriş yapın**

Eski patron hesabınızla giriş yapın. Tüm verileriniz (ürünler, satışlar, personel) geri yüklenmiş olacaktır.

---

<a name="senaryo-b-iletisim"></a>

> 📞 **Bu adımları kendiniz yapamıyorsanız — iletişime geçin:**
>
> **emirhann0077@gmail.com** adresine yazın veya arayın.
> Uzaktan bağlantı (TeamViewer / AnyDesk) ile tüm adımlar sizin yerinize gerçekleştirilebilir.

---

#### Senaryo C: Yeni bilgisayar aldınız 📞 Geliştirici Gerekli

Yeni bilgisayara geçişte **önce bizimle iletişime geçin.**

1. **emirhann0077@gmail.com** adresine yazın, lisans aktarımı talep edin
2. Size yeni bir **aktivasyon (davetiye) kodu** iletilir
3. **Senaryo B'deki adımları** izleyin — tek farkla: Adım 2'de `market-key.bak` dosyasını **KOPYALAMAYIN** (eski bilgisayarın lisans kaydıdır; kopyalanırsa "Erişim Engellendi" ekranı görürsünüz). Yalnızca `dbkey.bak → .dbkey` ve `config.bak → config.properties` kopyalanacak.
4. Uygulama verileri geri yükledikten sonra açılışta lisans aktivasyon ekranı çıkar — size iletilen davetiye kodunu ve market adınızı girin

Lisans aktarımı **ücretsizdir.**

---

#### Senaryo D: Yanlışlıkla ürünler silindi veya veri bozuldu ✅ Kolay

Uygulama çalışıyor ve giriş yapabiliyorsunuz.

1. **Yönetim Ekranı → Yedekler sekmesi**
2. Listeden geri dönmek istediğiniz tarihe ait yedeği seçin
3. **Geri Yükle** butonuna tıklayın
4. Çift onay ekranını geçin — uygulama kendini kapatır
5. **Uygulamayı yeniden açın** — açılışta yedek otomatik yüklenir, seçtiğiniz tarihteki verilerle devam edersiniz

> Yedekler listesi boşsa `yedek\gunluk\` klasörünü kontrol edin; ZIP dosyaları orada olmalı.

---

### Yedek Sağlık Kontrolü

Ayda bir şu kontrolleri yapın:

- [ ] Google Drive'da `yedek` klasörü güncel mi? (Son 7 günde en az 1 ZIP görünmeli)
- [ ] `yedek\gunluk\` klasöründe güncel tarihli, 0 KB'tan büyük ZIP dosyaları var mı?
- [ ] `yedek\dbkey.bak` dosyası mevcut mu?
- [ ] Patron hesabı şifrenizi hatırlıyor musunuz?

> ZIP dosyalarını çift tıklayıp açmayı **denemeyin** — şifreli oldukları için Windows "geçersiz" der, bu normaldir (yukarıdaki bölüme bakın).

---

### Geliştirici Müdahale Rehberi

> Bu bölüm müşteri aradığında **geliştirici olarak** yapılacak adımları açıklar.

#### Senaryo B — Müşteri Diski Formatladı

Amaç: `pending_restore.flag` dosyasını oluşturarak uygulamanın startup'ta otomatik restore yapmasını sağlamak.

**Yöntem 1: Uzaktan bağlantı (AnyDesk / TeamViewer)**

1. Müşteriye AnyDesk veya TeamViewer kurdurun, erişim kodunu alın
2. Bağlandıktan sonra sırayla:
   - Drive'dan `.dbkey`, `config.properties`, `market-key.dat` dosyalarını `MarketPOS` klasörüne kopyalayın
   - `MarketPOS\yedek\gunluk\` klasörünü oluşturun, Drive'daki ZIP'leri kopyalayın
   - Not Defteri ile `pending_restore.flag` dosyasını oluşturun (içine en son ZIP'in tam yolunu yazın)
   - Uygulamayı çalıştırın — otomatik restore başlar
3. Müşteri patron hesabıyla başarıyla giriş yapabildikten sonra işlem tamamdır

**Yöntem 2: Telefon rehberliği**

Müşteriyle telefonda Senaryo B adımlarını birebir takip edin. Dikkat edilecekler:

- **Adım 2:** `.dbkey` dosyası nokta ile başlıyor; dosya adı yanlış girilmemeli
- **Adım 4:** Not Defteri → Farklı Kaydet → Kayıt türünü "Tüm Dosyalar" olarak seçmesi şart; aksi halde `.flag.txt` olarak kaydeder ve uygulama dosyayı görmez
- **Adım 4:** ZIP dosyasının tam yolunu doğru yazdığından emin olun (tarih ve sürücü harfi dahil)

---

#### Senaryo C — Yeni Bilgisayar

1. OZR POS PatronEkrani'nı açın
2. Market sekmesinden müşterinin eski kaydını bulun
3. Eski market anahtarını devre dışı bırakın veya yeni kayıt oluşturun
4. Müşteriye yeni aktivasyon bilgisini iletin
5. Ardından Senaryo B adımlarını müşteriye telefon/uzaktan bağlantıyla uygulayın

---

## EN — English

### Why Backups Matter

OZR POS stores all your data (products, sales, staff) encrypted **on your own computer**. Nothing is sent to the cloud. This is more secure, but if your computer fails without a backup, data recovery is not possible.

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

> `AppData` is a hidden folder. To view it: File Explorer → View → Show hidden items.

---

### ⚠️ Important: Backup Files Won't Open in Windows — This Is Normal

If you double-click the `.zip` files in `gunluk\` or `islem\`, Windows says **"The compressed folder is invalid"**. This is NOT an error:

- Backups contain your business data, so they are **encrypted with AES-256**. Windows cannot open an encrypted file — if it could, so could anyone who copied it.
- Backups can only be restored **from inside the app**: Management Screen → Backups tab. The app decrypts them automatically.
- To verify a backup is healthy, check its **date and size** (recent date, larger than 0 KB) — do not try to open it.

> You may see older `veri_...zip` files in the root of the `yedek` folder — these are unencrypted backups from older versions; Windows can open them but the app no longer restores them. Your current backups are the ones in `gunluk\` and `islem\`.

---

### Google Drive Auto-Sync (Recommended)

1. Download and install [Google Drive for Desktop](https://www.google.com/drive/download/)
2. Sign in with your Google account
3. Click the Drive icon in the system tray → Settings → **"Back up from computer"**
4. Add: `C:\Users\[YourUsername]\AppData\Local\MarketPOS\yedek\`
5. Done — backups sync to Drive automatically.

**Storage:** The app caps backups at 500 MB and auto-cleans old files.

---

### Recovery Scenarios

#### Scenario A: App broke, same computer ✅ Easy

Uninstall → reinstall → log in with old credentials. Data is preserved. No Drive needed.

---

#### Scenario B: Disk wiped or Windows reinstalled ⚠️ Intermediate

The database starts empty after a wipe, so you must restore the backup **before launching the app**. Follow these steps in order.

**Step 1 — Create the folder**

Create this folder if it doesn't exist:
```
C:\Users\[YourUsername]\AppData\Local\MarketPOS\
```

**Step 2 — Copy configuration files from Drive**

Copy these files from your Google Drive `yedek` folder into `MarketPOS`. Pay attention to the exact names:

| Drive file | Name in MarketPOS folder |
|------------|--------------------------|
| `dbkey.bak` | `.dbkey` *(starts with a dot)* |
| `config.bak` | `config.properties` |
| `market-key.bak` | `market-key.dat` |

> ⚠️ Without `.dbkey`, backup files cannot be decrypted and data cannot be recovered.

**Step 3 — Copy backup ZIP files**

Create this folder and copy your ZIP backups from Drive into it:
```
C:\Users\[YourUsername]\AppData\Local\MarketPOS\yedek\gunluk\
```

**Step 4 — Create the restore trigger file**

> Do this **before** launching the app.

1. Open **Notepad**
2. Type the full path to the ZIP backup you want to restore. Example:
   ```
   C:\Users\[YourUsername]\AppData\Local\MarketPOS\yedek\gunluk\gunluk_2026-05-31_02-00-00.zip
   ```
3. Go to **File → Save As**:
   - **Location:** `C:\Users\[YourUsername]\AppData\Local\MarketPOS\`
   - **File name:** `pending_restore.flag`
   - **Save as type:** All Files (\*.\*)
4. Click **Save**

> Check that the file is named `pending_restore.flag` and not `pending_restore.flag.txt`.

**Step 5 — Launch the app**

Open the app. It will detect the flag file during startup and **automatically restore your database**. Startup may take a little longer than usual; the app then opens directly to the login screen.

**Step 6 — Log in**

Log in with your patron account credentials. All your data will be restored.

---

> 📞 **If you cannot complete these steps — contact us:**
>
> Email **emirhann0077@gmail.com** — we can connect remotely and complete the restore for you.

---

#### Scenario C: New computer 📞 Developer Required

When moving to a new computer, **contact us first.**

1. Email **emirhann0077@gmail.com** to request a license transfer
2. We will provide a new **activation (invitation) code**
3. Follow **Scenario B** above with one difference: in Step 2, do **NOT** copy `market-key.bak` (it is the old computer's license record; copying it shows an "Access Denied" screen). Copy only `dbkey.bak → .dbkey` and `config.bak → config.properties`.
4. After the data is restored, the app shows a license activation screen on startup — enter the invitation code and your store name

License transfer is **free of charge.**

---

#### Scenario D: Accidentally deleted data ✅ Easy

The app is running and you can log in.

1. **Management Screen → Backups tab**
2. Select the backup from the date you want to restore
3. Click **Restore**
4. Confirm twice — the app closes itself
5. **Reopen the app** — the backup is applied during startup and your data from the selected date is restored

---

### Monthly Health Check

- [ ] Is the Drive `yedek` folder up to date? (At least 1 ZIP from the last 7 days)
- [ ] Are recent ZIP files (larger than 0 KB) present in `yedek\gunluk\`?
- [ ] Does `yedek\dbkey.bak` exist?
- [ ] Do you remember your patron account password?

> Do **not** try to open the ZIP files by double-clicking — they are encrypted, so Windows reports them as "invalid". This is normal (see the section above).

---

*Son güncelleme / Last updated: 2026-06-10*
