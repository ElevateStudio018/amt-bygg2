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

Sidan har vit bas. De blå och guldfärgade sveps som återkommer ligger i `assets/brand/swoosh.svg` (fristående svep, klassen `has-swoosh` på en sektion, med `has-swoosh--r`/`--l` för placering) och `assets/brand/swoosh-edge.svg` (vit våg med svep i nederkant av bildheros och helbredda bilder). Startsidans hero ritar sina svep direkt i HTML så att de kan animeras in.

Loggans A går igen i hela sidan (sist i `assets/css/main.css`, "Loggan genom hela sidan"): knapparnas högerkant lutar som A:ets ben (bredd = 0,43 × höjd), sektionsnummer och etiketter har guldfotens trapetsform, listpunkterna är små blå A-ben, linjen `rule-gold` är A:et uppdelat (`assets/brand/rule.svg`) och bilderna i `intro__media`, `page-hero__aside` och `job__media` ramas in som A:et – fotot är högra benet, med blått ben och guldfot. Sidfoten och mobilmenyn har A-märket som vattenstämpel. Bakom hela sidan ligger dessutom ett stort A (`.brand-a`, sätts in av `src/build.py`) som byggs upp medan man scrollar – blått ben, marint ben, guldfot – och är komplett strax före sidfoten. Sektionerna har därför genomskinlig bakgrund.

Startsidans hero är bilden `hero-goteborg` (från ElevateStudio018/amt-bygg).

Bilderna `goteborg-*` och `bygg-arbetsplats` kommer från Unsplash (fri att använda kommersiellt, ingen attribuering krävs):

| Fil | Fotograf |
| --- | --- |
| `goteborg-kranar`, `goteborg-hamn` | Dmitrii E. |
| `goteborg-eriksberg` | Jeet Datta |
| `bygg-arbetsplats` | Glenov Brankovic |
