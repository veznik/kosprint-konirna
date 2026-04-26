# Konírna - šablona pro pořadatele KO sprintu

Interní instruktážní web pro tým „konírny" (startovního prostoru se startovními kojemi) na závodech v orientačním běhu KO sprint - schéma rozložení, jízdní řád startovní procedury, harmonogram dne, kontrolní seznam materiálu, pohled závodníka, obsazení týmu, klíčové zásady a tisknutelné materiály.

**Live demo:** https://kosprint-konirna.pages.dev/

Šablona je odvozená z **MČR KO sprint 2026 Třebíč**. Plný archiv letošní akce (s konkrétními jmény, časy a místem) je na https://kosprint-konirna-2026.pages.dev/.

## Co umí

- Interaktivní SVG schéma konírny (6 boxů + podpora) s vysvětlením pohybu závodníků a pořadatelů.
- Harmonogram dne (svolání, starty, výměny ruliček D21/H21, pauza SF → F).
- Tahák pro startéra s přesnými časy odpočtu pro každý rozběh.
- Kontrolní seznam materiálu (odškrtávací).
- Pohled závodníka od karantény po start.
- Sekce **K tisku** - 4 tisknutelné materiály jedním klikem:
  - Harmonogram + procedura (A4 oboustranně)
  - Tahák pro startéra (A4 oboustranně)
  - Čísla na boxy 1-8 (k laminování)
  - Poslední pokyny před startem (vyvěsit v karanténě)

## Jak použít pro svůj závod

1. **Klonování / fork:**
   ```bash
   git clone https://github.com/veznik/kosprint-konirna.git
   cd kosprint-konirna
   ```

2. **Editujte `index.html`** - hlavní (a jediný) zdrojový soubor. Vše inline (HTML, CSS, SVG, JS), žádný build step.

3. **Vyplňte placeholdery v hranatých závorkách** podle svého závodu:
   - `[Název závodu]` - např. „MČR KO sprint 2027 Liberec"
   - `[Datum závodu]` - např. „Sobota 15. 4. 2027"
   - `[doplnit]` v sekci Obsazení (jména pořadatelů)
   - `[email vedoucího]`, `[telefon vedoucího]` v patičce a CTA

4. **Upravte časy v harmonogramu a v taháku startéra** podle vlastního rozpisu. Schéma poslední minuty (-1:00 výzva, -0:40 OTEVŘÍT, -0:20 ZAVŘÍT, -0:10/-0:05, 0:00 výstřel) zůstává stejné.

5. **Doplňte vlastní fotky** (`konirna-zepredu.jpg`, `konirna-zezadu.jpg`, `desky-s-vyrezy-map.jpg`, `rulicky-map.jpg`) nebo nechte stávající ze 2026 jako referenci.

6. **Otevřete `index.html`** v prohlížeči pro náhled - není potřeba server.

## Nasazení

Vyberte si:

- **GitHub Pages** - v nastavení repa zapněte Pages na branch `main`, root.
- **Cloudflare Pages** - připojte repo, build command prázdný, output directory `/`.
- **Netlify, Vercel, vlastní hosting** - stačí nahrát `index.html` + JPG fotky na statický hosting.

## Konvence

- Veškerý text je **česky**.
- Terminologie: „KO sprint" (ne „K.O.", ne „KO Sprint"), „desky", „sprej", „ruličky", „výřezy", „self-choice", „karanténa", „kojemi"/„boxy".
- V SVG je **zrcadlené pořadí boxů** (Box 6 vlevo, Box 1 vpravo) kvůli streamovací kameře.
- D21 vs H21 mají různou trať - mezi kategoriemi probíhá **kompletní výměna ruliček**.

## Licence

MIT - viz [LICENSE](LICENSE). Můžete forknout, upravit, použít komerčně. Atribuce není povinná, ale potěší.

## Autor a kontakt

Infoweb vytvořil **Roman Věžník** (TTR7901) pro tým konírny na MČR KO sprint 2026 Třebíč. Tipy na vylepšení vítány - otevřete issue nebo pull request.
