# kaluk.net

Persönliches Portfolio von Oguzhan Kaluk. Statische Seite, gebaut mit [Eleventy](https://www.11ty.dev/), gehostet auf GitHub Pages unter der Custom Domain **kaluk.net**.

## Prinzipien

- **Sicher:** Keine externen Ressourcen (kein CDN, keine Fonts, kein JS), strikte Content-Security-Policy per Meta-Tag.
- **Performant:** Reines statisches HTML + eine kleine CSS-Datei, Systemschriften, gesamte Seite < 50 KB.
- **Minimalistisch:** Typografiegetriebenes, helles Editorial-Design.
- **Zweisprachig:** Deutsch unter `/`, Englisch unter `/en/`, verknüpft per `hreflang`.

## Struktur

```
src/
  _includes/base.njk   # Basis-Layout (Header, Footer, Meta-Tags)
  css/style.css        # Gesamtes Styling
  index.njk            # Startseite (DE)
  en/index.njk         # Startseite (EN)
  404.njk              # Fehlerseite
  sitemap.njk          # sitemap.xml
  static/              # Wird 1:1 in die Site-Root kopiert (CNAME, robots.txt)
eleventy.config.js     # Eleventy-Konfiguration
.github/workflows/     # Build & Deploy zu GitHub Pages
```

## Entwicklung

```sh
npm install
npm run dev     # Dev-Server mit Live-Reload auf http://localhost:8080
npm run build   # Statischer Build nach _site/
```

## Deployment

Jeder Push auf `main` baut die Seite per GitHub Actions und deployed sie zu GitHub Pages
(Repo-Einstellung: *Settings → Pages → Source: GitHub Actions*).

## Domain (kaluk.net)

1. Beim DNS-Anbieter: `A`-Records für den Apex auf `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (optional `AAAA`: `2606:50c0:8000::153` … `8003::153`), `CNAME` für `www` auf `okaluk.github.io`.
2. Im Repo: *Settings → Pages → Custom domain: kaluk.net*, danach **Enforce HTTPS** aktivieren.
3. Empfohlen: Domain unter *GitHub-Account → Settings → Pages → Verified domains* verifizieren (schützt vor Domain-Takeover).
