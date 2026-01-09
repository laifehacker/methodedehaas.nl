# Codedocumentatie - Methode de Haas Website

## Project Overzicht

**Website:** methodedehaas.nl
**Type:** Statische website voor manuele therapiepraktijk
**Framework:** Astro 5 + Tailwind CSS 4
**Doel:** Professionele online aanwezigheid voor de Methode de Haas praktijk in Zoetermeer

---

## Technische Stack

### Waarom Astro?

- **Statische site generatie** - Snelle laadtijden, geen server nodig
- **Zero JavaScript by default** - Minimale bundle size
- **Component-based** - Herbruikbare onderdelen
- **SEO-vriendelijk** - Volledige controle over HTML output
- **Eenvoudige hosting** - Kan overal gehost worden (Plesk, Netlify, etc.)

### Waarom Tailwind CSS?

- **Utility-first** - Snelle styling zonder custom CSS te schrijven
- **Consistentie** - Design tokens via configuratie
- **Productie-optimalisatie** - Ongebruikte CSS wordt automatisch verwijderd
- **Responsive design** - Ingebouwde breakpoint utilities

---

## Projectstructuur

```
methodedehaas.nl/
├── src/
│   ├── components/       # Herbruikbare componenten
│   │   ├── Navbar.astro  # Navigatie (desktop + mobiel)
│   │   └── Footer.astro  # Footer met contactinfo
│   │
│   ├── layouts/
│   │   └── Layout.astro  # Hoofdlayout met SEO, Schema.org
│   │
│   ├── pages/            # Pagina's (URL = bestandsnaam)
│   │   ├── index.astro           # Homepage
│   │   ├── methode-de-haas.astro # Over de methode
│   │   ├── wil-de-haas.astro     # Over de grondlegger
│   │   ├── therapeuten.astro     # Erik & Marieke
│   │   ├── behandeling.astro     # Behandelproces
│   │   ├── praktisch.astro       # Tarieven, vergoedingen
│   │   ├── contact.astro         # Contactpagina
│   │   └── kennisbank/           # SEO artikelen
│   │       ├── index.astro
│   │       └── [artikelen].astro
│   │
│   ├── styles/
│   │   └── global.css    # Tailwind imports + custom styles
│   │
│   └── img/              # Bronafbeeldingen
│
├── public/
│   └── images/           # Geoptimaliseerde afbeeldingen
│       ├── wil-de-haas.jpg
│       ├── erik.jpg
│       ├── marieke.jpg
│       └── marieke4-3.png
│
├── .claude/              # Claude Code documentatie
│   ├── deploy.md         # Deploy instructies
│   ├── codedocumentatie.md  # Dit bestand
│   └── voortgang.md      # Procesvoortgang
│
└── dist/                 # Build output (niet in git)
```

---

## Architectuurbeslissingen

### 1. Component Structuur

**Layout.astro** is het hart van de site:
- Bevat alle `<head>` content (meta tags, Open Graph, Twitter Cards)
- Schema.org JSON-LD voor SEO (Organization, LocalBusiness, WebSite)
- Geo-tags voor lokale vindbaarheid
- Slots voor header, content en footer

**Waarom slots?**
```astro
<Layout>
  <Navbar slot="header" />
  <!-- Page content -->
  <Footer slot="footer" />
</Layout>
```
Dit geeft flexibiliteit - elke pagina kan eigen header/footer logica hebben indien nodig.

### 2. Navigatie

**Desktop:** Horizontale nav links met active state highlighting
**Mobiel:** Hamburger menu met slide-down animatie

De navigatie is gedefinieerd als array voor makkelijk onderhoud:
```javascript
const navLinks = [
  { href: '/', label: 'Home' },
  { href: '/methode-de-haas', label: 'De Methode' },
  // ...
];
```

### 3. SEO Strategie

**On-page SEO:**
- Unieke title en description per pagina
- Semantic HTML (h1, h2, article, section)
- Alt-teksten op alle afbeeldingen

**Structured Data (Schema.org):**
- `MedicalBusiness` + `PhysicalTherapy` types
- Founder en employee informatie
- Adres, telefoon, openingstijden
- Geo-coordinaten voor lokale zoekopdrachten

**Kennisbank artikelen:**
- Long-form content voor zoekwoorden
- Interne links naar hoofdpagina's
- FAQ-achtige structuur

### 4. Afbeeldingen

**Bronbestanden:** `/src/img/` (originelen)
**Productie:** `/public/images/` (geoptimaliseerd)

Afbeeldingen worden handmatig gekopieerd en hernoemd voor consistentie:
- `wil-de-haas.jpg` - Groepsfoto overdracht
- `erik.jpg` - Portret Erik Berkelaar
- `marieke.jpg` - Portret Marieke (cirkel op homepage)
- `marieke4-3.png` - Portret Marieke (4:3 op therapeuten pagina)

### 5. Styling Conventies

**Tailwind classes** worden direct in componenten gebruikt.

**Custom utility classes** in `global.css`:
```css
.section { @apply py-16 lg:py-24; }
.container { @apply max-w-7xl mx-auto; }
.btn { @apply inline-flex items-center justify-center rounded-lg font-medium transition-colors; }
.btn-primary { @apply bg-emerald-600 text-white hover:bg-emerald-700; }
.card { @apply bg-white rounded-2xl shadow-sm; }
.badge { @apply inline-block px-3 py-1 text-sm font-medium rounded-full; }
```

**Kleurenpalet:**
- Primary: Emerald (500, 600, 700)
- Neutral: Gray scale
- Backgrounds: white, gray-50, emerald-50

---

## Praktijkinformatie

**Let op:** Deze gegevens staan op meerdere plekken en moeten consistent blijven:

| Gegeven | Waarde |
|---------|--------|
| Praktijk | Gezondheidscentrum Corporalis |
| Adres | Dorpsstraat 182B, C en D |
| Postcode | 2712 AR |
| Plaats | Zoetermeer |
| Telefoon | 079 323 7900 |
| Email | info@methodedehaas.nl |
| Therapeuten | Erik Berkelaar, Marieke Bezuijen |

**Locaties in code:**
- `Layout.astro` - Schema.org data
- `Footer.astro` - Contactgegevens
- `Navbar.astro` - Mobiel menu
- `contact.astro` - Contactpagina
- Diverse kennisbank artikelen

---

## Toekomstige Overwegingen

### Mogelijke verbeteringen:
1. **Contactformulier backend** - Huidige form heeft geen backend
2. **Google Maps embed** - Huidige iframe URL is placeholder
3. **Afbeelding optimalisatie** - Astro Image component voor WebP/AVIF
4. **Blog/Nieuws sectie** - Content collecties voor dynamische content
5. **Online afspraken** - Integratie met afsprakensysteem

### Niet geimplementeerd (bewust):
- **CMS** - Content is statisch, wijzigingen via code
- **Analytics** - Kan later toegevoegd worden
- **Cookie banner** - Geen tracking cookies aanwezig
