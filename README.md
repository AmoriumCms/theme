# Amorium

October CMS 4 için Amorium teması.

Gereksinim: Kurulu bir October CMS 4 sitesi (PHP 8.2+, MySQL InnoDB).

Tema `AmoriumCms.Amorium` eklentisiyle çalışır. Sayfalar, section'lar, yazılar, menüler, formlar, işletme bilgileri, demo içerik ve otomatik çeviri bu tek eklentidedir.

## Kurulum

Kurulum videosu: [youtube.com/watch?v=gORhqjjb7X0](https://www.youtube.com/watch?v=gORhqjjb7X0)

1. `.env` dosyasında `DB_URL` sonuna `?engine=InnoDB` ekleyin.

2. Temayı ve eklentiyi kurun. October Marketplace'ten veya doğrudan bu depolardan:

   ```bash
   php artisan plugin:install AmoriumCms.Amorium --from=https://github.com/AmoriumCms/plugin.git
   php artisan theme:install AmoriumCms.Amorium --from=https://github.com/AmoriumCms/theme.git
   ```

3. Kök dizinde sırasıyla çalıştırın:

   ```bash
   php artisan october:migrate
   php artisan tailor:migrate
   php artisan theme:use amoriumcms-amorium
   ```

   Marketplace ve `theme:install` temayı `themes/amoriumcms-amorium` klasörüne kurar. Zip paketinden kopyaladıysanız klasör adı `amorium` olur.

4. Demo içeriği yükleyin. Panelde **Ayarlar > CMS > Demo İçerik > Demo İçeriği Yükle** veya komut satırından:

   ```bash
   php artisan amorium:demo-install
   ```

   Diller, sayfalar, yazılar, kategoriler, menüler, section'lar, işletme bilgileri, tema ayarları ve medya dosyaları birlikte yüklenir. Bu işlem sitedeki mevcut içeriğin yerine geçer.

5. Sonradan yeni bir dil (site) eklediğinizde şu komutu çalıştırın:

   ```bash
   php artisan tailor:propagate
   ```

## Otomatik çeviri

`.env` dosyasına ekleyin:

```env
TRANSLATE_ENABLED=true
TRANSLATE_MODEL="gemini-flash-latest"
TRANSLATE_API_KEY=
```

## Güncelleme

```bash
php artisan october:update
php artisan tailor:migrate
```

Sürümler `vX.Y.Z` etiketleriyle işaretlenir.

## Geliştirme

Bu repo elle düzenlenmez. Geliştirme projesindeki `themes/amorium/scripts/package.ps1` betiği temayı ve eklentiyi ayrı depolara yazar, commit eder ve sürüm etiketlerini ekler.

Tema CSS dosyası derlenmiş olarak gelir. Tasarımı değiştirmek için tema klasöründe `npm install` ve `npm run build` çalıştırın.
