# Power BI Product- en Verkoopanalyse en KPI Dashboard

Het **KPI Dashboard** biedt inzicht in product- en verkoopanalyse gebaseerd op dummy data waarin een onderscheid wordt gemaakt tussen **Producten** en **Diensten**.   Met interactieve visualisaties helpt dit dashboard inzicht te geven in **KPI** schommelingen over een tijdspanne van 2 maanden.

---

## 📁 Datasetstructuur

Het Excel-bestand bevat de volgende tabellen:

- **Verkooptransacties**: feitentabel met verkoopdata
- **Producten**: productinformatie inclusief kostprijs en categorie
- **Klanten**: klantgegevens met locatie en segment
- **Datum**: datumdimensie met jaar, maand, weeknummer
- **DAX_Measures**: vooraf gedefinieerde DAX-measures en calculated columns

---

### 🔗 Relaties in het datamodel

- `Verkooptransacties[ProductID]` → `Producten[ProductID]`
- `Verkooptransacties[KlantID]` → `Klanten[KlantID]`
- `Verkooptransacties[Datum]` → `Datum[Datum]`

Deze relaties vormen een stermodel met `Verkooptransacties` als centrale feitentabel.

---

## 📊 Dashboardcomponenten

---

### 🧮 KPI-kaarten
- **Totale omzet**
- **Totale winst**
- **Winstmarge (%)**
- **Aantal actieve producten**
- ⚠️ Negatieve winst en marge signaleren mogelijke prijs- of kostproblemen

---

### 🏆 Top 10 producten per omzet
- SEO Optimalisatie is het best presterende product (€946,22)
- Andere toppers: Laptop, Printer, Consulting Uur, Website Ontwikkeling
- Ondersteunt beslissingen rond productfocus en marketing

---

### 📈 Verkoop per maand
- Lijnchart toont maandelijkse verkoop (bv. januari: €1.751,43)
- Groene kleur benadrukt groei
- Jaarfilter aanbevolen voor seizoensanalyse

---

### 👥 Verkoop per klantsegment
- Segmenten: Dienstverlening, B2B, Retail, Gezondheid
- Helpt bij gerichte marketing en prijsstrategieën
- Interactieve slicers voor segmentanalyse

---

### 📉 Winstmarge per productcategorie
- Zowel 'Dienst' als 'Product' tonen verlies
- Ondersteunt prijsaanpassingen, kostenreductie of productstopzetting

---

## 🧠 DAX-measures

Voorbeelden uit het tabblad `DAX_Measures`:

- `Totale Omzet = SUM(Verkooptransacties[TotaleWaarde])`
- `Totale Winst = SUMX(Verkooptransacties, (Verkooptransacties[Verkoopprijs] - RELATED(Producten[Kostprijs])) * Verkooptransacties[Aantal])`
- `Winstmarge % = DIVIDE([Totale Winst], [Totale Omzet], 0)`
- `Omzet per Maand = CALCULATE([Totale Omzet], ALLEXCEPT(Datum, Datum[MaandNaam]))`
- `Omzet per Segment = CALCULATE([Totale Omzet], ALLEXCEPT(Klanten, Klanten[Segment]))`

---

## 🛠 Gebruik in Power BI

- Bouw een stermodel met de opgegeven relaties
- Implementeer KPI-kaarten en grafieken zoals beschreven
- Gebruik slicers voor segment- en tijdsanalyses
- Optimaliseer DAX-formules voor performance en inzicht

---

## 👤 Auteur & Contact
**Naam:** Raf Wuytjens  
**E-mail:** [raf@itdevops.be](mailto:raf@itdevops.be)  
**Versie:** 1.0  

---

### 🕓 Versiegeschiedenis
| Versie | Datum | Wijziging |
|--------|--------|------------|
| **1.0** | Okt 2025 | Eerste release |

---

© 2025 Raf Wuytjens – *ITDEVOPS bv*
