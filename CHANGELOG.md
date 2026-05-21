# Sürüm Geçmişi / Changelog

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
