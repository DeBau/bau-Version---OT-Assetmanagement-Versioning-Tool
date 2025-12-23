# Benutzerhandbuch: Anwendung des Security-Moduls (IEC 62443 Workflow) – Schritt für Schritt

## 1) Was Sie am Ende erhalten
Nach Durchführung der Schritte haben Sie:
- ein **Zonenmodell** für ein OT-System (IACS) inkl. Conduits
- ein **SUC** mit versioniertem Audit-Snapshot (**Asset-Scope** + **ZoneSet_in_scope** + **ConduitSet_in_scope** + optional **NeighborZones/Boundary-Conduits** als Kontext)
- Risikoanalyse (inhärent/residual), SL-T/SL-A, SPS Controls, Evidence und SPR-Auswertung


## 2) Voraussetzungen (vor dem Start)
Stellen Sie sicher, dass folgende Stammdaten vorhanden sind (über Ihre anderen Wizards):

### Equipment (EUC)
- Werk 1 → Bereich Verpackung → **Linie IL73** → Maschine „Rundtakttisch“

### OT-System (IACS)
- **„IL73 Control System“** (funktionale Einheit der Automatisierung)
  - PLC-System (S7-1500)
  - HMI-System (WinCC Panel / IPC)
  - Industrial Switch (Profinet/SCALANCE)
  - Drives/IO (Profinet)
  - Engineering Access (Service-Laptop/Engineering Station)
  - Anbindung an OT-Services (Historian/Recipe/SCADA Gateway)
  - Remote Access über DMZ (Jump Host/Vendor Gateway)

### Assets (Beispiel)
- **A1:** PLC S7-1500  
- **A2:** HMI Panel/IPC  
- **A3:** Switch IL73  
- **A4:** Drive/IO-Knoten (optional als Gruppe)  
- **A5:** Engineering Station (oder Service-Laptop)  
- **A6:** OT-Services Server (Recipe/Historian Connector)  
- **A7:** Jump Host in OT-DMZ (Remote Access)  
- **A8:** Firewall / Industrial Security Appliance (falls vorhanden)

### Zuordnung (Stammdaten)
- Assets → Equipment (physisch: IL73)  
- Assets → OT-System („IL73 Control System“)  
- Assets → Location/Organisation/Prozess (z. B. „Packaging“, Instandhaltung, Schichtbetrieb)  
- Assets → Netzwerk (IP/VLAN/Subnet/Ports/Kommunikationsbeziehungen)  
- Assets → Zonen (falls bereits vorhanden) bzw. später im SUC persistiert


### Pflicht
- **Assets** mit **Asset-Typ** (PLC/HMI/Switch/Server/Jump Host/Engineering …)
- **Equipment (EUC)** Struktur (Linie/Anlage/Maschine)
- **OT-System (IACS)** und Zuordnung der Assets zum IACS
- **Organisationen** mit Rollen + User-Zuordnung
- **Locations** (Site → Area → Room → optional Schaltschrank)
- **Netzwerke** (als Objekte) und – wenn verfügbar – Asset ↔ Netzwerk Zuordnung


### Optional (für bessere Auto-Vorschläge)
- Kommunikationsbeziehungen/Ports/Flows
- Hinweise zu Remote Access (DMZ/Jump Host)
- Prozesskritikalität/Prozesszuordnung


## 3) Navigation: Die zwei Haupt-Workflows

### Workflow A: System zonieren (Architecture)
1. OT-System (IACS) öffnen
2. Zonen & Conduits erstellen (manuell oder per Vorschlag)
3. Zonenmodell speichern und versionieren

### Workflow B: SUC erstellen (Assessment)
1. SUC anlegen
2. Assets in Scope aufnehmen (Include/Exclude)
3. Zonen/Conduits im SUC **ableiten und persistieren** (ZoneSet_in_scope + ConduitSet_in_scope + NeighborZones)
4. Risiken, SL-T, SPS, Evidence, SL-A, SPR
5. SUC-Version freigeben (Audit-Snapshot)

> Wichtig: Zonierung ist **vor** dem SUC ein eigenes Thema. Das SUC **nutzt** Zonen/Conduits, er „erfindet“ sie nicht.

---

# Workflow A – System zonieren (Architecture Wizard)

## A1) OT-System (IACS) öffnen
1. Menü **OT-Systeme / IACS**
2. IACS auswählen (z. B. „IL73 Control System“)
3. Reiter **Architektur** oder **Zonenmodell** öffnen

**Prüfen Sie im IACS-Überblick:**
- „Assets im System“: plausibel?
- „Netzwerke“: vorhanden?
- „Locations/Orgas/Prozesse“: vorhanden (für spätere Plausibilitätschecks)?

## A2) Zonenmodell erstellen (Zonen anlegen)
1. Button **„Zonenmodell erstellen“** oder **„Neue Zone“**
2. Pro Zone folgende Felder ausfüllen:
   - **Name** (z. B. `Z-CELL-IL73`)
   - **Zone-Typ** (Cell/Area, OT-Services, OT-DMZ, Engineering …)
   - **Beschreibung/Zweck** (1–2 Sätze)

