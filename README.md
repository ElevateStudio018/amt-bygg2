# AMT Bygg – webbplats

Statisk webbplats för AMT Bygg (amtgroup.se). Ingen server eller databas krävs – alla filer kan laddas upp till valfritt webbhotell (Netlify, Vercel, GitHub Pages, Loopia, One.com m.fl.).

## Bygga

```bash
python3 src/build.py           # skriver sidorna till repots rot
python3 -m http.server 8000    # förhandsvisa på http://localhost:8000
```

Kräver Python 3 med Pillow (för bildmått). `python3 src/patterns.py` genererar om mönsterbiblioteket.

## Struktur

| Sökväg | Innehåll |
| --- | --- |
| `src/pages/*.html` | Sidornas innehåll (redigera här, inte i de byggda filerna) |
| `src/build.py` | Sidmall, meny, sidfot, klienter, partners, ramavtal och kontaktuppgifter |
| `src/patterns.py` | Materialmönster i loggans färger: träådring, fiskben, regelverk, tegel, snitt, rutnät |
| `assets/` | CSS, JS, typsnitt (lokalt hostade), bilder, logotyper, vCard |

Klienter, partners och försäkringsbolag läggs till i listorna `CLIENTS`, `PARTNERS` och `INSURERS` i `src/build.py` (logotyp i `assets/logos/<id>.png`).

## Formulär

Formulären öppnar idag ett förifyllt mejl till amtbygg@amtgroup.se. För att skicka direkt från sidan, sätt `FORM_ENDPOINT_CONTACT` och `FORM_ENDPOINT_DAMAGE` i `src/build.py` till t.ex. en Formspree-URL och bygg om.

## Omdirigering

Gamla adressen `/skadereparation` pekar vidare till `/anmal-skada/`.

## Typsnitt, svep och bilder

Loggan är egenritad och finns inte som typsnitt. All text sätts därför i Lexend (SIL Open Font License), som har samma geometriska, jämntjocka form som loggans bokstäver – runda G med tvärslå, raka Y och T. Typsnittet ligger lokalt i `assets/fonts/`.

Sidan har vit bas. De blå och guldfärgade sveps som återkommer ligger i `assets/brand/swoosh.svg` (kontaktbandet, klassen `has-swoosh`) och `assets/brand/swoosh-edge.svg` (vit våg med svep, används i dag inte). Startsidans hero ritar sina svep direkt i HTML så att de kan animeras in.

Formspråket är en koncernprofil (sist i `assets/css/main.css`, "Koncernprofil"): raka kanter utan skuggor, tunna linjer mellan sektioner, ett nyckeltalsband under startsidans hero, en Aktuellt-del på startsidan och breda bildbanderoller överst på undersidorna. Aktuellt-delen bygger bara på fakta som redan finns på sajten; byt ut eller lägg till nyheter i `src/pages/index.html`. Sektionsnummer skrivs som text och listpunkterna är små fyrkanter. De blå och gula svepen finns kvar i startsidans hero och i kontaktbandet längst ner på varje sida.

Startsidans hero är bilden `hero-goteborg` (från ElevateStudio018/amt-bygg).

Bilderna `goteborg-*` och `bygg-arbetsplats` kommer från Unsplash (fri att använda kommersiellt, ingen attribuering krävs):

| Fil | Fotograf |
| --- | --- |
| `goteborg-kranar`, `goteborg-hamn` | Dmitrii E. |
| `goteborg-eriksberg` | Jeet Datta |
| `bygg-arbetsplats` | Glenov Brankovic |
