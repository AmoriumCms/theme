# Amorium

Amorium theme for October CMS 4.

Requirement: An installed October CMS 4 site (PHP 8.2+, MySQL InnoDB).

The theme works with the [AmoriumCms.Amorium](https://github.com/AmoriumCms/plugin) plugin. Pages, sections, posts, menus, forms, business information, demo content and automatic translation are all in this single plugin.

## Installation

Installation video: [youtube.com/watch?v=gORhqjjb7X0](https://www.youtube.com/watch?v=gORhqjjb7X0)

1. Add `?engine=InnoDB` to the end of `DB_URL` in the `.env` file.

2. Install the theme and the plugin from the admin panel:

   1. Go to **Settings > Software Updates > Manage Plugins > Edit Composer**, add the plugin to the `require` section and save:

      ```json
      "amoriumcms/amorium-plugin": "^1.0.5"
      ```

   2. Find **Amorium** in the Marketplace and click **Install**. In the installation window choose **Install with Composer**. **Make a Copy** does not run Composer, so the plugin is not installed.
   3. Under **Theme Dependencies**, clear the **AmoriumCms.Amorium** checkbox, because Composer installs it. Keep **RainLab.User** and **Seed Theme Data** selected.

   The plugin, the database tables and the Tailor content tables are created during the installation, no command is needed. Then activate the theme in **Settings > Front-end Theme**.

3. Or install from the command line, directly from these repositories, and run these commands in the root directory, in order:

   ```bash
   php artisan plugin:install AmoriumCms.Amorium --from=https://github.com/AmoriumCms/plugin.git
   php artisan theme:install AmoriumCms.Amorium --from=https://github.com/AmoriumCms/theme.git
   php artisan october:migrate
   php artisan tailor:migrate
   php artisan theme:use amoriumcms-amorium
   ```

   The Marketplace and `theme:install` install the theme in the `themes/amoriumcms-amorium` folder. If you copied it from the zip package, the folder name is `amorium`.

4. Install the demo content. In the admin panel go to **Settings > CMS > Demo Content > Install Demo Content**, or run:

   ```bash
   php artisan amorium:demo-install
   ```

   Languages, pages, posts, categories, menus, sections, business information, theme settings and media files are installed together. This replaces the existing content of the site.

5. Whenever you add a new language (site) later, run:

   ```bash
   php artisan tailor:propagate
   ```

## Automatic Translation

Add to the `.env` file:

```env
TRANSLATE_ENABLED=true
TRANSLATE_MODEL="gemini-flash-latest"
TRANSLATE_API_KEY=
```

## Updating

```bash
php artisan october:update
php artisan tailor:migrate
```

Releases are marked with `vX.Y.Z` tags.

## Development

This repository is not edited by hand. The `themes/amorium/scripts/package.ps1` script in the development project writes the theme and the plugin to separate repositories, commits them and adds the version tags.

The theme CSS file ships compiled. To change the design, run `npm install` and `npm run build` in the theme folder.
