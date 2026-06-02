# Sürüm Geçmişi / Changelog

---

## v2.3.3 — 2026-06-02

### TR — Değişiklikler

**Kasa Ekranı**
- Bildirim kutusu artık kasa ekranının odağını çalmıyor — barkod okumaya devam edilebilir
- Hızlı ürün tuşlarına miktar öneki desteği: `3*barkod` yazıp Enter ile doğrudan 3 adet eklenebilir
- Hızlı ürün tuşlarına sağ tık menüsü eklendi: isim/fiyat düzenleme ve tuşu kaldırma
- Bulunamayan barkodlar listesine zaman damgası eklendi; liste uygulama yeniden başlatılsa bile korunur
- Ağ durumu göstergesi: ürün önbelleği yüklenirken bağlantı başarısız olursa kırmızı uyarı
- **Uzun süreli oturum kararlılığı:** Gece açık kalan marketlerde lisans yenilendikten sonra barkod okutulunca "Erişim Engellendi" hatası oluşabiliyordu; giderildi

**Yönetim Ekranı**
- Rapor sekmesine "Tüm Zamanlar" butonu eklendi — tüm geçmişi tek tıkla görüntüleme
- Ciro sekmesi kaldırıldı (rapor sekmesi tüm ihtiyacı karşılıyor)
- **Fiyat düzenleme:** Negatif fiyat girişi artık engelleniyor (önceden backend 400 dönse de ekranda "✓ Güncellendi" görünüyordu)
- **Kasiyer ekleme:** Aynı kullanıcı adı eklenmeye çalışıldığında hata mesajı artık ekranda görünüyor (önceden boş görünüyordu)

**Patron Ekranı**
- Market tablosuna "Son Bağlantı" sütunu eklendi — her marketin en son ne zaman aktif olduğu görülebiliyor (Az önce / N saat önce / N gün önce / Hiç bağlanmadı)
- Son Bağlantı sütununda saat farkı artık doğru hesaplanıyor (UTC düzeltmesi)
- Geçmiş tarihle lisans uzatma artık engelleniyor
- Market aktif/deaktif değiştirme işleminin sonucu artık doğru bildiriliyor

**Düzeltmeler**
- **Şifre değiştirme (yeni şifre):** Yeni şifrenin sonunda boşluk olduğunda kullanıcı kendi hesabına giremez hale geliyordu; giderildi
- **Şifre değiştirme (mevcut şifre alanı):** Giriş ekranı mevcut şifreyi boşluklu yazınca kabul ederken şifre değiştirme ekranındaki "mevcut şifre" alanı aynı şifreyi reddediyordu; davranış tutarlı hale getirildi
- **Uygulama simgesi düzeltildi:** v2.3.2 güncellemesiyle birlikte exe içine gömülen ikon bozulmuştu; Windows varsayılan ikonu görünüyordu. Kök neden: ICO dosyası eski BMP formatındaydı, .NET yükleyemiyordu. PNG formatına dönüştürüldü — hem görev çubuğu hem masaüstü kısayolu ikonu artık doğru görünür. Yeni kurulum yapan kullanıcılarda ikon hemen düzelir; oto-güncelleme yapanlarda pencere ikonu düzelir.
- Fatura yazdırma hatası artık yazıcı bulunamasa bile kasa ekranında bildirim olarak gösteriliyor

**Teknik**
- Uygulama kapatılırken gereksiz lisans sunucusu isteği kaldırıldı — bağlantı hatası oluşmuyordu ama gereksiz gecikme yaratıyordu
- Lisans sunucusuna bağlantı hataları (429, 500 vb.) artık tutarlı şekilde işleniyor
- Lisans bitiş tarihi her girişte otomatik güncelleniyor — uzun vadede "Erişim Engellendi" riski giderildi
- Tema değişikliği sırasında CSS geçici dosyası yeniden oluşturulmaz (önbellekleme)
- Hızlı ürün ekleme/düzenleme diyaloglarında fiyat hesaplaması kesinlik artırıldı (BigDecimal)
- Kod kalitesi iyileştirmeleri: APPDATA yolu tek kaynaktan yönetiliyor, ölü kod temizlendi
- Test sayısı: 123

### EN — Changes

