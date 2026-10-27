[README.md](https://github.com/user-attachments/files/34006300/README.md)
# Localizare magazine Lidl

Pagină web pentru căutarea rapidă a magazinelor Lidl după numărul magazinului: afișează denumirea, adresa, orașul, județul și codul poștal, centrează harta pe locație și oferă butoane de deschidere în Google Maps și de navigare.

Conține 238 de magazine, datele sunt incluse direct în `index.html` (nu există dependențe de server sau baze de date).

## Publicare pe GitHub Pages

1. Creează un repository nou (de exemplu `magazine-lidl`).
2. Încarcă `index.html` în rădăcina repository-ului.
3. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`, apoi **Save**.
4. După 1-2 minute pagina e disponibilă la:
   `https://<utilizator>.github.io/<repository>/`

## Atenție la confidențialitate

GitHub Pages pe un repository **public** înseamnă că adresele celor 238 de magazine sunt accesibile oricui are linkul, fără autentificare. Pentru acces restrâns e nevoie de un repository privat cu GitHub Pages, disponibil doar în planurile plătite (Pro / Team / Enterprise).

## Actualizarea listei de magazine

Datele sunt în `index.html`, în blocul `var MAGAZINE = { ... }`, câte un rând per magazin:

```javascript
"260":{"n": "Constanta/ Industriei Mici", "o": "Constanta", "j": "Constanta", "a": "Str. Industriei Mici, nr. 1", "c": "900161"},
```

unde `n` = denumire, `o` = oraș, `j` = județ / sector, `a` = adresă, `c` = cod poștal.

## Setări

În josul fișierului, la începutul blocului `<script>`:

| Setare | Implicit | Ce face |
|---|---|---|
| `ZOOM` | `17` | Nivelul de zoom la găsirea magazinului |
| `PREFIX` | `"Lidl"` | Cuvânt adăugat în căutarea pe hartă, ca pinul să cadă pe magazin, nu pe stradă |

## Funcționare

- **Google Maps** — hartă încorporată prin iframe, fără cheie API.
- **OpenStreetMap** — alternativă cu Leaflet (încărcat din cdnjs) și geocodare prin Nominatim.
- **Butoanele albastre** — deschid locația, respectiv ruta, în Google Maps, într-un tab nou.

Pentru magazinele fără adresă în listă, pagina afișează un avertisment și caută după denumire, oraș și județ.
