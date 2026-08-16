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
| `index.html` | Sitenin tamamı (HTML + CSS tek dosyada) |
| `CNAME` | GitHub Pages'e özel domain'i söyler — **silme** |
| `app-ads.txt` | **AdMob için zorunlu.** Google bunu `idiqutgames.com/app-ads.txt` adresinde arar |
| `robots.txt` | Arama motorlarına izin verir |
| `sitemap.xml` | Google indexleme için |

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
