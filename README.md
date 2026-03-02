# Projekt: E-Commerce Datenmodellierung

Professionelle Datenbanklösung zur Ablösung heterogener Datenquellen durch ein zentrales MySQL-System (Greenfield-Ansatz).

## Übersicht
* **Kernprozess:** Kunde → Bestellung → Zahlung
* **Stack:** MySQL 9.6.0, dbdiagram.io
* **Methodik:** Phasenbasiertes Vorgehen (3. Normalform, Refactoring, Automatisierung)

---

## Architektur & Design

### Datenmodell (ER-Diagramm)
Das Modell sichert durch die konsequente Einhaltung der **3. Normalform (3NF)** maximale Datenintegrität und minimiert Redundanzen. 

![ER-Diagramm](ER_Diagramm.png)  
*(Hinweis: Visualisierung der Tabellenbeziehungen und Constraints.)*

* **Kunde (1:n) Bestellung:** Abbildung der Kundenhistorie.
* **Bestellung (1:n) Positionen:** Auflösung der n:m Beziehung zwischen Bestellung und Produkt.
* **Zahlung (1:1) Bestellung:** Eindeutige Zuordnung via `UNIQUE-Constraint` zur Sicherung der Geschäftslogik.

### Highlights
* **Trigger:** Automatische Synchronisation des Bestellstatus bei Änderung des Zahlungsstatus.
* **Integrität:** Einsatz von `FOREIGN KEY` Constraints (`RESTRICT`/`CASCADE`) zur Absicherung der Datenbeziehungen.
* **BI-Views:** Vordefinierte Analyse-Views für Kundenumsätze und Prozess-Monitoring.

---

## Implementierungs-Phasen
1.  **Phase 2: Basis-Schema:** Definition der Tabellenstruktur, Datentypen und initiale Befüllung mit Testdaten (Seed-Daten).
2.  **Phase 3: Optimierung & Finalisierung:**
    * **Refactoring:** Migration der Status-Felder auf präzise ENUM-Werte.
    * **Automatisierung:** Implementierung der Trigger-Logik für autonome Prozessabläufe.
    * **Validierung:** Durchführung systematischer Funktionstests zur Verifizierung der Trigger-Aktionen.

---

## Installation & Nutzung

1. **Repository klonen**
   ```bash
   git clone https://github.com/eviwalkowsky/Projekt-Datenmodellierung.git

2. **In das Verzeichnis wechseln**
   ```bash
   cd Projekt-Datenmodellierung

3. **Datenbank und Tabellen importieren**
   ```bash
   mysql -u root -p < Export-File
   
4. **In My-SQL einloggen**
   ```bash
   mysql -u root -p



Autor: Evi Walkowsky | Matrikelnummer: 42304897

Modul: Projekt: Datenmodellierung (DLBWIPDM01)

Status: Abgeschlossen (Februar 2026)

