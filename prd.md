# Product Requirements Document (PRD)
## Budget Balancer - Interactieve Rijksbegroting Simulator

### 1. Product Overview

**Product Name:** Budget Balancer  
**Target Audience:** HBO Bedrijfskunde studenten  
**Product Type:** Educatieve web applicatie  
**Platform:** Responsive web app (HTML/CSS/JavaScript)

**Vision Statement:**  
Budget Balancer maakt complexe overheidsfinanciën begrijpelijk door studenten interactief hun ideale Nederlandse rijksbegroting te laten samenstellen via een intuïtieve, visuele interface.

### 2. Problem Statement

HBO Bedrijfskunde studenten hebben vaak moeite met het begrijpen van de complexiteit en omvang van overheidsuitgaven. Traditionele lesmethoden maken gebruik van statische tabellen en grafieken die weinig inzicht geven in de onderlinge verhoudingen en trade-offs tussen verschillende beleidskeuzes.

### 3. Success Metrics

**Primary KPIs:**
- Gemiddelde sessieduur > 10 minuten
- Voltooiingspercentage > 80%
- Gebruikerstevredenheid > 4.0/5.0

**Secondary KPIs:**
- Aantal gegenereerde PDF-rapporten
- Hergebruik van de applicatie binnen 7 dagen
- Aantal gedeelde begrotingen (toekomstige feature)

### 4. User Stories & Requirements

#### 4.1 Core User Stories

**Als student wil ik:**
- Snel begrijpen hoeveel de overheid uitgeeft en waaraan
- Experimenteren met verschillende budgetallocaties zonder complexe berekeningen
- Zien wat de gevolgen zijn van mijn keuzes in real-time
- Mijn ideale begroting als PDF kunnen downloaden voor presentatie/studie
- De applicatie op elke device kunnen gebruiken

**Als docent wil ik:**
- Dat studenten hands-on leren over overheidsfinanciën
- Discussiemateriaal krijgen uit studentenbegrotingen
- Dat de tool actuele data gebruikt

#### 4.2 Functional Requirements

**Must Have (MVP):**
- Visuele weegschaal interface met uitgaven (links) vs inkomsten (rechts)
- Interactieve sliders voor alle 15 uitgavencategorieën uit rijksbegroting 2026
- Real-time berekening en visualisatie van budgetbalans
- Kleurgecodeerd feedback systeem (rood=tekort, groen=overschot)
- Responsive design voor desktop, tablet en mobiel
- PDF export functionaliteit
- Local storage voor het bewaren van voortgang

**Should Have:**
- Cirkelvormige "budget-klok" voor proportionele weergave
- Iconische representaties per budgetcategorie
- Animaties bij wijzigingen
- Vergelijking met originele rijksbegroting 2026
- Tooltips met uitleg per categorie

**Could Have:**
- "Reset naar origineel" functie
- Meerdere scenario's kunnen opslaan
- Eenvoudige sharing functionaliteit
- Geavanceerde visualisaties (bijv. Sankey diagram)

**Won't Have (deze versie):**
- User accounts/login
- Backend database
- Multi-year projections
- Advanced economic modeling

### 5. Technical Requirements

#### 5.1 Frontend Stack
- **HTML5:** Semantische markup
- **CSS3:** Flexbox/Grid layout, CSS animaties
- **JavaScript (ES6+):** Vanilla JS of lichtgewicht framework
- **Chart Library:** Chart.js of D3.js voor visualisaties
- **PDF Generation:** jsPDF library
- **Icons:** Feather Icons of Heroicons

#### 5.2 Performance Requirements
- Laadtijd < 3 seconden
- Responsive design breakpoints: 320px, 768px, 1024px, 1200px+
- Browser support: Chrome, Firefox, Safari, Edge (laatste 2 versies)
- Offline functionaliteit via service workers (nice-to-have)

#### 5.3 Data Requirements
- Statische data uit Rijksbegroting 2026
- Local storage max 5MB voor gebruikersdata
- JSON data structure voor budget categorieën

### 6. User Interface Design Specifications

