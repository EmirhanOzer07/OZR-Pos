# Sürüm Geçmişi / Changelog

---

## v2.3.8 — 2026-09-01

### TR — Değişiklikler

**Kararlılık**
- Nadir bir durumda ("erişim engellendi" / uygulama açılmıyor), bilgisayar adı ile Windows kullanıcı adı aynı olduğunda dosya izinleri yanlış ayarlanabiliyordu — düzeltildi.

### EN — Changes

**Stability**
- Fixed a rare case where file permissions could be set incorrectly when the computer name matched the Windows username, causing "access denied" / startup failures.

---

## v2.3.7 — 2026-07-09

### TR — Değişiklikler

**Yönetim Ekranı**
- **Ürün ve kasiyer ekleme/düzenleme ekranları yenilendi:** Daha net ve ferah bir tasarım. Barkodu okutup Enter'a bastıkça sıradaki alana geçersiniz (`↑`/`↓` ile de gezinilir). Hatalar artık pencerenin içinde net görünür.
- **Ürünler sekmesi düzeni iyileştirildi:** Ürün ekleme ile listede arama görsel olarak ayrıldı; arama kutusu artık tabloya bitişik bir "filtre" gibi durur, "buraya barkod yazıp ekleme yapılır mı?" karışıklığı giderildi.

**Kasa Ekranı**
- **Hızlı ürünler artık tam görünür:** Ekrana sığmayan hızlı ürünlere de erişilebilir — hepsi `F4` veya "⤢ Tümü" penceresinde. Ürünleri **sürükleyip bırakarak** istediğiniz sıraya dizebilirsiniz.
- **Başlıkta market adınız ve logonuz:** Sol üstte marketinizin adı görünür. Adı istediğiniz zaman **Yönetim → Yazıcı → "Market Adı"** alanından değiştirebilirsiniz.
- **Satır silme (`Del`) düzeltildi:** Seçili satırı, seçim yoksa son satırı siler; barkod alanı yazımdayken de çalışır.

**Giriş**
- **"Beni hatırla" seçeneği:** Kapalıyken giriş bilgileriniz (şifre dahil) saklanmaz — paylaşımlı kasalarda güvenlik için.

**Yedekleme & Kararlılık**
- Yedekler **günde bir kez** alınır (bazı durumlarda günde iki kez alınması düzeltildi).
- Nadiren görülen **"erişim engellendi"** durumu (lisans önbelleği bozulması) giderildi; genel kararlılık ve güvenlik iyileştirmeleri.

### EN — Changes

**Management Screen**
- **Product & cashier add/edit screens redesigned:** A cleaner, more spacious layout. Scan a barcode and press Enter to jump to the next field (also navigable with `↑`/`↓`). Errors now appear clearly inside the dialog.
- **Products tab layout improved:** Adding products and searching the list are now visually separated; the search box sits as a "filter" attached to the table, removing the confusion of typing a barcode there to add.

**Checkout Screen**
- **Quick products fully visible:** Quick products that don't fit on screen are now reachable — all shown via `F4` or the "⤢ All" window. **Drag and drop** to reorder them.
- **Your store name & logo in the header:** Your store name appears at the top left. Change it anytime from **Management → Printer → "Store Name"**.
- **Row deletion (`Del`) fixed:** Removes the selected row, or the last row if none is selected; works even while typing in the barcode field.

**Login**
- **"Remember me" option:** When off, your login (including password) is not saved — for shared terminals.

**Backup & Stability**
- Backups are taken **once per day** (a case of taking them twice a day was fixed).
- A rare **"access blocked"** situation (license cache corruption) was resolved; general stability and security improvements.

---

## v2.3.6 — 2026-06-17

### TR — Değişiklikler

**Kasa Ekranı**
- **Çoklu sepet (Kasa 1 / 2 / 3):** Aynı anda 3 müşterinin sepetini ayrı tutabilirsiniz. Biri ödeme beklerken diğerinin ürünlerini okutmaya başlayın; `Ctrl+1/2/3` ile kasalar arasında geçin. Sepetler, ürünler ve indirimler birbirinden bağımsızdır; hızlı ürünler ve katalog tüm kasalarda ortaktır.
- **Barkod / Enter düzeltmesi:** Geçersiz barkod sonrası çıkan hata bildirimi, bir sonraki okutmanın Enter'ını yutuyordu; bu yüzden ürünü eklemek için elle Enter'a basmak gerekiyordu. Giderildi — okutma artık kesintisiz devam eder.
- **Nakit ödemede hızlı tam para:** Müşteri tam para verdiyse `F5`–`F5` ile fare/klavyeye dokunmadan satışı kapatın (fişe doğru tutar yazılır).
- **Sepeti temizleme:** `Esc` sonrası açılan onayda `Enter` doğrudan onaylar; iptal için Vazgeç veya tekrar `Esc`.

