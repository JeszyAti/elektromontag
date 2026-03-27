# TODO — Elektromontag weboldal

## Kész
- [x] PRD dokumentum
- [x] Astro + Tailwind CSS projekt felépítés
- [x] Sötét téma (antracit + narancs)
- [x] V2 logó (kör + villám + szikrák)
- [x] Összes szekció: Hero, Szolgáltatások, Rólunk, Vélemények, Kapcsolat, Footer
- [x] Scroll reveal animációk
- [x] SEO: JSON-LD, meta tagek, kulcsszó kutatás
- [x] Reszponzív mobil nézet + hamburger menü
- [x] Tegező hangnem
- [x] Git repo + GitHub: github.com/JeszyAti/elektromontag
- [x] VPS deploy Docker konténerrel: http://72.61.95.59:8080

## Deploy — domain beállítás után
- [ ] Domain regisztráció — `elektromontag.hu`
- [ ] DNS A rekord beállítás → `72.61.95.59`
- [ ] NPM proxy host — `elektromontag.hu` → `127.0.0.1:8080` + Let's Encrypt SSL
- [ ] Docker-compose port visszaállítás `127.0.0.1:8080`-ra (NPM beállítás után)
- [ ] Tűzfal: 8080 és 81 port bezárása (NPM beállítás után)

## Kiegészítések
- [ ] Google Analytics 4 — látogatottság mérés, `tel:` link kattintás tracking
- [ ] Open Graph kép — szép előnézet Facebook/Messenger megosztáshoz
- [ ] Valódi műhely fotó — `public/images/muhely.jpg` helyre másolni
- [ ] Google Maps embed pontosítás — Google Business Place ID-vel
- [ ] Google Business Profile frissítése weboldalcímmel
- [ ] Sitemap.xml generálás (Astro plugin)
- [ ] Aloldalak fő szolgáltatásokhoz (v2: /onindito-javitas, /klimafeltoltes, stb.)

## Frissítés (ha változik az oldal)
```bash
# 1. Lokálisan: buildelés és push
npm run build && git add -A && git commit -m "Update site" && git push

# 2. VPS-en: Hostinger terminálban volume cleanup
docker stop elektromontag-web; docker rm elektromontag-web elektromontag-deploy; docker volume rm elektromontag_site-data elektromontag_nginx-conf

# 3. Redeploy: Hostinger hPanel → Docker → elektromontag → vagy API-n keresztül
```
