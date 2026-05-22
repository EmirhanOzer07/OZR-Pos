# Sürüm Geçmişi / Changelog

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
