# idiqutgames.com

İdiqut Games kurumsal web sitesi. Tek sayfa, statik, hiçbir dış bağımlılığı yok
(font/script/CDN çağrısı yapmaz — bu yüzden çok hızlı açılır ve GDPR sorunu çıkarmaz).

## Dosyalar

| Dosya | Ne işe yarar |
|---|---|
| `index.html` | Sitenin tamamı (HTML + CSS tek dosyada) |
| `app-ads.txt` | **AdMob için zorunlu.** Google bu dosyayı `idiqutgames.com/app-ads.txt` adresinde arar |
| `robots.txt` | Arama motorlarına izin verir |
| `sitemap.xml` | Google'ın siteyi indexlemesi için |

## Yayınlama — Netlify (en kolay yol)

1. https://app.netlify.com/drop adresine git
2. `idiqutgames-website` klasörünü sayfaya sürükle-bırak → site anında yayında
   (`rastgele-isim.netlify.app` gibi geçici bir adres verir)
3. Ücretsiz hesap aç (siteyi kalıcı hale getirmek için)
4. **Site configuration → Domain management → Add a domain** → `idiqutgames.com` yaz
5. Netlify sana DNS kayıtlarını gösterir. Domain'i aldığın firmanın (GoDaddy,
   Namecheap, Turhost vb.) DNS paneline gir ve şunları ekle:

   ```
   A      @      75.2.60.5
   CNAME  www    <senin-siten>.netlify.app
   ```

   (Netlify ekranında yazan değerleri kullan — yukarıdakiler örnek.)
6. DNS'in yayılması 10 dakika – 24 saat sürer. SSL sertifikası (https) otomatik gelir.

### Güncelleme
`index.html`'i düzenle → Netlify panelinde **Deploys** sekmesine klasörü tekrar
sürükle-bırak. Bitti.

## Alternatif — Cloudflare Pages
Ücretsiz ve daha hızlı, ama domain'in nameserver'larını Cloudflare'e taşıman
gerekir. Netlify ile başlamak daha kolay.

## Yayına alınca yapılacaklar

- [ ] `hello@idiqutgames.com` e-posta adresini oluştur (domain sağlayıcın üzerinden
      yönlendirme/forwarding en kolayı). Site bu adresi gösteriyor.
- [ ] `idiqutgames.com/app-ads.txt` adresinin açıldığını tarayıcıdan kontrol et
- [ ] AdMob → Apps → App settings → **Developer website** alanına `idiqutgames.com` yaz
      (app-ads.txt'in doğrulanması için gerekli)
- [ ] Google Search Console'a siteyi ekle

## Oyun çıkınca eklenecekler

- Oyunlar bölümü (ekran görüntüleri + App Store / Google Play butonları)
- `privacy.html` — Gizlilik Politikası (App Store & Google Play için **zorunlu**)
- `terms.html` — Kullanım Şartları
- `support.html` — Destek sayfası (App Store'un istediği Support URL)
