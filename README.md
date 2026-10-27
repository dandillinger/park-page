# park-page

One static "PROJECT BEING REBUILT" page for domains I keep but don't run a site on.

- No contact info, no tracking, no external requests. A strict Content-Security-Policy allows only the page's own inline style and one hashed script.
- The script only shows the visiting domain's name. Without it, the page still reads correctly.
- `404.html` is a copy of `index.html`, so every path shows the same page.
- Served by GitHub Pages. GitHub Pages takes one custom domain per repo (`CNAME`); a second domain needs a copy of this repo or a multi-domain host (registry US-150).

## Domains parked here

- `phaseplan.tools` (registry US-150)

## Changing the script

The CSP pins the script by hash. After editing it, recompute:

```bash
printf '%s' '<script body>' | openssl dgst -sha256 -binary | base64
```

and update `script-src 'sha256-…'` in both `index.html` and `404.html`.
