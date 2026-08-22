# idiqutgames.com

İdiqut Games kurumsal web sitesi. Tek sayfa, statik, hiçbir dış bağımlılığı yok
(font/script/CDN çağrısı yapmaz — çok hızlı açılır, çerez kullanmaz).

**Tasarım:** baştan sona bej (`#FAF3ED` — logonun kendi zemini), ustwo Games
düzeninde minimal: bölümler arasında çerçeve/ayraç yok, ayrımı sadece boşluk
yapıyor. Oyun görseli kolonun tamamını kaplıyor.


**Hosting:** GitHub Pages · **Repo:** `sadam7846466-gif/idiqutgames-website` · **Branch:** `main`

---

## ✅ Domain ayarı — tamamlandı

`idiqutgames.com` GitHub Pages'e bağlı ve SSL çalışıyor. `www` de ana adrese
yönleniyor. Kayıtlar referans olarak dursun:

| Type  | Name | Value                        |
|-------|------|------------------------------|
| A     | @    | `185.199.108.153`            |
| A     | @    | `185.199.109.153`            |
| A     | @    | `185.199.110.153`            |
| A     | @    | `185.199.111.153`            |
| CNAME | www  | `sadam7846466-gif.github.io` |

Kontrol: `dig +short idiqutgames.com A`

---

## Dosyalar

| Dosya | Ne işe yarar |
|---|---|
| `index.html` | Ana sayfa (HTML + CSS + JS tek dosyada) |
| `privacy.html` | Gizlilik Politikası — **mağaza başvurusu için zorunlu** |
| `terms.html` | Kullanım Şartları / EULA |
| `support.html` | Destek sayfası — App Store'un istediği Support URL |
| `assets/legal.css` | Üç yasal sayfanın ortak stili (ana sayfanın tasarım dili) |
| `assets/` | Logo ve oyun görselleri — aşağıya bak |
| `CNAME` | GitHub Pages'e özel domain'i söyler — **silme** |
| `.nojekyll` | GitHub'ın dosyaları olduğu gibi yayınlamasını sağlar — **silme** |
| `app-ads.txt` | **AdMob için zorunlu.** Google bunu `idiqutgames.com/app-ads.txt` adresinde arar |
| `robots.txt` | Arama motorlarına izin verir |
| `sitemap.xml` | Google indexleme için |

### assets/ — logo dosyaları

Kaynak: `~/Downloads/şirket için/logo-v3/a.png` (1254×1254, krem zeminli).
Krem zemin şeffaflaştırıldı; her piksel **en yakın referans renge** atanarak
katmanlara bölündü (eşik kuralları kenar piksellerini kaybediyordu).

| Dosya | Nerede kullanılıyor | Boyut |
|---|---|---|
| `v3-art-circle.png` | Hero — mavi fırça dairesi, dönerek gelir | 83 KB |
| `v3-art-figure.png` | Hero — figür + mızrak + tech dokusu, aşağıdan yükselir | 31 KB |
| `v3-art-banner.png` | Hero — kızıl sancak, soldan sağa açılır | 91 KB |
| `v3-wordmark.png` | Hero, header ve footer yazısı | 12 KB |
| `game-hamster.jpg` | Games — Hamster Maze konsept görseli | 196 KB |
| `logo-full.png` | Basın kullanımı için tam logo | 83 KB |
| `og-image.png` | Link önizlemesi (1200×630) | 104 KB |
| `icon-512.png` `apple-touch-icon.png` `favicon-32.png` | Sekme ve ana ekran ikonu | — |

**Marka renkleri:** zemin `#FAF3ED` · kızıl `#A01810` · lacivert `#183048` · siyah `#14141C`

**Açılış animasyonu:** daire dönerek gelir → figür aşağıdan yükselir →
sancak soldan sağa açılır → yazı belirir. Toplam ~2.3 sn.


## Siteyi güncelleme

