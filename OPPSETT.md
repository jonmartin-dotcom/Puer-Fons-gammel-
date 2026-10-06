# Oppsett av returservice for Puer Fons

Dette er en komplett, kjørbar kopi av returløsningen (samme kodebase som
Nesco/Vitae Vital/Almea), tilpasset Puer Fons med goodsOwnerId **92** og
gull/bronse-profil basert på puerfons.no.

## 1. Opprett GitHub-repo

1. Opprett et nytt, tomt repo på GitHub, f.eks. `puerfons-returservice`.
2. Last opp alt innholdet i denne zip-filen til repoet (dra inn *innholdet*
   i mappen, ikke selve `returservice-puerfons`-mappen - ellers havner alt
   i en undermappe, se merknad i prosjektnotatet om det).

## 2. Opprett Vercel-prosjekt

1. Nytt prosjekt i Vercel, koblet til det nye GitHub-repoet.
2. Sett **Framework Preset til "Next.js" manuelt** (den settes ofte feil til
   "Other" automatisk).
3. Legg inn miljøvariablene under "Environment Variables" (se punkt 3).

## 3. Miljøvariabler i Vercel

De fleste verdiene er allerede fylt ut i `.env.example` siden de er delt med
de andre vareeierne. Dette må du fylle inn selv (de er hemmelige, så de
ligger ikke i koden):

- `ONGOING_USERNAME` = `API-bruker`
- `ONGOING_PASSWORD` = (samme passord som de andre vareeierne bruker på
  bruker 115 i Ongoing)
- `WEBSHIPPER_ACCESS_TOKEN` = (samme token som de andre vareeierne bruker)

Alt annet (warehouse, goodsOwnerId=92, carrier-ID, servicekode, lageradresse
med "c/o Puer Fons") er allerede riktig fylt ut i `.env.example` - kopier
verdiene derfra rett inn i Vercel.

## 4. Sjekk tilgang i Ongoing

Gå til bruker-ID 115 ("API-bruker") i Ongoing-admin, og sjekk at **"Puer
Fons" er huket av** i "Alle vareeiere"-lista på den brukeren. Ikke bruk "API
for vareeiere"-lista (det er en annen, separat mekanisme - se prosjektnotatet
for forklaring).

## 5. Deploy og test

1. Deploy (skjer automatisk når du pusher til GitHub).
2. Test FULL flyt med et reelt eller testordrenummer for goodsOwnerId 92 -
   ordreoppslag, varevalg, kontaktinfo, og at en etikett faktisk blir
   generert - før lenken deles med kunder.

Si ifra når det er oppe, så tester jeg flyten for deg på samme måte som for
de andre vareeierne.
