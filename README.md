# idiqutgames.com

İdiqut Games kurumsal web sitesi. Tek sayfa, statik, hiçbir dış bağımlılığı yok
(font/script/CDN çağrısı yapmaz — çok hızlı açılır, çerez kullanmaz).

**Hosting:** GitHub Pages · **Repo:** `sadam7846466-gif/idiqutgames-website` · **Branch:** `main`

---

## ⚠️ YAPILACAK: GoDaddy DNS ayarı

Site yayında ama domain hâlâ GoDaddy'nin park sayfasını gösteriyor.
Bunu düzeltmek için GoDaddy'de DNS kayıtlarını değiştirmen lazım — 3 dakikalık iş.

### Adımlar

1. https://dcc.godaddy.com/control/portfolio adresine gir
2. `idiqutgames.com` yanındaki **DNS** / **Manage DNS** butonuna bas
3. Listede duran hazır kayıtları **sil**:
   - `A` tipinde, adı `@` olan kayıt (park IP'sine gidiyor)
   - `CNAME` tipinde, adı `www` olan kayıt
4. Aşağıdaki **5 kaydı** ekle:

| Type  | Name | Value                        | TTL      |
|-------|------|------------------------------|----------|
| A     | @    | `185.199.108.153`            | 1 Hour   |
| A     | @    | `185.199.109.153`            | 1 Hour   |
| A     | @    | `185.199.110.153`            | 1 Hour   |
| A     | @    | `185.199.111.153`            | 1 Hour   |
| CNAME | www  | `sadam7846466-gif.github.io` | 1 Hour   |

> Evet, 4 tane `A` kaydı ve hepsinin adı `@`. Doğru — GitHub'ın 4 sunucusu var.
> CNAME değerinin sonundaki nokta önemli değil, GoDaddy kendi ekler.

5. **Save** / **Kaydet**

### Sonra

DNS'in yayılması genelde 10 dakika – 1 saat sürer (bazen 24 saate kadar).
Sonrasında `https://idiqutgames.com` açılacak. SSL sertifikası GitHub tarafından
otomatik ve ücretsiz kurulur (birkaç dakika daha sürebilir).

Kontrol etmek için terminalde:
```bash
dig +short idiqutgames.com A
```
`185.199.10x.153` adreslerini görüyorsan tamamdır.

---

## Dosyalar

| Dosya | Ne işe yarar |
|---|---|
| `index.html` | Sitenin tamamı (HTML + CSS + JS tek dosyada) |
| `assets/` | Logo görselleri — aşağıya bak |
| `CNAME` | GitHub Pages'e özel domain'i söyler — **silme** |
| `.nojekyll` | GitHub'ın dosyaları olduğu gibi yayınlamasını sağlar — **silme** |
| `app-ads.txt` | **AdMob için zorunlu.** Google bunu `idiqutgames.com/app-ads.txt` adresinde arar |
| `robots.txt` | Arama motorlarına izin verir |
| `sitemap.xml` | Google indexleme için |

### assets/ — logo dosyaları

Orijinal logolardan (`~/Downloads/şirket için/logo/`) üretildi. Siyah zemin
şeffaflaştırıldı, palet-PNG ile sıkıştırıldı.

| Dosya | Nerede kullanılıyor | Boyut |
|---|---|---|
| `mark-arc-left.png` `mark-stroke.png` `mark-sun.png` `mark-arc-right.png` | Hero'daki **fırça çizilme animasyonu** — logo dört darbeye ayrıldı, her biri sırayla çiziliyor | 43 KB |
| `logo-mark.png` | Header, oyun kartı, footer, arka plan filigranı | 53 KB |
| `wordmark.png` | Hero ve header yazısı (beyaz, kırmızı Q çizgisi korundu) | 6 KB |
| `logo-lockup.png` | Basın kullanımı için tam kilit — sayfada kullanılmıyor | 96 KB |
| `og-image.png` | WhatsApp/X/Facebook link önizlemesi (1200×630) | 111 KB |
| `icon-512.png` `apple-touch-icon.png` `favicon-32.png` | Tarayıcı sekmesi ve telefon ana ekranı | — |

Sayfanın yüklediği toplam görsel: **~59 KB**.

**Marka renkleri:** kırmızı `#F41420` · mavi `#2A63FF` · zemin `#08080A`

## Siteyi güncelleme

`index.html`'i düzenle, sonra:

```bash
cd ~/idiqutgames-website
git add -A && git commit -m "site güncellendi" && git push
```

Push'tan ~1 dakika sonra canlıda görünür.

## Yayına girince yapılacaklar

- [x] İletişim adresi: `idiqutgames@gmail.com` (sitede yayında)
- [ ] `idiqutgames.com/app-ads.txt` açılıyor mu tarayıcıdan kontrol et
- [ ] AdMob → Apps → App settings → **Developer website** alanına `idiqutgames.com` yaz
- [ ] Google Search Console'a siteyi ekle

## Oyun çıkınca eklenecekler

- Oyunlar bölümü (ekran görüntüleri + App Store / Google Play butonları)
- `privacy.html` — Gizlilik Politikası (App Store & Google Play için **zorunlu**)
- `terms.html` — Kullanım Şartları
- `support.html` — Destek sayfası (App Store'un istediği Support URL)