### Standard-Zonen (Empfehlung)
- Cell/Area (PLC/HMI/IO/Switch)
- OT-Services (Recipe/Historian/SCADA Connector)
- OT-DMZ (Jump Host / RA Gateway)
- Engineering (Engineering Station / Service Laptop)

## A3) Assets Zonen zuordnen
1. In der Zone: **„Assets hinzufügen“** (Multi-Select) oder Drag & Drop aus Asset-Liste
2. Wiederholen für alle Zonen

**Plausibilitäts-Check (UI-Hinweise):**
- Assets ohne Zone → „Unassigned“ Liste abarbeiten
- Switch/Firewall/Server ohne klare Rolle → markieren und bewusst zuordnen (Cell/Services/DMZ)

## A4) Conduits zwischen Zonen anlegen
1. Button **„Neuer Conduit“**
2. Endpunkte wählen: **Zone A ↔ Zone B**
3. Optional: Protokolle/Ports/Allowlist-Hinweise ergänzen

**Minimaler Conduit-Satz (Skeleton):**
- Cell ↔ Services
- Services ↔ DMZ
- DMZ ↔ External/IT/Remote
- Engineering ↔ Cell (sehr wichtig)

## A5) Zonenmodell speichern & versionieren
1. Button **„Speichern“**
2. Button **„Version erstellen“** (z. B. `IACS-Zonenmodell v1`)
3. Optional: Changelog-Kommentar („Erstaufnahme“, „DMZ ergänzt“, …)

**Ergebnis:** Ein IACS hat jetzt ein wiederverwendbares, versioniertes Zonenmodell.

---

# Workflow B – SUC erstellen (Assessment Wizard)

## B1) SUC anlegen
1. Menü **Assessments / SUC**
2. Button **„Neues SUC“**
3. Felder:
   - **SUC-Name** (z. B. `SUC-IL73-Control-System`)
   - **Site** (Werk 1)
   - **Beteiligte Organisationen** + Rollen
   - **Boundary-Optionen** (Remote Access, OT-Services, IT-Übergang …)
4. **Anlegen** / **Weiter**

## B2) Asset-Scope definieren (Include/Exclude)
1. Reiter **Scope**
2. Assets hinzufügen über:
   - Auswahl aus IACS („Assets aus System übernehmen“)
   - Filter nach Equipment/Location/Netzwerk/Asset-Typ
3. Pro Asset setzen:
   - **Include** (im Scope) oder **Exclude** (bewusst nicht im Scope)
   - optional Begründung bei Exclude

**Tipps:**
- Include: alle Assets, die Steuerung/Überwachung beeinflussen (PLC, HMI, Switch, IO/Drives, Engineering, OT-Services-Anbindung, DMZ/RA-Komponenten)
- Exclude: wirklich nur, wenn begründet (z. B. außerhalb der Betrachtung, „wird in anderem SUC behandelt“)

## B3) Zonen/Conduits im SUC ableiten und persistieren (Audit-Snapshot)
1. Reiter **Architektur im SUC** (oder „Zonen/Conduits“)
2. Button **„Zonenmodell auswählen“**
3. Quelle wählen:
   - IACS „IL73 Control System“
   - Zonenmodell-Version (z. B. v1)
4. Button **„Ableiten & übernehmen“** (oder „Übernehmen“)

**Regel (SUC-Scoping):**
- **ZoneSet_in_scope** = alle Zonen, in denen **inkludierte** Assets liegen
- **ConduitSet_in_scope** = alle Conduits **zwischen** Zonen aus ZoneSet_in_scope
- **NeighborZones (Kontext)** = Zonen, die über Conduits an ZoneSet_in_scope angebunden sind (Boundary/Exposure)
- Alle anderen Zonen/Conduits aus dem IACS-Zonenmodell sind für diesen SUC **nicht relevant** und werden nicht bewertet.

**Wenn Assets im Scope nicht zuordenbar sind:**
- UI zeigt „Unassigned Assets“ → Zurück in Workflow A oder im SUC eine klare Zuordnung wählen (je nach Ihrer Policy).

## B4) Risiken erfassen (Zone/Conduit verknüpft)
1. Reiter **Risikoanalyse**
2. Button **„Neues Risk Item“** oder **„Aus Template“**
3. Felder:
   - Titel
   - Szenario (kurz)
   - **Scope-Objekt**: Zone oder Conduit auswählen
   - Impact / Likelihood
   - Treatment (Mitigate/Accept/Transfer/Avoid)

**Regel für Anwender (einfach, passend zu Asset-Scope):**
- Technische/komponentenbezogene Risiken → Asset (primär)
- (z. B. Patchstand, Accounts, Hardening, Backup/Restore, lokale Konfiguration)
- Übergangs-/Kommunikationsrisiken → Conduit
- (z. B. Remote Access, erlaubte Ports/Protokolle, Segmentierung, Datenflusskontrolle)
- Bereichs-/Zellenrisiken → Zone
- (z. B. Cell-Netz-Stabilität/DoS, gemeinsame Betriebsprozesse, gemeinsame Schutzbedarfe)
- SUC verknüpft beides: Asset-Risiken bleiben führend, Zone/Conduit dienen der Aggregation (SL-T/Controls/Boundary) und Auswertung (SPR).


