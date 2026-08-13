# tclouds.hu — T-Cloud Solutions Kft.

Statikus, kétnyelvű (HU/EN) bemutatkozó oldal. **Nincs build, nincs függőség,
nincs futtatókörnyezet** — három fájl és egy stíluslap.

## Fájlok

```
index.html        magyar oldal
en/index.html     angol oldal
assets/style.css  közös stíluslap (mindkét oldal ezt használja)
assets/t-cloud.png  logó (forrás: tdhr-web/public/logos/)
CNAME             GitHub Pages egyedi domain: tclouds.hu
robots.txt        + sitemap.xml   kereső-alapok, induláskor
.nojekyll         a GitHub Pages ne futtasson Jekyllt
```

## Helyi megtekintés

```sh
python3 -m http.server 8899
# → http://localhost:8899/
```

## Élesítés (GitHub Pages, ingyenes)

```sh
gh repo create tclouds-web --public --source=. --push
gh api -X POST repos/:owner/tclouds-web/pages -f 'source[branch]=main' -f 'source[path]=/'
```

Utána a DNS-ben (Cloudflare) a `tclouds.hu`-ra:

```
A     tclouds.hu   185.199.108.153
A     tclouds.hu   185.199.109.153
A     tclouds.hu   185.199.110.153
A     tclouds.hu   185.199.111.153
CNAME www          <felhasznalonev>.github.io
```

A `CNAME` fájl már a repóban van, a HTTPS-t a GitHub automatikusan kiállítja.

## Szerkesztés

A tartalom közvetlenül a HTML-ben van, i18n-réteg nélkül. **Ha magyarul
módosítasz valamit, az `en/index.html`-ben is át kell vezetni** — szándékos
csere: két külön URL kell a helyes `hreflang`-hoz és az indexeléshez, cserébe a
szöveg két helyen él.

## Ellenőrzött cégadatok

Forrás: `tdhr-web` (`src/lib/constants.ts`,
`src/app/[lang]/adatkezelesi-tajekoztato/page.tsx`) — nem emlékezetből.

| | |
|---|---|
| Székhely | 1117 Budapest, Dombóvári út 9. 4. emelet |
| Cégjegyzékszám | 01-09-438601 |
| Adószám | 32710148-2-43 |

## Nyitott

- **`info@tclouds.hu` postafiók** — a cím ki van írva az oldalon és az
  impresszumban, de a fiók létezését nem ellenőriztem. Élesítés előtt tesztlevél.
- **Tárhelyszolgáltató** az impresszumban GitHub, Inc. — ha máshova kerül a
  hosting, mindkét nyelven át kell írni.
