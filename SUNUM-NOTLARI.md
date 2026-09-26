# Yeşil Köprü — Jüri Sunum Hazırlık Notları

Bu doküman, demo sunumu ve jüri soru-cevap bölümü için hazırlık malzemesidir.

---

## 1. Önerilen Demo Senaryosu (5–6 dakika)

| Adım | Ekran | Söyleyecekleriniz | Süre |
|---|---|---|---|
| 1 | Ana sayfa | Problem hikâyesi: çiftçi 1 TL'lik domatesi 4,50 TL'ye satılıyor, %53'ü yolda çürüyor. Köprü metaforunu gösterin. | 45 sn |
| 2 | Ana sayfa → "Gerçek fiyatlarla karşılaştırma" | "Uydurma rakam değil — Eylül 2026 hal bültenlerinden derledik. Domates hâlde 30 TL, bizde ürün+nakliye 19 TL." | 45 sn |
| 3 | Ana sayfa → "Tasarruf hesabı nasıl yapılır?" | Formülü açıklayın; +350'nin rapor bandının orta değeri, tasarrufun alt sınır olduğu vurgusu. | 30 sn |
| 4 | **Demo hesabıyla dene** (Zeynep, alıcı-İstanbul) | Alıcı paneli: mesafe sıralaması (haversine, gerçek koordinatlar). | 45 sn |
| 5 | Bir arzda **Eşleştir** | Üçlü modal: üretici + otomatik önerilen taşıyıcı + alıcı. Maliyet dökümü, tasarruf. **Alım-Satımı Onayla.** | 60 sn |
| 6 | **Siparişi Takip Et** | Durum akışı: Eşleştirildi → Yükleniyor → Yolda → Teslim Edildi. Çıkış yapıp **Ahmet (üretici-Antalya)** ile girin, siparişi yola çıkarın. | 60 sn |
| 7 | Ana sayfa → **Köprünün etkisi** panosu | Sayaçların arttığını gösterin: "her eşleşme bu sayaca yazılıyor". | 30 sn |
| 8 | Kapanış | İş modeli + yol haritası slaytı. | 30 sn |

> **İpucu:** Demo öncesi tarayıcıda "Demo verilerini sıfırla" bağlantısına basın — temiz tohum verisiyle başlarsınız. localStorage olduğu için kapatıp açsanız da veriler korunur.

---

## 2. Muhtemel 10 Jüri Sorusu ve Hazır Cevaplar

### S1 — "Buna gerçekten çiftçi katılır mı? Dijital okuryazarlık düşük."
**Cevap:** Benimseme planımız bunun için var (ana sayfadaki İş Modeli bölümü): SMS/telefonla arz girişi, köy muhtarlıkları ve tarım kooperatifleriyle iş birliği, sahada "tarla destek ekibi". Pilot hedefimiz tek ilde 50 üretici — ölçeklenebilirlik iddiası değil, ölçülebilir bir başlangıç.

### S2 — "Tasarruf hesabını nasıl yaptınız? +350 nereden geliyor?"
**Cevap:** Raporumuzdaki %300–600 aracı katkı bandının **muhafazakâr orta değeri** (×4,5). Formül ana sayfada açık: Geleneksel fiyat = ürün bedeli × 4,5; bizim fiyat = ürün bedeli + nakliye. Bu yüzden gösterdiğimiz tasarruf bir **alt sınırdır** — bant üst sınırına çekilirse tasarruf daha da büyür. Ek olarak gerçek hal bülteni fiyatlarıyla karşılaştırma tablosu koyduk: domateste %36 fark hal fiyatıyla bile doğrulanıyor.

### S3 — "Bu alanlarda başka platformlar var; farkınız ne?"
**Cevap:** Mevcut pazaryerleri ürün listeler ama **lojistiği kullanıcıya bırakır**. Bizim farklılaşmamız üç noktada: (1) güzergâh/kapasite kayıtlı taşıyıcı ağının sistemce **otomatik önerilmesi**, (2) siparişin her iki tarafın onayıyla ilerleyen **paylaşımlı durum akışı**, (3) israf azaltmanın metrik olarak takip edilmesi (etki panosu). Sözleşmeli üretim (sezon öncesi ön anlaşma) yol haritamızdaki bir sonraki farklılaştırıcıdır.

### S4 — "Sayfayı yenileyince veriler gidiyor mu?"
**Cevap:** Hayır — prototip artık `localStorage` ile çalışıyor; arzlar, siparişler ve oturum yenilenince korunuyor. Üretime geçişte tek değişen bu katmanın gerçek bir veritabanına (ör. PostgreSQL + REST API) bağlanması; arayüz kodunun büyük kısmı aynı kalır.

