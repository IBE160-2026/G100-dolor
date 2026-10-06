# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G100 – G100-dolor |
| **Product brief** | `product-brief.md` (commit `8d93ed7`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

Vurdert fil: `product-brief.md` i repoets rot, som er den eneste briefen. Det finnes ennå ikke PRD, arkitektur eller epics.

## Samlet vurdering

- **Godt utgangspunkt med justeringer.** Gruppen kan gå videre og innarbeide punktene under.

**Det som er bra:**

1. Briefen er skrevet med egen stemme og er ærlig om valgene: dere har valgt et avgrenset prosjekt for å rekke å gjøre det ordentlig, og vil bruke tiden på å teste at KI-koden faktisk virker. Det er en god holdning i dette emnet.
2. Avgrensningen er tydelig og fornuftig: innlogging, synkronisering, varsler og mobilapp er utelatt, og dere vil «først se om selve KI-forslagene er gode nok til å stole på».

**De viktigste endringene:**

1. Utvid omfanget litt. Slik Scope står, består appen av CRUD for oppgaver pluss ett KI-forslag. Det kan bli ferdig svært raskt og gir lite å vise. Det mangler også noe for å bruke prioriteten til noe: legg i det minste til sortering og filtrering etter prioritet, kategori og forfallsdato, og gjerne smarte lister som «Haster» og «Denne uken».
2. Gjør suksesskriteriene målbare. «De fleste oppgavene», «innen noen sekunder» og «ingen store feil» kan ikke sjekkes entydig. Lag et testsett, for eksempel 20 oppgavetekster med forventet kategori og prioritet, og sett et mål (for eksempel minst 15 av 20 riktige). Sett også en konkret tidsgrense, for eksempel under 5 sekunder.
3. Definer kategoriene og prioritetsnivåene. Briefen sier ikke hvilke kategorier som finnes, eller hva som gjør en oppgave «høy» prioritet. Skriv dette ned, slik at både KI-en og testene har noe å forholde seg til.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Enkel**

**Sammenlignbart med:** 6) To-do-liste med smarte etiketter (enkel). Briefen dekker en del av dette forslaget (kategori og prioritet), men ikke sammendrag eller smarte lister.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Lav | Få regler ut over CRUD. Prioritetsreglene er ikke definert ennå. |
| Datamodell – antall entiteter og relasjoner mellom dem | Lav | Oppgave og kategori. |
| Brukere, roller og innlogging | Lav | Én bruker uten innlogging. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Lav til middels | Ett KI-kall som gir kategori og prioritet. Krever strukturert svar og håndtering av feil. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Lav | Bare språkmodell-API. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Lav | Ingen. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Lav | Ingen. |
| Sikkerhet og personvern | Lav | Oppgavetekst sendes til en ekstern KI-tjeneste. Nevn det kort i appen. |

**Hva vanskelighetsgraden betyr for dere:**

- _Enkel:_ Et enkelt prosjekt gir stor sjanse for å bli ferdig. Vanskelighetsgraden inngår likevel i vurderingen, så for å nå helt opp må dere vise mer i gjennomføringen. Det betyr særlig et gjennomarbeidet design, grundig testing, en tydelig dokumentert prosess og en README som virker.

### Gjennomførbarhet med BMAD og Claude Code

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | OK | Ja, med god margin. Risikoen er at det blir for lite å vise, ikke for mye. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Risiko | Kjerneflyten er klar, men det blir få stories, og kategorier og prioritetsregler mangler. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | Enkel webapp med CRUD og ett API-kall er svært godt egnet. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | OK | Alt kan kontrolleres ved å bruke appen, og med et testsett kan dere vurdere KI-forslagene systematisk. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Risiko | CRUD kan testes, men KI-kriteriene er for vage. Lag testsett og bruk mock-svar i automatiske tester. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Ikke beskrevet. KI-delen trenger testmodus eller reserveforslag. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Krever språkmodell-API, uten plan for nøkkel, kostnad eller testmodus. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart som beskrevet.**

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Legg til sortering, filtrering og smarte lister i v1, slik at kategori og prioritet faktisk brukes til å gi oversikt.
2. Vurder én KI-utvidelse som løfter prosjektet, for eksempel at KI-en også foreslår forfallsdato fra tekst som «innen fredag», eller lager et kort sammendrag av lange oppgaver. Bruk samme mønster: forslag som brukeren kan godta eller endre.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Klart og personlig: oppgaveliste der KI foreslår kategori og prioritet. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | Juster | Forståelig, men generelt. Gi et konkret eksempel på en lang liste og hva som går galt. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | OK | Beskriver hva brukeren gjør og ser, og hva som er utelatt. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig: dere prøver ikke å finne opp noe nytt. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | Juster | «Personer som legger inn mange oppgaver i farta» er en god start. Si gjerne hvem (studenter? deg selv?) og på hvilken enhet, siden «i farta» kan bety mobil. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | Kriteriene er for vage til å sjekkes. Legg inn testsett, måltall og tidsgrense. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Juster | Tydelig, men for lite, og sortering/filtrering mangler. Utvid som foreslått. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Delte lister og kalender er tydelig lagt etter v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Grei start. Bruk BMAD videre (PRD, arkitektur, stories), commit jevnlig og lagre promptene. Planen om å bruke tiden på testing er god å dokumentere underveis. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Juster | Realistisk, men for lite. Legg til sortering, filtrering og en KI-utvidelse. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Vage kriterier gir ikke testtilfeller. Testsett med forventede svar vil gjøre dette til en styrke. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | Juster | Enkel flyt som er lett å se for seg. Skisser hvordan forslaget vises og endres, og bestem om appen skal fungere godt på mobil. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | OK | Ingen teknologi valgt ennå, og det er greit. Hold det enkelt, og kall KI fra serveren. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Planlegg testmodus eller reserveforslag for KI. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Bestem en mappe for planleggingsdokumenter og testsett, og hold API-nøkkelen i `.env` utenfor Git. |

## 3. Neste steg for gruppen

1. Skriv ned kategoriene og prioritetsnivåene, og lag et testsett med rundt 20 oppgaver og forventede svar. Skriv om suksesskriteriene med måltall.
2. Utvid Scope med sortering, filtrering og smarte lister, og vurder én KI-utvidelse.
3. Velg KI-tjeneste med plan for nøkkel og testmodus, og lag PRD med BMAD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