**Uzun Oturum / Kararlılık**
- **24 saat sorunu giderildi:** Günlerce kapatılmayan kasalarda oturum süresi dolunca "Erişim Engellendi" / ürünler görünmüyor durumu oluşabiliyordu (yeniden başlatma gerekiyordu). Artık net "Oturum süresi doldu — yeniden giriş yapın" uyarısı gelir, giriş sonrası kaldığınız yerden devam edersiniz.
- **Proaktif uyarı her ekranda:** Kasa gibi Yönetim panelinde de, siz hiçbir işlem yapmasanız bile oturum süresi dolunca otomatik uyarı gelir (eskiden yalnız bir işlem yapınca fark ediliyordu).
- **Oturum süresi 24 saatten 3 güne çıkarıldı** — çok daha seyrek yeniden giriş.

**Personel**
- **Yeniden işe alım:** Silinen bir kasiyer, aynı kullanıcı adıyla tekrar eklenebilir (eskiden "bu kullanıcı adı zaten alınmış" hatası veriyordu). Geçmiş satış kayıtları korunur.

**Yedekleme**
- **Uyku sonrası yedek telafisi:** Bilgisayar günlerce uyku modunda kalsa bile, uygulama açık kaldığı sürece günlük yedek ve Excel ürün listesi yedeği otomatik tamamlanır — yeniden başlatmaya gerek kalmadan.
- **Geri yükleme güvenliği:** Geri yükleme sırasında yarım kalma (örn. elektrik kesintisi) ve disk sorunlarına karşı orijinal veriyi koruyan ek güvenceler eklendi.

**Yazıcı**
- **Test fişi durumu net bildiriliyor:** Yazıcı seçili/bağlı değilse artık açık uyarı verir (eskiden her durumda "gönderildi" diyordu).

### EN — Changes

**Sales Screen**
- **Multiple parked carts (Register 1 / 2 / 3):** Hold up to three customers' carts at once. Start scanning a second customer's items while the first waits to pay; switch with `Ctrl+1/2/3`. Carts, products and discounts are independent; quick-product buttons and the catalog are shared across all registers.
- **Barcode / Enter fix:** After scanning an invalid barcode, the error notification consumed the next scan's trailing Enter, forcing a manual Enter to add the product. Fixed — scanning now continues uninterrupted.
- **Fast exact-cash:** When the customer pays the exact amount, press `F5`–`F5` to complete the sale without touching the mouse/keyboard (the receipt records the correct amount).
- **Clear cart:** On the `Esc` confirmation, `Enter` confirms directly; cancel with Cancel or `Esc` again.

**Long Session / Stability**
- **24-hour issue fixed:** On registers left open for days, an expired session could cause "Access Denied" / products not showing (a restart was required). Now a clear "Session expired — please log in again" prompt appears, and you continue where you left off after logging in.
- **Proactive prompt on every screen:** Like the sales screen, the Admin panel now also shows the session-expired prompt automatically even if you take no action (previously it surfaced only when you performed an operation).
- **Session lifetime raised from 24 hours to 3 days** — far less frequent re-login.

**Staff**
- **Re-hire:** A deleted cashier can be re-added with the same username (previously it errored "username already taken"). Past sales records are preserved.

**Backups**
- **Post-sleep backup catch-up:** Even if the computer stays asleep for days, the daily backup and the Excel product-list backup are completed automatically while the app is open — no restart required.
- **Restore safety:** Added safeguards that protect the original data against interrupted restores (e.g., power loss) and disk issues.

**Printer**
- **Clear test-receipt status:** If no printer is selected/connected, a clear warning is now shown (previously it always said "sent").


---

## v2.3.5 — 2026-06-03

### TR — Değişiklikler

**Yönetim Ekranı — Ürün Ekleme**
- **Çift gönderim koruması:** "Ekle" tuşuna veya Enter'a hızlıca iki kez basılınca ürün kaydedildiği hâlde "ürün eklenemedi" uyarısı görülebiliyordu. Kayıt tamamlanana kadar alanlar artık kilitlenir.
- **Anlamlı hata mesajı:** Aynı barkod tekrar eklenmeye çalışılınca "Ürün eklenemedi!" yerine artık "Bu barkod bu markette zaten kayıtlı!" mesajı görünür.
- **Doğru sonuç bildirimi:** Kaydedilemeyen bir ürün için yanlışlıkla "✓ Eklendi" gösterilebiliyordu; artık sonuç her zaman doğru bildirilir.

