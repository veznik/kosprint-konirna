# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Co tento repozitář je

Veřejná **šablona** (MIT) pro pořadatele závodů v orientačním běhu KO sprint — interní instruktážní web pro tým „konírny" (startovní prostor s kojemi). Repo na GitHubu: `veznik/kosprint-konirna`. Live demo: https://kosprint-konirna.pages.dev/.

Šablona je odvozená z konkrétní akce **MČR KO sprint 2026 Třebíč**; archiv té konkrétní akce běží odděleně na `kosprint-konirna-2026.pages.dev` a tato verze obsahuje placeholdery místo jmen, dat a kontaktů.

**Zdroj pravdy** pro úpravy šablony žije v paralelní pracovní složce `/Users/romanveznik/Vibe/KOsprint/` (soubor `konirna.html` + vlastní `CLAUDE.md`). Tam se obvykle edituje jako první a sem se synchronizuje. Pokud se ale uživatel rozhodne editovat přímo zde, je `index.html` jediný zdrojový soubor.

## Struktura

- `index.html` — **jediný zdrojový soubor**. Vše inline (HTML, CSS, SVG schéma konírny, JS lightbox + JS print funkce). ~1900 řádků, žádný build step. Hlavní sekce (`<section id="...">`): `layout`, `fotky`, `procedura`, `harmonogram`, `material`, `zavodnik`, `lide`, `poznamky`, `tisk`, `vyzva`.
- `*.jpg` — 4 referenční fotky z 2026 (`konirna-zepredu.jpg`, `konirna-zezadu.jpg`, `desky-s-vyrezy-map.jpg`, `rulicky-map.jpg`). Reference, dají se nahradit vlastními.
- `README.md` — uživatelská dokumentace pro forking + customizaci.
- `LICENSE` — MIT.

## Deploy

Cloudflare Pages, projekt `kosprint-konirna`. Wrangler je již autentizován.

```bash
npx wrangler pages deploy . --project-name kosprint-konirna
```

Push na GitHub neaktivuje žádný auto-deploy — CF Pages se nasazuje vždy ručně přes wrangler z lokálu.

## Tisknutelné materiály (sekce „K tisku")

JS funkce v `index.html` otevírají nové okno s vlastním CSS a volají `window.print()`:
- `printHarmonogramProcedura()` — A4 oboustranně.
- `printStarterCheat()` — tahák startéra, A4 oboustranně.
- `printBoxNumbers()` — 8 stránek, velká čísla 1-8 (7-8 oranžová „rezerva"). Logo (`<img class="box-logo-tl">`) vlevo nahoře z externí URL `https://www.ceskyorientak.cz/wp-content/uploads/2025/03/logo_tmave.svg`. **Nápis „BOX" se nepoužívá** — překrýval by se s logem.
- `printPokynyPredStartem()` — jednostránkový A4, 5 bullet bodů.

Při úpravách rozložení tisku zachovat: `position: relative` na `.box-page`, absolutně pozicovaná loga (top/left nebo bottom/right 14mm, height 22mm).

## Kontextové konvence (důležité při editaci)

- **Jazyk**: čeština. Veškerý text v UI.
- **Pomlčky**: používat krátkou pomlčku `-`, ne em-dash `—`.
- **Terminologie**: „KO sprint" (ne „K.O.", ne „KO Sprint"), „desky" (plurál), „sprej" (ne „spray"), „ruličky", „výřezy", „self-choice", „karanténa", „kojemi"/„boxy".
- **Placeholdery v hranatých závorkách**: `[Název závodu]`, `[Datum závodu]`, `[doplnit]`, `[email vedoucího]`, `[telefon vedoucího]`. Při změnách obsahu je neztratit — uživatel šablony si je vyplňuje sám.
- **Bez konkrétních jmen v procedurálních popiscích** — používá se jen role: `Vedoucí`, `Zapisovač`, `Speaker`, `Vodič`, `Box`. Konkrétní jména patří jen do tabulky „Obsazení konírny" a do patičky (kde má pořadatel doplnit svá).
- **Box mirroring**: V SVG je zrcadlené pořadí kvůli streamovací kameře — Box 6 vlevo, Box 1 vpravo.
- **D21 vs H21**: jiná trať → mezi kategoriemi probíhá kompletní výměna všech ruliček.
- **Self-choice výřezy** zůstávají v deskách po celé SF, mění se jen mezi SF a F. **Ruličky map** se naopak liší pro D21 a H21.

## Atribuce

V patičce: „Infoweb vytvořil Roman Věžník (TTR7901)" — neměnit, jde o autorství šablony, ne o pořadatele.
