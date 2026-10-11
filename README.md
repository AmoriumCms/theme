# Amorium

October CMS 4 için Amorium teması ve eklentileri.

Gereksinim: Kurulu bir October CMS 4 sitesi (PHP 8.2+, MySQL InnoDB).

## Kurulum

Kurulum videosu: [youtube.com/watch?v=gORhqjjb7X0](https://www.youtube.com/watch?v=gORhqjjb7X0)

1. Repoyu indirin ve `themes` ile `plugins` klasörlerini October kök dizinine kopyalayın.

   ```bash
   git clone https://github.com/tulparstudyo/amorium-theme.git
   cp -r amorium-theme/themes amorium-theme/plugins /october/kok/dizini/
   ```

   - `themes/amorium` (demo içerik `demo` klasöründedir)
   - `plugins/amorium` (business, demo, form, navigation, pages, post, sections, translate)

2. `.env.example` içindeki değerleri sitenin `.env` dosyasına aktarın:
   - `DB_URL` sonuna `?engine=InnoDB` eklenmeli.
   - Otomatik çeviri için `TRANSLATE_ENABLED=true` ve `TRANSLATE_API_KEY` doldurulmalı.

3. Kök dizinde sırasıyla çalıştırın:

   ```bash
   php artisan october:migrate
   php artisan tailor:migrate
   php artisan theme:use amorium
   ```

4. Demo içeriği yükleyin. Panelde **Ayarlar > CMS > Demo İçerik > Demo İçeriği Yükle** veya komut satırından:

   ```bash
   php artisan amorium:demo-install
   ```

   Diller, sayfalar, yazılar, kategoriler, menüler, section'lar, işletme bilgileri, tema ayarları ve medya dosyaları birlikte yüklenir. Bu işlem sitedeki mevcut içeriğin yerine geçer.

5. Sonradan yeni bir dil (site) eklediğinizde şu komutu çalıştırın:

   ```bash
   php artisan tailor:propagate
   ```

## Güncelleme

Repodaki yeni sürümü çekip `themes/amorium` ve `plugins/amorium` klasörlerini sitedekilerin üzerine kopyalayın, ardından:

```bash
php artisan october:migrate
php artisan tailor:migrate
```

Sürümler `vX.Y.Z` etiketleriyle işaretlenir.

## Geliştirme

Bu repo elle düzenlenmez. Geliştirme projesindeki `themes/amorium/scripts/package.ps1` betiği paketi oluşturur, bu klasörü günceller, commit eder ve sürüm etiketini ekler.

Tema CSS dosyası derlenmiş olarak gelir. Tasarımı değiştirmek için `themes/amorium` klasöründe `npm install` ve `npm run build` çalıştırın.
