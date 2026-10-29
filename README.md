# simpleapi.dev home page

Static welcome page for https://simpleapi.dev and https://www.simpleapi.dev. One file, no build step.

- `index.html` is the whole page (inline CSS and JS). The hero form calls `keys.simpleapi.dev/api/keys/request` then `/verify` to hand out a first Todos key.
- `nginx/simpleapi.dev` is the vhost as deployed on the production server (`/etc/nginx/sites-available/simpleapi.dev`).

## Deploy

The page is served from `/var/www/simpleapi/home/public/index.html` on the production server.

```
scp index.html <user>@<server>:/tmp/simpleapi-home-index.html
ssh <user>@<server> 'sudo install -o root -g www-data -m 644 /tmp/simpleapi-home-index.html /var/www/simpleapi/home/public/index.html'
```

The certificate is the certbot cert named `simpleapi.dev` (covers `simpleapi.dev` and `www.simpleapi.dev`) and renews automatically.