### EN — Changes

**Management Screen — Product Add**
- **Double-submit protection:** Pressing "Add" or Enter twice quickly could show "product could not be added" even though the product was saved. Fields are now locked until saving completes.
- **Meaningful error message:** Attempting to add a duplicate barcode now shows "This barcode is already registered in this store!" instead of the generic "Product could not be added!"
- **Accurate result message:** A product that could not be saved could incorrectly show "✓ Added"; the result is now always reported correctly.

---

## v2.3.4 — 2026-06-03

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
- **Fiyat düzenleme:** Negatif fiyat girişi artık engelleniyor (önceden kaydedilmese de ekranda "✓ Güncellendi" görünüyordu)
- **Kasiyer ekleme:** Aynı kullanıcı adı eklenmeye çalışıldığında hata mesajı artık ekranda görünüyor (önceden boş görünüyordu)

**Düzeltmeler**
- **Şifre değiştirme (yeni şifre):** Yeni şifrenin sonunda boşluk olduğunda kullanıcı kendi hesabına giremez hale geliyordu; giderildi
- **Şifre değiştirme (mevcut şifre alanı):** Giriş ekranı mevcut şifreyi boşluklu yazınca kabul ederken şifre değiştirme ekranındaki "mevcut şifre" alanı aynı şifreyi reddediyordu; davranış tutarlı hale getirildi
- **Kasiyer ekleme (şifre depolama):** Kasiyer şifresi boşlukla eklendiğinde kasiyer kendi hesabına giremez hale geliyordu; şifre değiştirme ve ilk kurulumla tutarlı şekilde düzeltildi
- **Uygulama simgesi düzeltildi:** v2.3.2 güncellemesiyle birlikte exe içine gömülen ikon bozulmuştu; Windows varsayılan ikonu görünüyordu. Hem görev çubuğu hem masaüstü kısayolu ikonu artık doğru görünür. Yeni kurulum yapan kullanıcılarda ikon hemen düzelir; oto-güncelleme yapanlarda pencere ikonu düzelir.
- Fatura yazdırma hatası artık yazıcı bulunamasa bile kasa ekranında bildirim olarak gösteriliyor

**Kararlılık**
- Uygulama kapanışı hızlandı (kapanırken gereksiz bağlantı beklemesi kaldırıldı)
- Lisans doğrulamasında bağlantı sorunları daha sağlam karşılanıyor
- Lisans bitiş tarihi her girişte otomatik güncelleniyor — uzun vadede "Erişim Engellendi" riski giderildi
- Tema değişikliği daha hızlı
- Hızlı ürün ekleme/düzenleme ekranlarında fiyat hesaplaması kuruş hassasiyetinde

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
- **Price editing:** Negative price entry is now blocked (previously the screen showed "✓ Updated" even though nothing was saved)
- **Add cashier:** Duplicate username error message is now displayed correctly (was blank before)

**Fixes**
- **Password change (new password):** A trailing space in the new password caused the user to be locked out of their account; fixed
- **Password change (current password field):** The login screen accepted the current password with trailing spaces, but the "current password" field in the change dialog rejected it; behavior is now consistent
- **Add cashier (password storage):** A cashier added with a trailing space in their password could not log in to their account; fixed to be consistent with password change and initial setup
- **App icon fixed:** After the v2.3.2 update, the icon embedded in the exe was broken — Windows showed the default Java icon. Both taskbar and desktop shortcut icons now display correctly. Fresh installations from v2.3.3 ZIP fix the icon immediately; users updating via auto-update will see the correct window icon.
- Receipt printing errors now shown as in-app notifications even when no printer is found

**Stability**
- Faster app exit (removed an unnecessary connection wait on close)
- License validation handles connection problems more robustly
- License expiry date now auto-synced on every login — eliminates long-term "Access Denied" risk
- Faster theme switching
- Exact (to-the-cent) price calculation in quick product add/edit dialogs

---

## v2.3.3 — 2026-05-30

### TR — Değişiklikler
- **Uygulama simgesi düzeltildi:** v2.3.2 ile bozulan simge yeniden doğru görünür (yeni kurulumda masaüstü kısayolu dahil; otomatik güncellemede pencere ve görev çubuğu).
- **Güncelleme ekranı:** İlerleme penceresi artık donmuyor; tamamlandı/hata bildirimi otomatik gelir.
- Kasa ekranı iyileştirmelerinin ilk bölümü bu sürümde geldi; tam liste v2.3.4 notlarındadır.

