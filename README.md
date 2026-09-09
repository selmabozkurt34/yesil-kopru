# 🌉 Yeşil Köprü — Aracısız Tarım Pazaryeri

**Yeşil Köprü**, çiftçiler (üreticiler) ile alıcıları aracısız buluşturan bir dijital tarım pazaryeri prototipidir. Üretici kıyısı ile alıcı kıyısı arasında bir köprü kurar: ürün tarladan doğrudan alıcıya geçer, aracı katkısı ve taşıma kayıpları ortadan kalkar.

> Tarım Teknolojileri Yarışması kapsamında hazırlanmış, tarayıcıda doğrudan çalışan bir demo/prototiptir.

---

## 📊 Problem

| İstatistik | Değer |
|---|---|
| Ürünlerin aracılar yüzünden fiyatlanma artışı | **%300 – %600** |
| Tüketiciye ulaşamadan israf olan meyve-sebze | **≈ %53** |
| Yeşil Köprü'deki aracı sayısı | **0** |

Geleneksel zincirde tarladan markete uzanan yolda ürün el değiştirdikçe katlanır; Yeşil Köprü bu zinciri tek bir doğrudan eşleştirmeye indirger.

## ✨ Özellikler

- **Rol tabanlı kimlik doğrulama** — ayrı Giriş / Kayıt akışı; kayıt olurken ad-soyad, telefon, e-posta, il ve rol (Üretici/Alıcı) seçilir. Kullanıcı, rolüne uygun panele otomatik yönlendirilir.
- **Erişim kontrolü** — üretici paneli, alıcı paneli ve lojistik ağı giriş yapmadan kesinlikle görüntülenemez; her rol yalnızca kendi panelini açar.
- **Üretici Paneli** — ürün adı, miktar (kg), fiyat (TL/kg), konum (kayıt ilinden otomatik) ve hasat tarihiyle arz ekleme; aktif arzları listeleme ve silme.
- **Alıcı Paneli** — ürün adı ve ile göre arama; sonuçların **haversine formülü** ile alıcının konumuna olan gerçek coğrafi mesafeye göre yakından uzağa sıralanması.
- **Eşleştirme akışı** — üretici + önerilen taşıyıcı + alıcı bilgisinin yan yana gösterildiği özet ekranı; ürün bedeli + nakliye = toplam şeklinde maliyet dökümü; aracılı zincire kıyasla tahmini tasarruf (+%350 aracı katkısı varsayımıyla). Onaylamayla arz satıldı olarak düşer, sipariş numarası üretilir ve "İşlem Başarılı!" onay ekranı gösterilir.
- **Lojistik Ağı** — taşıyıcı firmalar güzergâh (kalkış→varış ili), kapasite (ton) ve birim ücret (TL/ton) ile kaydolur. Eşleşme sırasında sistem güzergâha ve kapasiteye en uygun taşıyıcıyı otomatik önerir (önce birebir güzergâh, yoksa en yakın hat).
- **Responsive tasarım** — masaüstünde ve mobilde düzgün görünüm; yeşil–bej paleti, tek toprak/bakır vurgu rengi ve rakamsal veriler için mono/teknik font.

## 🔑 Demo Hesapları

Giriş ekranında "Doldur" düğmeleriyle tek tıkla denenebilir:

| Rol | E-posta | Şifre | Konum |
|---|---|---|---|
| 🚜 Üretici | `ahmet@greenbridge.tr` | `123456` | Antalya |
| 🏪 Alıcı | `zeynep@greenbridge.tr` | `123456` | İstanbul |

Kayıt ekranından yeni üretici/alıcı hesapları da oluşturulabilir; prototip 6 hazır kullanıcı, 9 örnek arz, 7 taşıyıcı firma ve 20 illik koordinat listesiyle gelir.

## 🚀 Çalıştırma

Ek bir kurulum gerektirmez:

1. [`yesil-kopru.html`](./yesil-kopru.html) dosyasını indirin.
2. Herhangi bir modern tarayıcıda açın (çift tık yeterli).

Önerilen demo akışı: alıcı hesabıyla giriş yapın → arama sonuçlarının mesafeye göre sıralandığını görün → bir arzda **Eşleştir** deyin → maliyet dökümü ve tasarrufu inceleyin → **Alım-Satımı Onayla** → üretici hesabıyla girip işlemin "Son İşlemler"e düştüğünü görün.

## 🛠 Teknik Notlar

- **Tek dosya**: HTML + CSS + JS tek bir `yesil-kopru.html` içinde; harici framework/backend yoktur.
- **Bellek içi (in-memory) veri**: kalıcı veritabanı yoktur; sayfa yenilendiğinde demo verileri baştan yüklenir (footer'daki "Demo verilerini sıfırla" bağlantısı da aynı işi yapar).
- **Haversine mesafesi**: il koordinatları üzerinden gerçek kuş uçuşu mesafesi hesaplanır; taşıyıcı önerisi de aynı koordinat tabanını kullanır.
- **Demo düzeyi giriş**: şifreler düz metin tutulur; gerçek ödeme, e-posta/SMS bildirimi ve production seviyesinde güvenlik bu aşamanın kapsamı dışındadır.
- **Görsel kimlik**: köprü metaforu; Fraunces (başlık), Manrope (gövde), Space Mono (sayısal veri) fontları.

---

*Yeşil Köprü · Tarladan sofraya aracısız köprü* 🌾