İlgili `.html` dosyasını düzenle, sonra:

```bash
cd ~/idiqutgames-website
git add -A && git commit -m "site güncellendi" && git push
```

Push'tan ~1 dakika sonra canlıda görünür.

## Yasal sayfalar

`privacy.html`, `terms.html` ve `support.html` 22 Ağustos 2026'da eklendi.
Üçü de ana sayfanın tasarım dilini paylaşıyor (`assets/legal.css`), dış
bağımlılığı yok, mobilde tablolar kendi kutusunda yana kayıyor.

**Neye göre yazıldılar.** Metinler şu varsayımlarla hazırlandı — oyunun
gerçeği bunlardan farklıysa metni de değiştir:

- Oyunda **Google AdMob reklamı** var
- **Google Analytics for Firebase** + **Crashlytics** var
- Motor **Unity**
- **Uygulama içi satın alma** var, ödeme Apple/Google üzerinden
- Hesap sistemi, giriş, sohbet, bulut kayıt **yok** — ilerleme sadece cihazda
- Hedef kitle genel; 13 yaş altı için koruyucu maddeler yazıldı (kişiselleştirilmemiş reklam, COPPA)

### Yetkili mahkeme

`terms.html` → **15. Governing law**: İstanbul mahkemeleri ve icra daireleri
yetkili. Şirket başka bir ile taşınırsa oradaki tek cümleyi güncellemek yeterli.

### Mağaza başvurusunda bu adresler istenecek

| Nerede | Alan | Yazılacak adres |
|---|---|---|
| App Store Connect | Privacy Policy URL | `https://idiqutgames.com/privacy.html` |
| App Store Connect | Support URL | `https://idiqutgames.com/support.html` |
| App Store Connect | EULA (özel sözleşme) | `https://idiqutgames.com/terms.html` |
| Play Console | Gizlilik politikası | `https://idiqutgames.com/privacy.html` |
| Play Console | Veri silme talebi URL'i | `https://idiqutgames.com/support.html#data-deletion` |
| Play Console | Destek e-postası | `idiqutgames@gmail.com` |

Sürüm tarihi üç sayfanın da başında (`Effective` / `Last updated`). Metni
değiştirdiğinde `Last updated` tarihini de güncelle.

## Yayına girince yapılacaklar

- [x] İletişim adresi: `idiqutgames@gmail.com` (sitede yayında)
- [x] Domain + SSL çalışıyor
- [x] `idiqutgames.com/app-ads.txt` açılıyor (HTTP 200)
- [x] Gizlilik, Şartlar ve Destek sayfaları yayında
- [ ] AdMob → Apps → App settings → **Developer website** alanına `idiqutgames.com` yaz
- [ ] Google Search Console'a siteyi ekle ve `sitemap.xml`'i gönder

## Hamster Maze çıkınca

- `game-hamster.jpg` yerine **gerçek ekran görüntüsü** koy (şu anki konsept görseli)
- Google Play / App Store butonları ekle
- Oyunun kendi sayfası (`hamster-maze.html`) — ustwo'daki "More →" gibi
- `support.html` içindeki SSS'yi oyuncudan gelen gerçek sorulara göre güncelle

## Oyun çıkınca yapılacaklar

`index.html` içinde her projenin altında hazır duruyor:

```html
<div class="stores">
  <span class="store">Google Play<span class="soon">Soon</span></span>
  <span class="store">App Store<span class="soon">Soon</span></span>
</div>
```

Çıkınca `<span class="store">` → `<a class="store" href="MAGAZA_LINKI">` yap ve
içindeki `<span class="soon">Soon</span>` satırını sil. Ayrıca `Release`
künyesini `Not announced` yerine tarihe çevir.

İkinci proje için ayrılmış yer: `.slot` bloğu. Görsel gelince `.slot`'u
`.frame` + `<img>` ile değiştir, başlığı ve sloganı yaz.
