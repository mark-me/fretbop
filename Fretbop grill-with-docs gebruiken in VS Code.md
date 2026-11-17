# Fretbop: grill-with-docs gebruiken in VS Code

Nov 17, 2026 · @Mark

## Wat grill-with-docs doet

`/grill-with-docs` interviewt je over je ontwerp, net als `/grill-me`, maar legt de uitkomsten vast in je repo: termen in `GLOSSARY.md` en besluiten als ADR's in `docs/adr/`.

| | `/grill-me` | `/grill-with-docs` |
| --- | --- | --- |
| Geheugen | Geen: schrijft niets weg | Leest je repo en schrijft bestanden |
| Bestanden | Geen | `GLOSSARY.md` (root), `docs/adr/0001-slug.md` enz. |
| Gebruikt | `grilling` | `grilling` + `domain-modeling` |
| Wanneer | Los idee, nog geen repo | Repo met documentatie of code |

De skill zelf is kort: hij roept twee andere skills aan, `grilling` (het interview) en `domain-modeling` (woordenlijst en ADR's). Die twee moet je dus ook installeren.

- **grilling** werkt in rondes. Elke ronde bevat genummerde vragen, met per vraag een aanbevolen antwoord. "Ja" betekent dat je de aanbeveling overneemt.
- **domain-modeling** werkt `GLOSSARY.md` direct bij zodra een term vastligt. Een ADR stelt hij alleen voor als een besluit moeilijk terug te draaien is, zonder context verrassend is, en het resultaat is van een echte afweging.

Bronnen: [AI Hero – grill-me](https://www.aihero.dev/skills-grill-me), [grill-with-docs SKILL.md](https://github.com/mattpocock/skills/blob/HEAD/skills/engineering/grill-with-docs/SKILL.md), [domain-modeling SKILL.md](https://github.com/mattpocock/skills/blob/HEAD/skills/engineering/domain-modeling/SKILL.md), [grilling SKILL.md](https://github.com/mattpocock/skills/blob/HEAD/skills/productivity/grilling/SKILL.md)

## Skills installeren

Installeer drie skills in één keer: `grill-with-docs` en de twee die hij aanroept.

**Nodig:** VS Code met de Claude Code-extensie, en Node.js (voor `npx`).

1. Open de map `fretbop` in VS Code.
2. Open de terminal (**Terminal → New Terminal**) en voer uit:

```bash
npx -y skills@latest add mattpocock/skills --skill grill-with-docs --skill grilling --skill domain-modeling --agent claude-code
```

1. Controleer waar de skills terechtkwamen: in de repo (`.claude/skills/`) of in je thuismap (`~/.claude/skills/`). Staan ze in de repo, commit ze dan mee, zodat ze ook op een andere machine werken.
2. Herlaad VS Code (**Command Palette → Developer: Reload Window**), open het Claude-paneel en typ `/`. Je moet `grill-with-docs` in de lijst zien.

Later bijwerken: `npx skills update`.

**Waarom `--agent claude-code`:** zonder die optie kan de installer de skills in `.agents/skills/` zetten, een map die Claude Code niet leest ([bron](https://vibeindex.ai/skills/mattpocock/skills/grill-with-docs), [bron](https://claudemarketplaces.com/skills/mattpocock/skills/grill-with-docs)).

Al `grill-me` en `grilling` geïnstalleerd? Dan kan dat blijven staan; de opdracht hierboven voegt alleen toe wat ontbreekt.

## De repo voorbereiden

Zet de besluiten uit `docs/decisions.md` om naar losse ADR's in `docs/adr/`, anders heb je na de eerste sessie twee besluitenregisters naast elkaar.

`domain-modeling` verwacht ADR's in `docs/adr/` met volgnummers (`0001-slug.md`, `0002-slug.md`) en zoekt het hoogste nummer om verder te tellen ([ADR-FORMAT.md](https://github.com/mattpocock/skills/blob/HEAD/skills/engineering/domain-modeling/ADR-FORMAT.md)). Een ADR mag één alinea zijn: een titel en 1–3 zinnen met context, besluit en reden.

**Doelstructuur:**

```
fretbop/
├── README.md
├── LICENSE
├── CLAUDE.md
├── GLOSSARY.md            # maakt de skill zelf aan bij de eerste term
└── docs/
    ├── grilling-brief.md
    └── adr/
        ├── 0001-target-audience.md
        ├── 0002-instruments-as-data.md
        ├── …
        └── 0015-project-name.md
```

1. Maak `docs/adr/` en zet elk besluit uit `decisions.md` in een eigen bestand (één besluit = één ADR).
2. Verwijder `docs/decisions.md`. De fasen en de stack verhuizen naar `README.md`.
3. Pas in `CLAUDE.md` de verwijzing aan van `docs/decisions.md` naar `docs/adr/` en `GLOSSARY.md`.
4. Pas in `docs/grilling-brief.md` "Decisions 8–15" aan naar "ADRs 0008–0015".
5. Commit: `git add . && git commit -m "Convert decisions to ADRs"`.

`GLOSSARY.md` hoef je niet vooraf te maken: de skill maakt hem aan zodra de eerste term vastligt.

## Plan mode uitzetten

Kies onder het invoerveld van het Claude-paneel een andere modus dan Plan; voor grill-with-docs werkt de modus waarin Claude vraagt vóór elke bewerking het best.

Plan mode is hier om twee redenen ongeschikt: Claude mag dan geen bestanden schrijven (dus geen `GLOSSARY.md` of ADR's), en de modus duwt de agent naar een plan voordat het interview klaar is.

**Per gesprek:** klik op de modusindicator onderaan het invoerveld en kies een andere modus dan Plan ([Claude Code-documentatie](https://code.claude.com/docs/en/permission-modes)). Die keuze geldt alleen voor dat gesprek.

**Als standaard voor elk nieuw gesprek:**

1. Open **Settings** (`Ctrl+,` of `Cmd+,`).
2. Zoek op `Claude Code initial permission mode`.
3. Kies `default` (vraagt toestemming per bewerking). Niet `plan`.

Of in `settings.json` van VS Code:

```json
"claudeCode.initialPermissionMode": "default"
```

**Let op:** de instelling `permissions.defaultMode` in `.claude/settings.json` van je project bepaalt níet met welke modus een VS Code-gesprek start. Daarvoor telt alleen de VS Code-instelling hierboven ([bron](https://alexcloudstar.com/md/blog/claude-code-plan-mode-2026/)).

**Waarom `default` en niet automatisch bewerken:** je ziet dan elke `GLOSSARY.md`-wijziging en elke nieuwe ADR voordat hij geschreven wordt, en kunt afwijzen wat niet klopt. Wordt dat te veel geklik, kies dan `acceptEdits` en controleer alles achteraf met `git diff`.

## Een sessie starten

Start elke sessie in een nieuw gesprek, met plan mode uit, en geef één onderwerp uit de briefing mee.

1. Open de map `fretbop` in VS Code en open het Claude-paneel.
2. Begin een **nieuw gesprek**, zodat oude context de sessie niet stuurt.
3. Controleer de modusindicator: niet Plan.
4. Plak de startprompt hieronder en verstuur.

```
/grill-with-docs Read CLAUDE.md, docs/adr/ and docs/grilling-brief.md first. Grill me on topic 1 of the brief only: the didactic sequence of the first 10 lessons.
```

**Eén onderwerp per sessie.** De briefing heeft vijf onderwerpen. Per sessie één houdt het gesprek kort genoeg om scherp te blijven, en elke sessie eindigt met een commit. Vervang bij de volgende sessie "topic 1" door het volgende nummer.

**Volgorde:** begin met onderwerp 1 (didactiek). Beheersing (2) en de definitie van "klaar" (4) hangen ervan af.

## Tijdens de sessie

Jij beslist, Claude zoekt feiten op: beantwoord elke vraag met ja, nee met reden, of "weet ik niet".

**Rondes of één vraag tegelijk.** `grilling` stelt standaard per ronde alle vragen die nu al te beantwoorden zijn, genummerd, elk met een aanbevolen antwoord. Jouw `CLAUDE.md` vraagt om één vraag tegelijk; die regel gaat waarschijnlijk voor. Wil je liever rondes, haal de regel dan uit `CLAUDE.md`.

**Zo antwoord je:**

| Je antwoord | Wat er gebeurt |
| --- | --- |
| `ja` | Je neemt de aanbeveling over |
| `nee, want …` | Claude past het ontwerp aan en vraagt door |
| `weet ik niet` | Claude onderzoekt het of stelt een kleinere vraag; vaak de nuttigste vervolgvragen |
| `parkeer dit` | De vraag blijft open; vraag aan het eind om een lijst |

Vermijd een reeks `ja`-antwoorden zonder nadenken: dan schrijft de skill Claude's aannames vast als jouw besluiten.

**GLOSSARY.md.** Claude wijst je op wisselend taalgebruik ("je zei *greep*, eerder *voicing*") en legt de gekozen term vast. Houd de woordenlijst Engels, net als de code; Nederlandse UI-termen horen in de vertaalbestanden, niet in de glossary. De glossary bevat geen implementatiedetails.

**ADR's.** Claude stelt een ADR voor wanneer een besluit moeilijk terug te draaien is, verrassend zonder context, en een echte afweging. Wijs een voorgestelde ADR gerust af als hij aan een van die drie niet voldoet.

**Einde.** De sessie is klaar als er geen open vragen meer zijn. Claude vraagt dan of jullie hetzelfde begrip hebben; pas na jouw bevestiging handelt hij erop.

## Afronden

Controleer na elke sessie wat er veranderd is en commit het, voordat je aan het volgende onderwerp begint.

- [ ] Bekijk de wijzigingen: `git status` en `git diff` (of het Source Control-paneel van VS Code).
- [ ] Lees elke nieuwe ADR in `docs/adr/`: klopt het besluit en de reden?
- [ ] Lees de nieuwe termen in `GLOSSARY.md`: staan er geen implementatiedetails in?
- [ ] Vraag Claude om een lijst van geparkeerde vragen en zet die onderaan `docs/grilling-brief.md`.
- [ ] Werk `docs/grilling-brief.md` bij: zet het afgeronde onderwerp onder "Settled".
- [ ] Commit: `git add . && git commit -m "Grilling: <onderwerp>"`.

Klopt een ADR niet, pas hem dan zelf aan of verwijder hem voor je commit. Wat in de repo staat, gebruikt de volgende sessie als waarheid.

## Werkwijze per onderwerp

Elk onderwerp krijgt een eigen branch en een nieuw gesprek. Je merget de branch naar `main` voordat je aan het volgende onderwerp begint.

Het geheugen tussen sessies zit in de repo, niet in het gesprek: de ADR's en `GLOSSARY.md` die op `main` staan, zijn het startpunt voor de volgende ronde.

1. **Branch maken vanaf een bijgewerkte `main`:**

   ```bash
   git switch main && git pull
   git switch -c grill/02-mastery
   ```

2. **Nieuw gesprek** in het Claude-paneel, modus niet Plan, met de startprompt voor het volgende onderwerp:

   ```
   /grill-with-docs Read CLAUDE.md, GLOSSARY.md, docs/adr/ and docs/grilling-brief.md first. Grill me on topic 2 of the brief only: mastery thresholds.
   ```

3. **Sessie doen**, op de branch. Claude schrijft ADR's en termen in de werkmap.
4. **Afronden** met de checklist hierboven, en committen op de branch.
5. **Mergen naar `main`.** Via een pull request op GitHub zie je alle nieuwe ADR's in één overzicht, handig om ze na te lezen. Alleen werken mag ook lokaal:

   ```bash
   git switch main
   git merge --no-ff grill/02-mastery
   git push
   git branch -d grill/02-mastery
   ```

6. **Terug naar stap 1** voor het volgende onderwerp.

**Branchnamen:**

| Onderwerp | Branch |
| --- | --- |
| 1 Didactische volgorde | `grill/01-didactics` |
| 2 Beheersing | `grill/02-mastery` |
| 3 Risico fase 3 | `grill/03-chord-detection-risk` |
| 4 Definitie van klaar | `grill/04-definition-of-done` |
| 5 Uitbreiding instrumenten | `grill/05-instrument-extension` |

**Eén onderwerp tegelijk open.** De skill nummert ADR's door vanaf het hoogste nummer in `docs/adr/`. Twee open branches maken allebei bijvoorbeeld een `0016`, wat bij het mergen botst. Merge daarom eerst, begin dan pas aan het volgende onderwerp.

**Een mislukte sessie weggooien.** Bevalt een sessie niet, dan gooi je de branch weg en begin je opnieuw vanaf `main`:

```bash
git switch main
git branch -D grill/02-mastery
```

**Een eerder besluit herzien.** Verandert een onderwerp een bestaand besluit, laat Claude dan geen bestaande ADR overschrijven. Hij schrijft een nieuwe ADR, en de oude krijgt bovenaan `Status: superseded by ADR-00NN`. Zo blijft zichtbaar waarom het besluit veranderde.

## Problemen oplossen

| Probleem | Oplossing |
| --- | --- |
| `/grill-with-docs` staat niet in de `/`-lijst | Controleer of de skills in `.claude/skills/` of `~/.claude/skills/` staan, niet in `.agents/skills/`. Herinstalleer met `--agent claude-code` en herlaad het venster. |
| Claude meldt dat `grilling` of `domain-modeling` ontbreekt | Installeer ze alsnog met de opdracht uit **Skills installeren**. |
| Claude maakt een plan in plaats van vragen te stellen | Plan mode staat aan. Kies een andere modus en begin een nieuw gesprek. |
| Elk nieuw gesprek start in Plan | Zet `claudeCode.initialPermissionMode` in de VS Code-instellingen op `default`. |
| Claude vraagt om bestanden te bewerken en je wilt niet steeds klikken | Kies voor die sessie `acceptEdits` en controleer achteraf met `git diff`. |
| ADR's krijgen een nummer dat al bestaat of een eigen formaat | Controleer of je oude besluiten echt in `docs/adr/` staan met het formaat `0001-slug.md`. |
| Claude heropent besluiten die vastliggen | Verwijs in je antwoord naar de "Settled"-lijst in `docs/grilling-brief.md`. |
| `npx` wordt niet gevonden | Installeer Node.js en open een nieuwe terminal. |
