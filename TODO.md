# TODO — Elektromontag weboldal

## Deploy (élesítés)
- [x] VPS-re deploy — Docker konténer fut: http://72.61.95.59:8080
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

## Frissítés (ha változik az oldal)
```bash
# Lokálisan: buildelés és push
npm run build && git add -A && git commit -m "Update site" && git push

# VPS-en: Hostinger hPanel → Docker → elektromontag → Redeploy
# Vagy a Hostinger API-n keresztül újradeployolható
```
