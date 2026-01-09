# Voortgangslog - Methode de Haas Website

Dit document houdt de ontwikkelingsvoortgang bij. Elke significante wijziging wordt hier gedocumenteerd.

---

## 2025-01-09 - Apache .htaccess Fix voor Productie

### Wat is gedaan:
- `.htaccess` toegevoegd aan `public/` folder
- RewriteEngine regels voor URL routing
- Caching en compressie instellingen

### Probleem:
- Productie site (methodedehaas.baksteen.dev) gaf 500 errors op alle pagina's behalve homepage
- `/therapeuten` → 500 error
- `/therapeuten/index.html` → werkte wel

### Oorzaak:
- Apache server serveerde geen `index.html` voor directory URLs zonder trailing slash
- Astro genereert statische bestanden als `/pagina/index.html`
- Browser vraagt `/pagina` aan, Apache kan dat niet vinden

### Oplossing:
- `.htaccess` met RewriteEngine regels om `/pagina` → `/pagina/index.html` te redirecten
- Ook regels voor directories met trailing slash

### Bestanden toegevoegd:
- `public/.htaccess` - Apache URL routing configuratie

---

## 2025-01-09 - Documentatie & Deploy Setup

### Wat is gedaan:
- `.claude/deploy.md` aangemaakt met verplichte deploy instructies
- `.claude/codedocumentatie.md` aangemaakt met uitgebreide technische documentatie
- `.claude/voortgang.md` aangemaakt (dit bestand)

### Waarom:
- Duidelijke deploy workflow voorkomt dat kapotte builds live gaan
- Codedocumentatie zorgt voor kennisbehoud bij toekomstige wijzigingen
- Voortgangslog geeft inzicht in wat er is gedaan en waarom

---

## 2025-01-09 - Foto Updates Therapeuten

### Wat is gedaan:
- Marieke's foto op therapeuten pagina gewijzigd naar `marieke4-3.png`
- Bestaande foto's behouden op homepage (ronde thumbnails)

### Bestanden gewijzigd:
- `src/pages/therapeuten.astro` - Nieuwe afbeelding src

### Waarom:
- Betere aspect ratio (4:3) voor de grotere kaarten op therapeuten pagina
- Homepage gebruikt ronde uitsnede, daar past `marieke.jpg` beter

---

## Eerdere Sessies - Locatie Update Pijnacker → Zoetermeer

### Wat is gedaan:
- Alle verwijzingen naar Pijnacker (Klein Vlieland 2) vervangen
- Nieuwe locatie: Gezondheidscentrum Corporalis, Zoetermeer
- Adres: Dorpsstraat 182B, C en D, 2712 AR Zoetermeer
- Telefoon behouden: 079 323 7900

### Bestanden gewijzigd:
- `src/layouts/Layout.astro` - Schema.org data, geo-coordinaten
- `src/components/Footer.astro` - Contactgegevens
- `src/components/Navbar.astro` - Mobiel menu
- `src/pages/contact.astro` - Adres en kaart
- `src/pages/wil-de-haas.astro` - Verhaal en contactinfo
- `src/pages/index.astro` - CTA sectie
- Alle kennisbank artikelen

### Waarom:
- Praktijk is verhuisd van Pijnacker naar Zoetermeer
- Erik Berkelaar en Marieke Bezuijen zetten de methode voort
- Wil de Haas is teruggetreden maar blijft vermeld als grondlegger

---

## Eerdere Sessies - Foto's Toevoegen

### Wat is gedaan:
- `wil-de-haas.jpg` toegevoegd aan public/images
- `erik.jpg` toegevoegd aan public/images
- `marieke.jpg` toegevoegd aan public/images
- `marieke4-3.png` toegevoegd aan public/images

### Bestanden gewijzigd:
- `src/pages/index.astro` - Foto's in therapeuten sectie
- `src/pages/wil-de-haas.astro` - Hero foto
- `src/pages/therapeuten.astro` - Grote profielkaarten

### Waarom:
- Professionele uitstraling met echte foto's
- Persoonlijke connectie met bezoekers
- Vertrouwen opbouwen door gezichten te tonen

---

## Eerdere Sessies - Initiële Website Opzet

### Wat is gebouwd:
- Complete Astro 5 + Tailwind CSS 4 website
- Responsive design (mobile-first)
- SEO geoptimaliseerd met Schema.org
- Kennisbank met SEO artikelen

### Pagina's:
1. **Homepage** - Hero, USPs, therapeuten intro, CTA
2. **De Methode** - Uitleg over de behandelmethode
3. **Wil de Haas** - Verhaal van de grondlegger
4. **Therapeuten** - Erik Berkelaar & Marieke Bezuijen
5. **Behandeling** - Wat te verwachten
6. **Praktisch** - Tarieven en vergoedingen
7. **Contact** - Contactgegevens en formulier
8. **Kennisbank** - SEO artikelen over klachten en behandelingen

### Design keuzes:
- **Emerald groen** als primaire kleur (rust, gezondheid, natuur)
- **Witte achtergrond** met subtiele groene accenten
- **Serif-loze lettertypes** voor moderne uitstraling
- **Ruime whitespace** voor professionele, rustige look

---

## Template voor Nieuwe Entries

```markdown
## YYYY-MM-DD - [Korte Titel]

### Wat is gedaan:
- [Bullet points van wijzigingen]

### Bestanden gewijzigd:
- `pad/naar/bestand.astro` - Beschrijving

### Waarom:
- [Reden voor de wijziging]

### Wat niet werkte / Alternatieven geprobeerd:
- [Indien van toepassing]

### Open punten:
- [Indien van toepassing]
```
