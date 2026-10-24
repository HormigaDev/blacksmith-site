# BBEL Blacksmith presentation site

The public, multilingual presentation site for Blacksmith. It introduces the project, its
bare-metal deployment scope, architecture, and security model in English, Spanish, and
Portuguese.

The site is built with Astro and generated as static HTML, so production hosting only needs a
web server such as Nginx.

## Routes

- English: `/`
- Español: `/es/`
- Português: `/pt/`

## Local development

```sh
pnpm install
pnpm dev
```

Build the static site with:

```sh
pnpm build
```

The generated files are written to `dist/`. The `.astro/` directory is Astro's local generated
cache and must not be committed.

## Nginx deployment

Copy the contents of `dist/` to the directory served by Nginx:

```nginx
server {
    listen 443 ssl http2;
    server_name blacksmith.example.com;

    root /var/www/blacksmith-site;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Before publishing, replace `blacksmith.example.com` with the final domain in the Nginx
configuration, `astro.config.mjs`, `public/robots.txt`, and `public/sitemap.xml`.

The site links to the main project at
https://github.com/HormigaDev/blacksmith and includes the Blacksmith forge logo and the
HormigaDev GitHub profile image in `public/assets/`.

## License

This site is released under the [MIT License](./LICENSE).