**Sales Screen**
- Notification popup no longer steals focus from the barcode field — scanning can continue uninterrupted
- Quick product buttons now support quantity prefix: type `3*barcode` + Enter to add 3 units at once
- Right-click menu on quick product buttons: edit name/price or remove the button
- Not-found barcode list now shows timestamps; list persists across app restarts
- Network indicator: turns red if product cache fails to load on startup
- **Long-session stability:** Fixed "Access Denied" errors that could occur on barcode scan after a license renewal while the app was left open overnight

**Management Screen**
- "All Time" button added to the Report tab — view full history with one click
- Revenue tab removed (the Report tab covers all use cases)
- **Price editing:** Negative price entry is now blocked (previously the backend rejected it with 400 but the screen showed "✓ Updated")
- **Add cashier:** Duplicate username error message is now displayed correctly (was blank before)

**Owner Screen**
- "Last Connection" column added to market table — shows when each store last connected (Just now / N hours ago / N days ago / Never connected)
- Last Connection time difference now calculated correctly (UTC fix)
- Setting a past date for license renewal is now blocked
- Active/deactivate market result is now reported correctly

**Fixes**
- **Password change (new password):** A trailing space in the new password caused the user to be locked out of their account; fixed
- **Password change (current password field):** The login screen accepted the current password with trailing spaces, but the "current password" field in the change dialog rejected it; behavior is now consistent
- **App icon fixed:** After the v2.3.2 update, the icon embedded in the exe was broken — Windows showed the default Java icon. Root cause: the ICO file was in legacy BMP format that .NET cannot load. Converted to PNG format — both taskbar and desktop shortcut icons now display correctly. Fresh installations from v2.3.3 ZIP fix the icon immediately; users updating via auto-update will see the correct window icon.
- Receipt printing errors now shown as in-app notifications even when no printer is found

**Technical**
- Removed unnecessary license server call on app exit
- License server connection errors (429, 500, etc.) now handled consistently
- License expiry date now auto-synced on every login — eliminates long-term "Access Denied" risk
- CSS temp file is no longer recreated on every theme toggle (caching)
- Improved price calculation precision in quick product add/edit dialogs (BigDecimal)
- Code quality: AppData path now sourced from a single location; dead code removed
- Test count: 123

---

## v2.3.2 — 2026-05-28

### TR — Değişiklikler

**Düzeltmeler**
- JWT oturumu sona erince uygulama sessizce çöküyor ve giriş ekranına dönmüyordu; artık otomatik olarak giriş ekranına yönlendiriyor
- SHA-256 doğrulaması: bazı sistemlerde dosya hash'i başına BOM karakteri ekleniyordu; temizlendi — güncelleme doğrulama hatası giderildi
- Uygulama simgesi düzeltildi (piksel bozulması)

### EN — Changes

**Fixes**
- When the JWT session expired, the app crashed silently without returning to the login screen; it now redirects automatically
- SHA-256 verification: some systems prepended a BOM character to the file hash, causing update validation to fail; cleaned up
- Application icon rendering fix (pixel corruption)

---

## v2.3.1 — 2026-05-23

### TR — Değişiklikler

**İyileştirmeler**
- v2.3.0 kullanıcılarının otomatik güncelleme alabilmesi için sürüm numarası güncellendi
- Tablo sütun genişlikleri DPI ölçeğine göre düzeltildi — farklı ekran çözünürlüklerinde görünüm bozulmuyor
- Giriş ekranı tam ekranda açılıyor

### EN — Changes

**Improvements**
- Version number updated so v2.3.0 users receive the auto-update notification
- Table column widths fixed for DPI scaling — layout no longer breaks on non-standard resolutions
- Login screen now opens in full-screen mode

---

## v2.3.0 — 2026-05-22

### TR — Değişiklikler

**Güvenlik**
- UrunController: `@Cacheable` kaldırıldı — cache hit'te market yetki kontrolü atlanıyordu, artık her istekte çalışır
- SatisRepository: `findAllByKullaniciId` sorgusuna eksik `market.id` filtresi eklendi

**Düzeltmeler**
- CSV yükleme: 1 MB'dan büyük dosyalar Spring multipart filtresi nedeniyle 500 döndürüyordu; artık 5 MB'ya kadar destekleniyor
- CSV yükleme: toplu yükleme yedeği artık transaction commit sonrası alınıyor — yeni ürünler artık yedeğe dahil
- VeriTabaniAnahtarService: `icacls` process pipe buffer deadlock riski giderildi
- Büyük dosya yükleme hatası artık "Sunucu hatası oluştu" yerine anlaşılır mesaj veriyor

