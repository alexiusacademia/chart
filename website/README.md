# chart's website

The page for the chart library, live at https://chart-package.syncster.dev.

Author: Alexius Academia · Started 2026-10-25

A static page: no build step, no dependencies.

```
index.html              # the page; its gallery code is the code in ../examples/gallery.tsl
styles.css              # light and dark colours
assets/gallery/*.png    # the gallery pictures, saved by `tessel run examples`
assets/share.png        # the picture shown when a link to the site is shared
assets/app*.png         # copies of ../docs/app.png and ../docs/app-dark.png
assets/favicon.svg
netlify.toml            # no build; HTML isn't cached
```

## Changing it

After changing the library or a gallery chart, from the library's folder:

```bash
tessel run examples                      # remakes docs/*.png and website/assets/*
cp docs/app.png docs/app-dark.png website/assets/
python3 -m http.server 8080 -d website   # look at http://localhost:8080/
```

Keep each gallery card's code in `index.html` the same as its chart in
`examples/gallery.tsl` (the page shows `savePNG` where the file calls `save`).

## Publishing

Netlify project `chart-package`, team syncster.dev, custom domain
`chart-package.syncster.dev`. Nothing deploys by itself:

```bash
npx -y netlify-cli deploy --prod --dir website --site ad05151e-1bf5-4772-a0c3-df3dedd2baad
```