### S5 — "Nakliye fiyatı gerçekçi mi?"
**Cevap:** Lojistik ağındaki birim ücretler (300–640 TL/ton) Türkiye'deki sefer piyasası aralıklarıyla uyumlu örnek değerler. Sistem nakliyeyi yük tonajına göre hesaplar ve tek araca 25 ton (tır dorse) üst sınır koyar; daha büyük yükler birden fazla araçla karşılanır.

### S6 — "Ödeme/güven nasıl olacak? Çiftçi parasını alamazsa?"
**Cevap:** Modelimizde ödeme, alıcı tarafından **escrow (aracı havuz) hesabına** yapılır; ürün teslim onaylanmadan üreticiye aktarılmaz. Uyuşmazlıkta platform karar süreci işletir. Taşıyıcılar kapasite beyanıyla kaydolur ve değerlendirme puanı alır. (Bu demo düzeyinde simüle ediliyor; gerçek entegrasyon ödeme kuruluşu iş birliğiyle olur.)

### S7 — "Platform işten ne kazanıyor?"
**Cevap:** Tamamlanan işlemde %2–3 komisyon + taşıyıcıdan sefer başına küçük hizmet payı. Kritik nokta: üreticinin kaydı, arzı ve araması **ücretsiz** — platform, yalnızca değer yaratıldığında (işlem gerçekleştiğinde) gelir elde eder. Bu, benimseme engelini kaldırır.

### S8 — "Mesafeyi/sıralamayı nasıl hesaplıyorsunuz?"
**Cevap:** 20 il için gerçek enlem-boylam koordinatlarıyla **haversine formülü** (kuş uçuşu mesafe). Sonuçlar alıcının konumuna olan mesafeye göre artan sıralanır; taşıyıcı önerisi de önce birebir güzergâh, sonra en yakın hat mantığıyla aynı koordinat tabanını kullanır.

### S9 — "Bunu kim test etti? Kullanıcı araştırması yaptınız mı?"
**Cevap:** Dürüst cevap: prototip aşamasındayız; hedefimiz jüri önünde işlevselliği kanıtlamak. Pilot planımız (50 üretici) ilk kullanıcı araştırması döngüsüdür — ölçülecek metrikler: arz girişinde tamamlama oranı, eşleşme-teslim oranı, tekrar satış oranı. *(Eğer gerçekten çevrenizde çiftçi/tüccarla konuştysanız burada o anekdotu anlatın — en güçlü cevap olur.)*

### S10 — "Ölçeklenince ne olur? Arz-talep çift taraflı ağ problemi değil mi?"
**Cevap:** Doğru tespit — bu yüzden coğrafi yoğunlaşma stratejisi uyguluyoruz: ülke geneli yerine **tek ilde kritik kütle** kurup (pilot), yan yana illere genişlemek. Yoğun ilde mesafeler kısa, nakliye ucuz, eşleşme hızlı olur; bu da ağ etkisini bölgesel olarak başlatır. Soğuk zincir entegrasyonu (2027 H1) bozulabilir ürün kategorisini açar.

---

## 3. "Prototipten Ürüne" Teknik Notu (S4'ün derinleştirilmiş hâli)

| Katman | Prototipte | Üretimde |
|---|---|---|
| Veri | localStorage (tarayıcı) | PostgreSQL + API (ör. Supabase/Firebase hızlı başlangıç) |
| Kimlik | Demo düzeyi kontrol | SMS doğrulamalı oturum, rol bazlı yetki (RBAC) |
| Fotoğraf | Canvas ile 720px küçültme, data URL | Nesne depolama (S3 benzeri) + CDN |
| Bildirim | Toast (ekran içi) | SMS/push: "siparişiniz yola çıktı" |
| Ödeme | Simüle (escrow anlatımı) | Ödeme kuruluşu entegrasyonu (iyzico vb.) |
| Eşleştirme | Kural tabanlı (güzergâh + kapasite + mesafe) | Aynı kurallar + zamanla öğrenen öneri |

---

## 4. Kısa Kapanış Cümlesi (öneri)

> "Yeşil Köprü, %300–600'lük aracı katkısını ve %53'lük israfı tek bir doğrudan eşleştirmeye indirger. Bugün gösterdiğimiz prototip, tarladan sofraya uzanan yolda sadece iki taraf bırakıyor: üreten ve alan."