**Testler**
- JWT süresi dolmuş token reddi testi eklendi
- Satış özeti endpoint'inde market izolasyon testi eklendi
- CSV dosya boyutu sınırı (5 MB) testi eklendi
- CSV hatalı Content-Type reddi testi eklendi (CWE-434)
- Toplam test sayısı: 118

### EN — Changes

**Security**
- UrunController: removed `@Cacheable` — authorization check was bypassed on cache hits; now runs on every request
- SatisRepository: added missing `market.id` filter to `findAllByKullaniciId`

**Fixes**
- CSV upload: files larger than 1 MB returned HTTP 500 due to Spring multipart limit; now supports up to 5 MB
- CSV upload: bulk upload backup now taken after transaction commit — newly added products are included
- VeriTabaniAnahtarService: fixed `icacls` process pipe buffer deadlock risk
- Large file upload error now returns a clear user message instead of "Server error"

**Tests**
- Added JWT expired token rejection test
- Added sales summary endpoint market isolation test
- Added CSV file size limit (5 MB) test
- Added CSV wrong Content-Type rejection test (CWE-434)
- Total test count: 118

---

## v2.2.11 — 2026-05-22

### TR — Değişiklikler

**Düzeltmeler**
- Güncelleme ekranı: indirme sırasında ilerleme çubuğu boş görünüyordu, animasyon artık düzgün çalışıyor
- Güncelleme tamamlandıktan sonra "Güncelleme başarıyla tamamlandı" onay ekranı bazen görünmüyordu, düzeltildi

**İyileştirmeler**
- Güncelleme indirme sırasında gereksiz arayüz çağrıları azaltıldı → daha akıcı ilerleme göstergesi

### EN — Changes

**Fixes**
- Update screen: progress bar appeared empty during download; animation now works correctly
- "Update completed successfully" confirmation dialog was sometimes missing after update; fixed

**Improvements**
- Reduced unnecessary UI calls during update download for smoother progress display

---

## v2.2.10 — 2026-05-22

### TR — Değişiklikler

**Düzeltmeler**
- Hızlı ürün ekleme: Barkod okutulduktan hemen sonra ürün bulunamıyor sorun giderildi
- Ürün güncelleme (F2 hızlı fiyat, yönetim ekranı düzenleme, CSV çakışma çözümü) artık yedek alıyor

**İyileştirmeler**
- Her satıştan sonra gereksiz veritabanı yedekleme kaldırıldı → satış işlemi belirgin şekilde hızlandı
- Uygulama bellek sınırı 256 MB → 512 MB olarak artırıldı (uzun çalışmada çöküş riski azaldı)
- Şifreleme anahtarı yoksa uygulama sessiz hata yerine açık hata mesajı veriyor

**Güvenlik**
- Yönetici API erişimi için JWT doğrulaması güçlendirildi

---

### EN — Changes

**Fixes**
- Quick product add: resolved "barcode not found" immediately after adding a new product
- Product updates (F2 quick price, admin edit, CSV conflict resolution) now trigger backups

**Improvements**
- Removed unnecessary full database dump after every sale → noticeably faster checkout
- JVM heap increased 256 MB → 512 MB (reduced risk of out-of-memory crashes on long sessions)
- Encryption key errors now fail with a clear message instead of silent failure

**Security**
- Strengthened JWT validation for admin API access

---

## v2.2.9 — 2026-04-10

### TR
- Toplu CSV yükleme: aynı barkodda farklı fiyat/isim çakışması tespit ve çözüm ekranı
- Güncelleme döngüsü önleme: `.installed_version` dosyası ile sürüm takibi
- Satış ekranı indirim özelliği (F3)
- Hata düzeltmeleri ve kararlılık iyileştirmeleri

### EN
- Bulk CSV upload: conflict detection and resolution for duplicate barcodes with different data
- Update loop prevention via `.installed_version` file
- Discount feature on sales screen (F3)
- Bug fixes and stability improvements

---

## v2.2.4

- Güncelleme dialog genişliği ve ilerleme çubuğu düzeltmesi
- H2 kilit retry mekanizması

## v2.2.3

- Güncelleme döngüsü ve dialog hataları giderildi

## v2.2.2

- Güvenlik yamaları, hata düzeltmeleri

## v2.2.1 / v2.2.0

- İlk kararlı 2.x serisi
