# Deploy Instructies - VERPLICHT

## Vereiste stappen voor elke deploy

**BELANGRIJK: Volg deze stappen ALTIJD in de juiste volgorde!**

### 1. Lokale build draaien (VERPLICHT)

```bash
npm run build
```

- Controleer dat de build ZONDER FOUTEN afrondt
- Fix eventuele build errors voordat je doorgaat
- De `dist/` folder bevat nu de productie-bestanden

### 2. Test de build lokaal (aanbevolen)

```bash
npm run preview
```

- Controleer de site op http://localhost:4321
- Verifieer dat alle pagina's correct laden
- Controleer afbeeldingen en styling

### 3. Commit en push

Pas NA een succesvolle build:

```bash
git add .
git commit -m "Beschrijving van wijzigingen"
git push
```

## Waarom deze volgorde?

- Build errors worden lokaal ontdekt, niet pas op de server
- Voorkomt dat een kapotte site live gaat
- Bespaart tijd bij het debuggen

## Checklist voor deploy

- [ ] `npm run build` succesvol afgerond
- [ ] Geen TypeScript/ESLint errors
- [ ] Site getest met `npm run preview`
- [ ] Commit gemaakt met duidelijke beschrijving
- [ ] Gepusht naar remote