### EN — Changes
- **App icon fixed:** The icon broken in v2.3.2 displays correctly again (including the desktop shortcut on fresh installs; window and taskbar via auto-update).
- **Update screen:** The progress window no longer freezes; completion/error notices appear automatically.
- The first part of the checkout-screen improvements shipped in this release; see the v2.3.4 notes for the full list.

---

## v2.3.2 — 2026-05-28

### TR — Değişiklikler

**Düzeltmeler**
- Oturum süresi dolunca uygulama sessizce çalışmaz hâle geliyor ve giriş ekranına dönmüyordu; artık uyarı verip giriş ekranına yönlendiriyor
- Bazı bilgisayarlarda güncelleme dosyası doğrulaması hatalı olarak başarısız oluyordu; giderildi
- Uygulama simgesi düzeltildi (piksel bozulması)

### EN — Changes

**Fixes**
- When the session expired, the app silently stopped working without returning to the login screen; it now warns and redirects automatically
- On some computers the update file verification failed incorrectly; fixed
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
- Yetki denetimleri güçlendirildi; güvenlik iyileştirmeleri

**Düzeltmeler**
- CSV yükleme: 1 MB'dan büyük dosyalar yüklenemiyordu; artık 5 MB'a kadar destekleniyor
- CSV toplu yüklemeden sonra alınan yedek artık yeni eklenen ürünleri de içeriyor
- İlk kurulumda nadiren görülen takılma riski giderildi
- Büyük dosya yükleme hatası artık "Sunucu hatası oluştu" yerine anlaşılır mesaj veriyor

### EN — Changes

**Security**
- Strengthened authorization checks; security improvements

**Fixes**
- CSV upload: files larger than 1 MB could not be uploaded; now supports up to 5 MB
- The backup taken after a bulk CSV upload now includes the newly added products
- Fixed a rare hang risk during first-time setup
- Large file upload error now returns a clear user message instead of "Server error"

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
- Hızlı ürün ekleme: yeni eklenen ürünün barkodu hemen okutulunca "bulunamadı" görünmesi sorunu giderildi
- Ürün güncelleme (F2 hızlı fiyat, yönetim ekranı düzenleme, CSV çakışma çözümü) artık yedek alıyor

**İyileştirmeler**
- Her satıştan sonra gereksiz veritabanı yedekleme kaldırıldı → satış işlemi belirgin şekilde hızlandı
- Uygulamanın kullanabildiği bellek artırıldı (uzun çalışmada çökme riski azaldı)
- Şifreleme anahtarı yoksa uygulama sessiz hata yerine açık hata mesajı veriyor

**Güvenlik**
- Oturum doğrulaması güçlendirildi

### EN — Changes

**Fixes**
- Quick product add: resolved "barcode not found" immediately after adding a new product
- Product updates (F2 quick price, management screen edit, CSV conflict resolution) now trigger backups

**Improvements**
- Removed unnecessary full database dump after every sale → noticeably faster checkout
- Increased the memory available to the app (reduced risk of crashes on long sessions)
- Encryption key errors now fail with a clear message instead of silent failure

**Security**
- Strengthened session validation

---

## v2.2.9 — 2026-05-21

### TR
- Toplu CSV yükleme: aynı barkodda farklı fiyat/isim çakışması tespit ve çözüm ekranı
- Güncelleme kurulduktan sonra aynı güncellemenin tekrar önerilmesi engellendi
- Satış ekranı indirim özelliği (F3)
- Hata düzeltmeleri ve kararlılık iyileştirmeleri

### EN
- Bulk CSV upload: conflict detection and resolution for duplicate barcodes with different data
- The same update is no longer offered again after it has been installed
- Discount feature on sales screen (F3)
- Bug fixes and stability improvements

---

## v2.2.4 — 2026-05-20

- Güncelleme dialog genişliği ve ilerleme çubuğu düzeltmesi
- Güncelleme sonrası nadiren görülen "uygulama açılmıyor" hatası giderildi

## v2.2.3 — 2026-05-20

- Güncelleme döngüsü ve dialog hataları giderildi

## v2.2.2 — 2026-05-16

- Güvenlik yamaları, hata düzeltmeleri

## v2.2.1 / v2.2.0 — 2026-05

- İlk kararlı 2.x serisi