#### 6.1 Layout Structure
```
Header: Titel + Reset Button
├── Budget Balance Indicator (centraal)
├── Left Panel: Uitgaven Sliders
│   ├── Sociale Zekerheid (€124.7B)
│   ├── Zorg (€119.5B)
│   ├── [Overige 13 categorieën]
├── Right Panel: Inkomsten Display
│   ├── Loon- en inkomstenbelasting (€110.3B)
│   ├── [Overige inkomstenbronnen]
└── Footer: Export PDF + Info
```

#### 6.2 Visual Design Elements
- **Kleurenschema:** Nederlands overheidsthema (oranje/blauw accenten)
- **Typography:** Moderne, leesbare sans-serif (bijv. Inter, Roboto)
- **Weegschaal:** Centrale visuele metafoor met real-time kanteling
- **Sliders:** Custom styled met category icons
- **Feedback:** Kleurgecodeerd (rood/geel/groen) met smooth transitions

#### 6.3 Responsive Behavior
- **Desktop (>1024px):** Side-by-side layout
- **Tablet (768-1024px):** Gestapelde layout met behoud van weegschaal
- **Mobile (<768px):** Verticale stack, compact sliders, tap-friendly controls

### 7. User Experience Flow

#### 7.1 Onboarding
1. Welcome screen met korte uitleg (30 sec)
2. "Quick Tour" van de interface
3. Start met originele begroting als baseline

#### 7.2 Core Interaction Loop
1. Student past uitgavenslider aan
2. Weegschaal en totalen updaten real-time
3. Visuele feedback (kleuren/animaties)
4. Herhaal voor verschillende categorieën
5. Bekijk impact via visualisaties
6. Export naar PDF wanneer tevreden

#### 7.3 Export Flow
1. "Export PDF" button
2. Preview van rapport
3. Optie voor notities/naam
4. Download gegenereerde PDF

### 8. Content & Data Structure

#### 8.1 Budget Categories (Uitgaven)
```json
{
  "uitgaven": [
    {
      "id": "sociale_zekerheid",
      "naam": "Sociale Zekerheid en Arbeidsmarkt",
      "bedrag": 124.7,
      "icon": "users",
      "beschrijving": "Uitkeringen, pensioenen, arbeidsmarktbeleid"
    },
    // ... overige 14 categorieën
  ],
  "inkomsten": [
    {
      "id": "loon_inkomsten",
      "naam": "Loon- en inkomstenbelasting",
      "bedrag": 110.3,
      "icon": "briefcase"
    },
    // ... overige inkomstenbronnen
  ]
}
```

#### 8.2 PDF Report Template
- Header: "Mijn Ideale Rijksbegroting"
- Studentnaam/datum
- Vergelijking origineel vs. aangepast
- Top 3 wijzigingen
- Balans overzicht
- Footer: Gegenereerd door Budget Balancer

### 9. Implementation Phases

#### Phase 1 (MVP - Week 1-2)
- Basic layout en responsive design
- Core slider functionaliteit
- Eenvoudige weegschaal visualisatie
- PDF export basis

#### Phase 2 (Enhanced - Week 3)
- Verbeterde visualisaties (budget-klok)
- Animaties en transitions
- Local storage implementatie
- Cross-browser testing

#### Phase 3 (Polish - Week 4)
- Performance optimalisatie
- Accessibility verbetering
- Advanced PDF features
- User testing en feedback verwerking

### 10. Success Criteria

**Launch Ready When:**
- Alle 15 budgetcategorieën volledig functioneel
- Responsive design werkt op alle target devices
- PDF export produceert bruikbare rapporten
- Laadtijd < 3 seconden op gemiddelde connectie
- User testing toont >4.0 satisfaction score

**Educational Goals Met When:**
- Studenten kunnen binnen 10 minuten een volledige begroting maken
- Begrip van trade-offs tussen beleidskeuzes is verbeterd
- Docenten rapporteren verhoogde engagement in lessen over overheidsfinanciën

### 11. Risks & Mitigations

**Technical Risks:**
- Browser compatibiliteit → Extensive testing plan
- Performance op mobile devices → Lightweight libraries
- PDF generation complexity → Fallback naar simple text export

**Educational Risks:**
- Te complex voor doelgroep → User testing met studenten
- Niet aligned met curriculum → Feedback loop met docenten
- Data wordt snel outdated → Modulaire data structure

---

**Document Owner:** Product Manager  
**Last Updated:** [Huidige datum]  
**Version:** 1.0  
**Review Date:** [Review datum]