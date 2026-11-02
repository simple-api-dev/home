# simpleapi.dev home page

Source of the simpleapi.dev home page. Bug reports and feedback for all SimpleAPI services go in [Issues](https://github.com/simple-api-dev/home/issues).

Static page for https://simpleapi.dev and https://www.simpleapi.dev. One HTML file with inline CSS and JS, no build step, plus the shared icons.

- `index.html` is the whole page. The hero form calls `keys.simpleapi.dev/api/keys/request` then `/verify` to hand out a first Todos key.
- `favicon.ico`, `icon-*.png` and `og-image.png` are the shared SimpleAPI brand assets.
- `nginx/simpleapi.dev` is the vhost as deployed on the production server (`/etc/nginx/sites-available/simpleapi.dev`).

## Deploying

The page is served from `/var/www/simpleapi/home/public/` on the production server. Copy `index.html`, `404.html` and the icon files there.

```
scp index.html 404.html favicon.ico icon-*.png og-image.png <user>@<server>:/tmp/
ssh <user>@<server> 'cd /tmp && sudo install -o root -g www-data -m 644 index.html 404.html favicon.ico icon-*.png og-image.png /var/www/simpleapi/home/public/'
```

The certificate is the certbot cert named `simpleapi.dev` (covers `simpleapi.dev` and `www.simpleapi.dev`) and renews automatically.

## Uptime check

`.github/workflows/uptime.yml` checks every site and API from GitHub every 15 minutes. A failed run emails the owner through GitHub's notifications for failed workflows. The production server also checks itself every 5 minutes and emails the owner, but only this check notices when the whole server is down. GitHub turns off scheduled workflows in a public repository after 60 days without commits and emails a warning first; re-enable it under Actions.

## License

[MIT](LICENSE)