## B5) SL-T (Target) pro Zone/Conduit setzen
1. Reiter **Security Level**
2. Für jede Zone/Conduit-Karte:
   - SL-T setzen (z. B. 2 oder 3)
   - Rationale: Verweis auf Risk Items (Dropdown/Link)

## B6) SPS Controls anwenden (Controls + Tracking)
1. Reiter **SPS / Controls**
2. Button **„Controls anwenden“**:
   - Auswahl: Zone/Conduit-Templates (DMZ, Cell, Engineering, Services)
   - Auswahl: Asset-Templates (PLC, HMI/Windows, Switch, Jump Host)
3. Controls prüfen, ggf. anpassen
4. Pro Control:
   - Status: **Implemented / Verified / Operated**
   - Verantwortliche Rolle/Organisation (falls vorgesehen)
   - Verknüpfen mit Risk Items (Traceability)

## B7) Evidence erfassen (Nachweise hochladen/verlinken)
1. In einem Control die Sektion **Evidence**
2. Evidence hinzufügen:
   - Datei/Upload (Rule Export, Config Dump, Protokoll)
   - Link/Referenz (Ticket, Change-Record, Monitoring-Auszug)
   - Datum + Reviewer

**Empfohlene Minimal-Evidence (Beispiele):**
- Firewall/ACL: Rule Export + Review-Protokoll
- Backup/Restore: Restore-Test-Protokoll
- Accounts: User-Review-Protokoll (periodisch)
- Switch: Config Dump/Portstatus

## B8) SL-A bewerten (Achieved) & Gaps
1. Reiter **SL-A / Gap**
2. Pro Zone/Conduit:
   - SL-A setzen (evidence-gestützt)
3. Tool zeigt automatisch:
   - Gap: SL-T vs SL-A
   - offene Controls/Risiken, die den Gap treiben




## B9) SPR anzeigen (Reporting)
1. Reiter **SPR / Dashboard**
2. Anzeigen:
   - SPR-I / SPR-V / SPR-O pro Zone/Conduit
   - Roll-up auf IACS und Equipment (falls konfiguriert)
3. Export (PDF/CSV) falls vorhanden

## B10) SUC-Version freigeben (Audit-Snapshot)
1. Button **„SUC-Version erstellen“** oder **„Freigeben“**
2. Kommentar (was wurde geändert / warum)
3. Ergebnis: SUC v1 ist **auditierbar** gespeichert (Scope + Zonen/Conduits + Risk/SL/SPS/Evidence/SPR)

---

## 4) Walkthrough am Beispiel „IL73“ (kompakt)

### A) Zonierung im IACS
- Z-CELL-IL73: A1, A2, A3, A4
- Z-OT-SERVICES: A6
- Z-OT-DMZ: A7, A8
- Z-ENG-IL73: A5
- (Optional) Z-IT als External/Neighbor-Zone
Conduits:
- C1 Cell↔Services
- C2 Services↔DMZ
- C3 DMZ↔External (Z-IT/Remote)
- C0 ENG↔Cell
- optional C4 DMZ↔ENG

### B) SUC
- SUC-IL73-Control-System erstellen
- Assets includen (A1–A8)
- Zonenmodell v1 auswählen
- SUC leitet automatisch ab:
  - ZoneSet_in_scope = Zonen der inkludierten Assets
  - ConduitSet_in_scope = Conduits zwischen In-Scope-Zonen
  - NeighborZones = angebundene Zonen als Kontext (z. B. External/IT)
- Risk Items anlegen (R1…R4)
- SL-T setzen (z. B. Cell=3, DMZ=3, ENG=3, Services=2–3; Conduits entsprechend)
- SPS Templates anwenden, Evidence pflegen
- SL-A bewerten, SPR prüfen
- SUC v1 freigeben


---

## 6) Checklisten (für Anwender)

### Checklist: Zonierung fertig?
- [ ] Alle System-Assets sind einer Zone zugeordnet
- [ ] Zonenmodell versioniert gespeichert

### Checklist: SUC auditfähig?
- [ ] Asset-Scope (Include/Exclude) vollständig
- [ ] ZoneSet_in_scope + ConduitSet_in_scope (und NeighborZones/Boundary-Conduits, falls vorhanden) im SUC persistiert
- [ ] Risk Items verknüpft (Zone/Conduit)
- [ ] SL-T gesetzt und begründet
- [ ] SPS Controls angewendet + Traceability zu Risiken
- [ ] Evidence vorhanden (mindestens für kritische Controls)
- [ ] SL-A bewertet, Gaps dokumentiert
- [ ] SPR plausibel
- [ ] SUC-Version freigegeben

---
