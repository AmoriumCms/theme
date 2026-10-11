# Amorium

October CMS 4 için Amorium teması.

Gereksinim: Kurulu bir October CMS 4 sitesi (PHP 8.2+, MySQL InnoDB).

Tema şu eklentilerle çalışır, her biri ayrı bir depodadır:
`Amorium.Pages`, `Amorium.Sections`, `Amorium.Post`, `Amorium.Navigation`, `Amorium.Form`, `Amorium.Business`, `Amorium.Demo`, `Amorium.Translate`.

## Kurulum

Kurulum videosu: [youtube.com/watch?v=gORhqjjb7X0](https://www.youtube.com/watch?v=gORhqjjb7X0)

1. `.env` dosyasında `DB_URL` sonuna `?engine=InnoDB` ekleyin.

2. Temayı ve eklentileri kurun. October Marketplace'ten veya doğrudan bu depolardan:

   ```bash
   php artisan plugin:install Amorium.Pages --from=https://github.com/amorium-october/pages.git
   php artisan plugin:install Amorium.Sections --from=https://github.com/amorium-october/sections.git
   php artisan plugin:install Amorium.Post --from=https://github.com/amorium-october/post.git
   php artisan plugin:install Amorium.Navigation --from=https://github.com/amorium-october/navigation.git
   php artisan plugin:install Amorium.Form --from=https://github.com/amorium-october/form.git
   php artisan plugin:install Amorium.Business --from=https://github.com/amorium-october/business.git
   php artisan plugin:install Amorium.Demo --from=https://github.com/amorium-october/demo.git
   php artisan plugin:install Amorium.Translate --from=https://github.com/amorium-october/translate.git
   php artisan theme:install Amorium.Amorium --from=https://github.com/amorium-october/theme.git
   ```

3. Kök dizinde sırasıyla çalıştırın:

   ```bash
   php artisan october:migrate
   php artisan tailor:migrate
   php artisan theme:use amorium-amorium
   ```

   Marketplace ve `theme:install` temayı `themes/amorium-amorium` klasörüne kurar. Zip paketinden kopyaladıysanız klasör adı `amorium` olur.

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

Bu repo elle düzenlenmez. Geliştirme projesindeki `themes/amorium/scripts/package.ps1` betiği temayı ve eklentileri ayrı depolara yazar, commit eder ve sürüm etiketlerini ekler.

Tema CSS dosyası derlenmiş olarak gelir. Tasarımı değiştirmek için tema klasöründe `npm install` ve `npm run build` çalıştırın.
