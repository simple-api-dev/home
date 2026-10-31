Source of the simpleapi.dev home page. Bug reports and feedback for all SimpleAPI services go in Issues.

# simpleapi.dev home page

Static welcome page for https://simpleapi.dev and https://www.simpleapi.dev. One HTML file with inline CSS and JS, no build step, plus the shared icons.

- `index.html` is the whole page. The hero form calls `keys.simpleapi.dev/api/keys/request` then `/verify` to hand out a first Todos key.
- `favicon.ico`, `icon-*.png` and `og-image.png` are the shared SimpleAPI brand assets.
- `nginx/simpleapi.dev` is the vhost as deployed on the production server (`/etc/nginx/sites-available/simpleapi.dev`).

The hero form has a temporary "Access code" field for the private preview. To remove it, search `index.html` for `ACCESS-GATE`.

## Deploying

The page is served from `/var/www/simpleapi/home/public/` on the production server. Copy `index.html` and the icon files there.

```
scp index.html favicon.ico icon-*.png og-image.png <user>@<server>:/tmp/
ssh <user>@<server> 'cd /tmp && sudo install -o root -g www-data -m 644 index.html favicon.ico icon-*.png og-image.png /var/www/simpleapi/home/public/'
```

The certificate is the certbot cert named `simpleapi.dev` (covers `simpleapi.dev` and `www.simpleapi.dev`) and renews automatically.

## License

MIT, see `LICENSE`.
