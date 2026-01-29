# bauVision OT-VAM
## OT Asset Management & Versioning System

---

## Was ist bauVision OT-VAM?

**bauVision OT-VAM** (Operational Technology - Versioning & Asset Management) ist ein **vollständiges OT Asset Management und Versionierungssystem** für industrielle Produktionsumgebungen mit integrierter IEC 62443 Security Compliance.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           bauVision OT-VAM                                  │
│         "OT Asset Management & Versioning for Industrial Production"        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ASSET MANAGEMENT          VERSIONING              SECURITY                │
│   ─────────────────         ──────────              ────────                │
│   • Standorte               • Check-In/Out          • IEC 62443 Zones       │
│   • Organisationen          • 21 CFR Part 11        • SL Assessment         │
│   • Prozesse                • 4-Augen-Prinzip       • Gap Analysis          │
│   • Equipment               • E-Signatur            • Incident Response     │
│   • OT-Assets               • 50+ OT-Dateitypen     • NIS2 Compliance       │
│   • Netzwerke               • Diff-Ansicht          • Vulnerability Mgmt    │
│   • Systeme                 • Auto-Backup           • Quality Gates         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

# STAMMDATEN - Was wird verwaltet?

---

## 1. STANDORTE (Locations)

**Standort-Hierarchie für physische Strukturen**

```
Enterprise
  └── Site (Werk)
       └── Area (Bereich)
            └── Cell (Zelle)
                 └── Unit (Einheit)
```
<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">




### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **ISA-95 Hierarchie** | Enterprise → Site → Area → Cell → Unit |
| **Automatische Pfadberechnung** | /Enterprise/Site/Area/Cell |
| **Standort-Typen** | Werk, Gebäude, Etage, Raum, Bereich |
| **GPS-Koordinaten** | Optional für Geo-Mapping |
| **Lagepläne** | Floor Plans mit Upload |
| **Beziehungen** | Assets, Equipment, Organisationen, Netzwerke, Zonen |
| **Breadcrumbs** | Vollständige Hierarchie-Navigation |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Zuständigkeiten** | Verantwortliche Organisationen pro Standort |
| **Wartungszonen** | Gruppierung für Wartungsplanung |

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Zonen-Zuordnung** | Security Zones pro Standort |
| **Zugangskontrollen** | Physische Sicherheit dokumentiert |
| **Audit Trail** | Änderungshistorie |

---

## 2. ORGANISATIONEN (Organizations)

**Unternehmensstruktur und Verantwortlichkeiten**

```
Enterprise
  └── Division (Geschäftsbereich)
       └── Department (Abteilung)
            └── Team
                 └── Role
```
<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">

### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Hierarchie** | Enterprise → Division → Department → Team |
| **Automatische Pfadberechnung** | /Enterprise/Division/Department |
| **Cycle Detection** | Verhindert zirkuläre Hierarchien |
| **Beziehungen** | Standorte, Assets, Equipment, Prozesse, Netzwerke, Zonen |
| **Optimistic Locking** | Sichere parallele Bearbeitung |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Wartungsteams** | Zuordnung zu Equipment |
| **Eskalationspfade** | Hierarchische Eskalation |
| **Schichtmodelle** | Team-Zuordnungen |

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Zonen-Verantwortung** | Security Owner pro Zone |
| **Incident Response** | Zuständige Teams |
| **Berechtigungen** | Tenant-basierte Zugriffskontrolle |

---

## 3. PROZESSE (Processes)

**Industrielle Fertigungsprozesse und Abläufe**

```
Hauptprozess
  └── Teilprozess 1
       └── Arbeitsschritt 1.1
       └── Arbeitsschritt 1.2
  └── Teilprozess 2
```

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Hierarchie** | Parent-Child Prozessstruktur |
| **Prozess-Typen** | Production, Support, Quality, Safety |
| **Kritikalität** | Safety-Critical, Quality-Critical, Normal |
| **Prozessfluss** | Visuelle Darstellung mit React Flow |
| **Flow Connections** | Prozess-Verbindungen (Edges) |
| **Flow Layout** | Node-Positionen speicherbar |
| **Beziehungen** | Standorte, Equipment, Assets, Organisationen |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Prozess-Equipment** | Welche Anlagen für welchen Prozess |
| **Ausfallauswirkung** | Cascade-Effekte bei Störung |
| **Prozess-Dokumentation** | Verlinkte Runbooks |




### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **BIA Integration** | Business Impact pro Prozess |
| **Zonen-Mapping** | Welche Zonen unterstützen welchen Prozess |
| **Incident Impact** | Prozessauswirkung bei Incidents |


<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


---

## 4. NETZWERKE (Networks)

**OT-Netzwerk-Infrastruktur**

### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Netzwerk-Typen** | Ethernet, Serial, Wireless, Fieldbus |
| **IP-Konfiguration** | CIDR, Gateway, DNS, NTP |
| **VLAN Management** | VLAN-ID Verwaltung |
| **Protokolle** | OPC UA, Modbus, EtherNet/IP, PROFINET, etc. |
| **Bandbreite** | Konfigurierte/Genutzte Bandbreite |
| **Redundanz** | Ring, Mesh, Dual-Star, Single-Point-of-Failure |
| **Purdue Level** | 0-5 Klassifizierung |
| **Beziehungen** | Standorte, Systeme, Assets, Zonen |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Completeness Score** | Datenqualitäts-Bewertung |
| **Dokumentation** | Netzpläne, Konfigurationen |
| **Change Tracking** | Änderungen mit Ticket-Referenz |
| **RTO/RPO** | Recovery Time/Point Objectives |

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Firewall Config** | Firewall-Konfiguration dokumentiert |
| **Air-Gapped** | Netzwerk-Isolation Flag |
| **Policy Exceptions** | Ausnahmen mit Ablaufdatum |
| **Security Zone** | Zuordnung zu Security Zones |
| **DPI/IDS** | Deep Packet Inspection, Intrusion Detection |

---

## 5. SYSTEME (IACS - Industrial Control Systems)

**Automatisierungssysteme und deren Hierarchie**

```
IACS-Gruppe (Logische Gruppierung)
  └── SCADA System
       └── PLC 1
       └── PLC 2
  └── HMI System
```

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">

### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **System-Typen** | SCADA, DCS, PLC, HMI, Historian, Engineering Workstation |
| **Hierarchie** | Parent-Child Systemstruktur |
| **IACS Groups** | Logische Gruppierung von Systemen |
| **Kommunikation** | System-zu-System Verbindungen |
| **Beziehungen** | Netzwerke, Standorte, Prozesse, Assets |
| **Safety System** | Sicherheitssystem-Flag |
| **Criticality** | Kritikalitätsstufe |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Equipment Import** | Equipment als Systeme importieren |
| **Asset-Zuordnung** | Welche Assets zu welchem System |

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Automatische Zone-Ableitung** | IACS Group → Security Zone |
| **Automatische Conduit-Ableitung** | System-Kommunikation → Conduits |
| **Zonen-Zuordnung** | System-to-Zone Mapping |
| **Conduit-Zuordnung** | System-to-Conduit Mapping |

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">

---

## 6. EQUIPMENT / ANLAGEN

**Physische Produktionsanlagen und Maschinen**

```
Plant (Anlage)
  └── Area (Bereich)
       └── Line (Linie)
            └── Machine (Maschine)
                 └── Anlage (Komponente)
```
<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Hierarchie** | Plant → Area → Line → Machine → Anlage (5 Ebenen) |
| **Equipment Code** | Eindeutige Kennzeichnung |
| **Hersteller-Daten** | Manufacturer, Model, Serial Number, Baujahr |
| **Criticality** | A, B, C Klassifizierung |
| **Safety Relevant** | Flag für sicherheitsrelevante Anlagen |
| **Beziehungen** | Standorte, Organisationen, Prozesse, Netzwerke, Zonen, Assets (alle N:M) |
| **Equipment Summary** | Aggregierte Übersicht aller Anlagen |

### LIFECYCLE MANAGEMENT (13 Status):
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      EQUIPMENT LIFECYCLE                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Planned → Ordered → Delivered → Installation → Commissioning → Active     │
│                                                         │                   │
│                                            ┌────────────┼────────────┐      │
│                                            ▼            ▼            ▼      │
│                                        Standby    Maintenance    Repair     │
│                                            │            │            │      │
│                                            └────────────┼────────────┘      │
│                                                         ▼                   │
│                                                     Inactive                │
│                                                         │                   │
│                                    Decommissioning ◄────┘                   │
│                                            │                                │
│                                    Decommissioned                           │
│                                            │                                │
│                                        Disposed                             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


| Feature | Beschreibung |
|---------|--------------|
| **Vollständige Historie** | Alle Statuswechsel mit Datum und User |
| **13 Lifecycle-Status** | Von Planung bis Entsorgung |
| **Notizen pro Wechsel** | Dokumentation der Statusänderung |
| **Audit Trail** | Wer hat wann was geändert |

### INSTANDHALTUNG-Features:

#### Elektrische Prüfungen (VDE/DGUV Vorschrift 3):
| Feature | Beschreibung |
|---------|--------------|
| **Prüfarten** | Erstprüfung, Wiederholungsprüfung, Änderungsprüfung |
| **Prüferqualifikation** | EFK, EFKffT, VEFK, Sachverständiger |
| **Angewandte Normen** | VDE 0100, VDE 0105, etc. (Array) |
| **Ergebnis** | Bestanden, Bestanden mit Auflagen, Nicht bestanden |
| **Mängelmanagement** | Befunde mit Behebungsstatus und Datum |
| **Prüfprotokolle** | Protokollnummer + Dateianhang |
| **Messwerte** | Iso-Widerstand, Schleifenimpedanz, RCD, etc. (JSONB) |
| **Nächster Termin** | Automatische Berechnung Folgeprüfung |

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


#### Prüfchecklisten (VDE-konform):
| Feature | Beschreibung |
|---------|--------------|
| **Standard-Prüfpunkte** | Nach VDE-Normen vordefiniert |
| **Kategorien** | Sichtprüfung, Erprobung, Messung |
| **Messanforderungen** | Messeinheit, Bestehungskriterium |
| **Einzelergebnisse** | Pro Prüfpunkt: passed/failed/not_applicable |
| **Gemessene Werte** | Dokumentation der Messwerte |
| **Eigene Prüfpunkte** | Custom Items ohne Stammreferenz |

#### Runbook System (OT Knowledge Management):
| Feature | Beschreibung |
|---------|--------------|
| **Entry Types** | Troubleshooting, Procedure, Checklist, Knowledge, How-to |
| **Severity** | Info, Warning, Critical |
| **Difficulty** | Easy, Medium, Hard, Expert |
| **Status** | Draft → Review → Published → Archived |
| **Problem/Lösung** | Symptoms, Solution, Prevention |
| **Sicherheitshinweise** | Safety Warnings integriert |
| **Zeitschätzung** | Geschätzte Dauer in Minuten |
| **Benötigte Tools** | Required Tools (JSONB) |
| **Berechtigungen** | Required Permissions (JSONB) |
| **Steps** | Schritt-für-Schritt Anleitungen |
| **Versioning** | Version + History pro Eintrag |
| **Comments** | Diskussionen und Feedback |
| **Statistiken** | Views Count, Helpful Count |
| **Attachments** | Dateien anhängen |

<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Zone-Zuordnung** | Security Zone pro Equipment (N:M) |
| **BIA** | Business Impact Assessment (1:1) |
| **Incident Linking** | Betroffenes Equipment bei Incidents |

### FUNCTIONAL SAFETY (IEC 61508 / ISO 13849 / IEC 62061):

#### Safety Classification (1:1 pro Equipment):
| Feature | Beschreibung |
|---------|--------------|
| **SIL Required/Achieved** | SIL 1-4 nach IEC 61508/61511 |
| **PL Required/Achieved** | PL a-e nach ISO 13849 |
| **Category** | B, 1, 2, 3, 4 nach ISO 13849 |
| **SILCL** | IEC 62061 Klassifizierung |
| **Safety Function** | Beschreibung der Sicherheitsfunktion |
| **Assessment Schedule** | Intervall + letzte/nächste Prüfung |
| **Proof Test Schedule** | Intervall + letzte/nächste Prüfung |


<img src="https://github.com/DeBau/bau-Version---OT-Assetmanagement-Versioning-Tool/blob/main/images/agent.png" alt="Agent" width="600">


#### Safety Assessments (Risikobeurteilung):
| Feature | Beschreibung |
|---------|--------------|
| **Assessment Type** | Art der Bewertung |
| **Risk Graph Inputs** | Severity, Frequency, Probability |
| **Hazard Type** | Art der Gefährdung |
| **Hazard Description** | Beschreibung der Gefährdung |
| **Calculated SIL/PL** | Berechnetes Sicherheitsniveau |
| **Risk Level** | Ermitteltes Risikoniveau |
| **Safety Function** | Definierte Sicherheitsfunktion |
| **Mitigation Measures** | Risikominimierungsmaßnahmen |
| **Residual Risk** | Dokumentiertes Restrisiko |
| **Approval Workflow** | Draft → Assessed → Approved/Rejected |
| **Assessed By / Approved By** | Mit User-Referenz |

#### Safety Components (N:M mit Assets):
| Feature | Beschreibung |
|---------|--------------|
| **Component Type** | Safety-PLC, Not-Aus, Lichtvorhang, Safety-Relay, Scanner, etc. |
| **Component Function** | Beschreibung der Sicherheitsfunktion |
| **SIL/PL Capability** | Fähigkeit der Komponente |
| **Zertifizierung** | Zertifizierungsstelle (TÜV, Dekra, etc.) |
| **Zertifizierungsnummer** | Eindeutige Referenz |
| **Zertifizierungsstandard** | IEC 61508, ISO 13849, etc. |
| **Gültigkeitsdatum** | Valid Until |

---

## 7. ASSETS (OT-Assets)

**Software, Firmware, Konfigurationen auf Equipment**

### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Asset-Typen** | Software, Firmware, Configuration, License |
| **Hierarchie** | Parent-Child Asset-Struktur |
| **Software Catalog** | Zentrale Software-Verwaltung |
| **Telemetrie** | Asset-Telemetriedaten |
| **Beziehungen** | Equipment, Standorte, Organisationen, Prozesse, Netzwerke, Zonen |
| **Enriched View** | ISA-95 Breadcrumbs, Relationship Counts |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Software Updates** | Update-Tracking |
| **Lizenzen** | Lizenzverwaltung mit Ablaufdatum |
| **Lifecycle (SLC)** | Software Lifecycle Status |
| **Security Config** | Sicherheitsparameter |

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Risk Scenarios** | Asset-spezifische Risikoszenarien |
| **CVE Matching** | Automatische Vulnerability-Korrelation |
| **Zone-Vererbung** | Zone von übergeordnetem Asset/Equipment |

---

## 8. ZONEN (Security Zones - IEC 62443)

**Sicherheitszonen nach IEC 62443-3-2**

```
┌──────────────────────────────────────────────────────────────────────┐
│                        SECURITY ZONES                                │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   Enterprise Zone (Level 5)                                          │
│        │                                                             │
│   DMZ (Level 3.5)    ◄─── Conduit ───►   Enterprise Zone             │
│        │                                                             │
│   Supervisory Zone (Level 3)                                         │
│        │                                                             │
│   Control Zone (Level 2)                                             │
│        │                                                             │
│   Process Zone (Level 1)                                             │
│        │                                                             │
│   Safety Zone (Level 0)                                              │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Zone-Typen** | Process, Safety, Control, Supervisory, Manufacturing, Enterprise, DMZ |
| **Purdue Level** | 0-5 Klassifizierung |
| **Hierarchie** | Parent-Child Zone-Struktur |
| **Beziehungen** | Systeme, Netzwerke, Assets, Standorte, Organisationen |
| **React Flow** | Visuelle Zone-Diagramme |
| **Auto-Ableitung** | Automatisch aus IACS-Gruppen |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Zone Dashboard** | Statistiken und Übersicht |
| **Completeness** | Vollständigkeits-Score |

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **SL-Target (SL-T)** | Ziel-Security-Level pro FR1-FR7 |
| **SL-Achieved (SL-A)** | Erreichtes Security-Level |
| **FR-Vector** | Functional Requirement Bewertung |
| **Gap Analysis** | SL-T minus SL-A |
| **Business Criticality** | Low, Medium, High, Critical |
| **Safety Relevance** | Sicherheitsrelevanz-Flag |
| **Physical Security** | Zugangskontrollen dokumentiert |
| **Assessment History** | Audit Trail aller Bewertungen |

---

## 9. CONDUITS (Zone-Verbindungen)

**Kontrollierte Übergänge zwischen Security Zones**

### TECHNIK-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Conduit-Typen** | Firewall, Data Diode, VPN, DMZ, Proxy, Router, Direct |
| **Source/Target Zone** | Von-Zone → Nach-Zone |
| **Protokolle** | Erlaubte Protokolle |
| **Ports** | Erlaubte Ports |
| **Auto-Ableitung** | Automatisch aus System-Kommunikation |

### INSTANDHALTUNG-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Dokumentation** | Konfigurationsdokumentation |
| **Change Tracking** | Änderungshistorie |

### SECURITY-Features:
| Feature | Beschreibung |
|---------|--------------|
| **Firewall Rules** | Firewall-Regeln dokumentiert |
| **Encryption** | Verschlüsselung aktiviert |
| **DPI** | Deep Packet Inspection |
| **Protocol Validation** | OPC UA Security, etc. |
| **IDS/IPS** | Intrusion Detection/Prevention |
| **Approval Workflow** | Genehmigungsprozess |
| **SL Assessment** | Conduit-spezifisches SL |
| **Compensating Controls** | Kompensierende Maßnahmen |

---

# TEIL 2: VERSIONING SYSTEM

---

## ASSET VERSIONING (21 CFR Part 11 konform)

**Vollständige Versionskontrolle für OT-Dateien mit elektronischer Signatur**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         VERSION CONTROL WORKFLOW                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Check-Out  ──►  Bearbeitung  ──►  Check-In  ──►  Signatur  ──►  Approval  │
│       │               │               │              │              │       │
│   Lock Asset     Edit Files      Upload v1.2.3   Sign Hash    4-Augen       │
│   (Exclusive)    (Offline)       (SHA-256)       (Password)   (Review)      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### OT-spezifische Dateitypen (50+):

| Kategorie | Dateitypen |
|-----------|------------|
| **PLC Programming** | PLC Program, Multiproject, Library, Block, Safety Program, UDT, Function |
| **HMI/SCADA** | HMI Project, Screen, Script, Template, Symbol Library |
| **Motion Control** | Drive Parameters, Motion Cam, CNC Program, Axis Config |
| **Robotics** | Robot Program, Cell Config, Tool Config, Path Program |
| **Network Config** | Network Config, Firewall Config, Switch Config, Fieldbus Config |
| **Sensors** | Vision Project, Sensor Config, Camera Config |
| **Process Control** | Recipe, Process Parameters, Batch Config |
| **Documentation** | Electrical Schema, Documentation, Manual |
| **System** | System Image, Firmware, Project Archive, Backup |

### 21 CFR Part 11 Compliance:

| Feature | Beschreibung |
|---------|--------------|
| **Elektronische Signatur** | SHA-256 Hash mit Passwort-Verifikation |
| **Unveränderlichkeit** | Signierte Versionen sind unveränderbar |
| **Audit Trail** | Vollständiges Logging: User, IP, Timestamp, Action |
| **4-Augen-Prinzip** | Approval Workflow mit separatem Reviewer |
| **Signaturgrund** | Reason for Signature dokumentiert |
| **Rejection Workflow** | Ablehnung mit Kommentar |

### Zusätzliche Versioning-Features:

| Feature | Beschreibung |
|---------|--------------|
| **Check-Out Locking** | Exklusiver Zugriff mit Ablaufzeit |
| **Force Release** | Admin-Override für Locks |
| **Diff-Ansicht** | Unified Diff zwischen Versionen |
| **Version Tree** | Hierarchische Versionsdarstellung |
| **Timeline View** | Kombinierte Version + Audit Events |
| **Tags** | Bis zu 20 Tags pro Version |
| **Ticket-Referenz** | Verlinkung zu Ticket-System |
| **Change Types** | Feature, Bugfix, Config, Backup, Initial |
| **Auto-Backup** | Konfigurierbare Backup-Intervalle |
| **Retention Policy** | Aufbewahrungsfristen |
| **Max Upload** | Bis zu 2 GB pro Datei |
| **Statistics Dashboard** | Versioning-Statistiken |

---

# TEIL 3: INSTANDHALTUNG (Maintenance)

---

## PRÜFUNGEN (VDE/DGUV Inspections)

**Elektrische Prüfungen nach VDE und DGUV Vorschrift 3**

| Feature | Beschreibung |
|---------|--------------|
| **Prüfarten** | Erstprüfung, Wiederholungsprüfung, Änderungsprüfung |
| **Prüfer-Qualifikation** | EFK, EFKffT, VEFK, Sachverständiger |
| **Prüfzyklen** | Konfigurierbare Intervalle |
| **Checklisten** | Konfigurierbare Prüfpunkte mit Messanforderungen |
| **Messwerte** | Iso-Widerstand, Schleifenimpedanz, RCD, etc. |
| **Mängelmanagement** | Befunde mit Schweregrad und Behebungsstatus |
| **Prüfprotokolle** | Vollständige PDF-Protokolle |
| **Nächster Termin** | Automatische Berechnung |
| **Erinnerungen** | Benachrichtigungen vor Fälligkeit |

---

## RUNBOOK SYSTEM (OT Knowledge Management)

**Strukturierte Anleitungen für OT-Personal**

| Feature | Beschreibung |
|---------|--------------|
| **Entry Types** | Troubleshooting, Procedure, Checklist, Knowledge, How-to |
| **Markdown** | Vollständige Markdown-Unterstützung |
| **Steps** | Schritt-für-Schritt mit Checkpoints |
| **Safety Warnings** | Sicherheitshinweise integriert |
| **Versioning** | Änderungshistorie pro Eintrag |
| **Comments** | Diskussionen und Feedback |
| **Voting** | Helpfulness-Bewertung |
| **Related Entries** | Related, Prerequisite, Follow-up |
| **Equipment-Link** | Runbooks pro Equipment |
| **Network-Link** | Runbooks pro Netzwerk |

---

## SOFTWARE CATALOG & UPDATES

**Zentrale OT-Software-Verwaltung**

| Feature | Beschreibung |
|---------|--------------|
| **Software Catalog** | Zentrale Software-Datenbank |
| **Update Packages** | JSON-basierte Update-Pakete |
| **Package Upload** | Direkter Datei-Upload |
| **Validation** | Paket-Validierung vor Installation |
| **Export** | Katalog-Export für Backup/Transfer |
| **Update History** | Vollständige Update-Historie |
| **Version Tracking** | Katalog-Versionierung |

---

# TEIL 4: SECURITY & COMPLIANCE

---

## SECURITY LEVEL ASSESSMENT (Vollständig anpassbar)

**Eigener Fragenkatalog kann entworfen werden!**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      CUSTOM SL ASSESSMENT ENGINE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   TEMPLATES          ──►   Eigene Assessment-Vorlagen erstellen             │
│   CATEGORIES         ──►   Eigene Kategorien definieren (FR1-FR7+)          │
│   QUESTIONS          ──►   Eigene Fragen formulieren                        │
│   RESPONSE TYPES     ──►   Multiple Choice, Skala, Text, etc.               │
│   SCORING LOGIC      ──►   Eigene Bewertungslogik                           │
│   TEMPLATE VERSIONS  ──►   Versionierung der Vorlagen                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Assessment-Typen:

| Assessment | Beschreibung | Anwendung |
|------------|--------------|-----------|
| **Risk Assessment** | Risikobewertung mit Q1-Q23 | Initiale Risikoermittlung |
| **SL-Target (SL-T)** | Ziel-Security-Level | FR1-FR7, Werte 0-4 |
| **SL-Achieved (SL-A)** | IST-Zustand | FR1-FR7, Werte 0-4 |

### Features:

| Feature | Beschreibung |
|---------|--------------|
| **Custom Templates** | Vollständig eigene Fragenkataloge |
| **Template Versioning** | Audit-Trail für Template-Änderungen |
| **Bulk Response** | Mehrere Antworten auf einmal |
| **FR-Vector** | Automatische Berechnung |
| **Gap Calculation** | SL-T minus SL-A |
| **Critical Gaps** | Automatisch bei Gap ≥ 2 |
| **Risk-based SL-T** | Empfehlung aus Risk Assessment |
| **Assessment Summary** | Übersicht pro Zone |

---

## GAP ANALYSIS

**Differenz zwischen Ziel und IST**

| Feature | Beschreibung |
|---------|--------------|
| **Gap Calculation** | SL-Target minus SL-Achieved pro FR |
| **Critical Gaps** | Automatische Markierung bei Gap ≥ 2 |
| **Priority** | Critical, High, Medium, Low |
| **Status** | Open → In Progress → Resolved |
| **Owner Assignment** | Verantwortlicher zuweisen |
| **Target Date** | Zieldatum für Behebung |
| **Remediation Plan** | Maßnahmenplan dokumentiert |
| **Root Cause** | Ursachenanalyse |
| **SUC Summary** | Aggregierte Gap-Übersicht |

---

## SECURITY PROTECTION SCHEME (SPS)

**Control Baselines nach IEC 62443-3-3**

| Feature | Beschreibung |
|---------|--------------|
| **Control Baselines** | Vordefinierte IEC 62443-3-3 Controls |
| **FR/SR Mapping** | Functional Requirement / Security Requirement |
| **Zone Controls** | Controls pro Zone |
| **Conduit Controls** | Controls pro Conduit |
| **Evidence** | Nachweis-Dateien anhängen |
| **Exceptions** | Ausnahmen mit Begründung |
| **Templates** | Wiederverwendbare Control-Sets |
| **SL Application** | Controls für SL1, SL2, SL3 |

---

## SECURITY PROTECTION RATING (SPR)

**Aggregierte Security-Bewertung**

| Feature | Beschreibung |
|---------|--------------|
| **Zone SPR** | Security Rating pro Zone |
| **Conduit SPR** | Security Rating pro Conduit |
| **SPR Snapshots** | Zeitpunktbezogene Aufnahmen |
| **Trend Analysis** | Entwicklung über Zeit |
| **SUC Rollup** | Aggregation auf SUC-Ebene |
| **History** | Historische Snapshots abrufbar |

---

## QUALITY GATES (G1-G10)

**IEC 62443-2-1 Meilensteine**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           QUALITY GATES                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ASSET GATES:    G1 ──────► G2                                             │
│                   Inventar   Klassifizierung                                │
│                                                                             │
│   SUC GATES:      G3 ──► G4 ──► G5 ──► G6 ──► G7 ──► G8 ──► G9 ──► G10      │
│                   SUC   IACS  Zones Conduit SL-T   SL-A   Gap   Plan        │
│                                                                             │
│   Pro Gate:       Readiness Score │ Work Items │ Critical Issues │ Pass     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

| Gate | Beschreibung | Prüfung |
|------|--------------|---------|
| **G1** | Asset Inventory | Asset-Inventar vollständig |
| **G2** | Asset Classification | Klassifizierung abgeschlossen |
| **G3** | SUC Definition | System Under Consideration definiert |
| **G4** | IACS Groups | IACS-Gruppen gebildet |
| **G5** | Zones | Sicherheitszonen abgeleitet |
| **G6** | Conduits | Conduits definiert |
| **G7** | SL-Target | Ziel-SL Assessment durchgeführt |
| **G8** | SL-Achieved | IST-SL Assessment durchgeführt |
| **G9** | Gap Analysis | Gap-Analyse abgeschlossen |
| **G10** | Action Plan | Maßnahmenplan verabschiedet |

---

## INCIDENT MANAGEMENT (NIST SP 800-61 + NIS2)

**OT-Incident Response mit CISA NCISS Scoring**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         INCIDENT LIFECYCLE                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Detected ──► Reported ──► Contained ──► Eradicated ──► Recovered ──► Closed │
│       │           │            │              │             │           │   │
│    NCISS       NIS2 24h    Containment    Root Cause    Recovery    Lessons │
│    Score       Report      Actions        Analysis      Verify      Learned │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### NCISS Scoring (CISA):

| Impact-Kategorie | Beschreibung | Scoring |
|------------------|--------------|---------|
| **Functional Impact** | Verfügbarkeit/Operations | 0-100 |
| **Information Impact** | Vertraulichkeit/Integrität | 0-100 |
| **Recoverability Impact** | Wiederherstellungsaufwand | 0-100 |
| **Safety Impact** | Personal-/Umweltsicherheit | 0-100 |
| **NCISS Score** | Gewichteter Gesamtscore | 0-100 |

### Severity-Ableitung:

| Score | Severity |
|-------|----------|
| 80-100 | Emergency |
| 60-79 | Severe |
| 40-59 | High |
| 20-39 | Medium |
| 0-19 | Low |

### NIS2 Compliance:

| Feature | Beschreibung |
|---------|--------------|
| **Reportability Check** | Automatische NIS2-Relevanz-Prüfung |
| **Initial Report** | 24-72h je nach Severity |
| **Intermediate Report** | 7 Tage |
| **Final Report** | 30 Tage |
| **Overdue Tracking** | Fristüberschreitungen |
| **Estimated Damage** | Schadensschätzung in EUR |

### OT-spezifische Features:

| Feature | Beschreibung |
|---------|--------------|
| **Affected Assets** | Betroffene Assets verlinken |
| **Purdue Levels** | Betroffene Level 0-5 |
| **Production Impact** | Produktionsauswirkung |
| **Safety System Affected** | Sicherheitssystem betroffen |
| **MITRE ATT&CK** | Mapping zu ATT&CK for ICS |
| **Root Cause** | Security, Human Error, System Failure, etc. |

### Containment Actions:

| Action | Beschreibung |
|--------|--------------|
| **Isolate Asset** | Asset vom Netzwerk trennen |
| **Disable Service** | Dienst deaktivieren |
| **Block IP** | IP-Adresse sperren |
| **Kill Process** | Prozess beenden |
| **Backup** | Sicherung erstellen |
| **Status Tracking** | Planned → Executing → Executed/Failed/Rolled Back |
| **Safety Review** | Sicherheitsfreigabe erforderlich |

### Incident Playbooks:

| Feature | Beschreibung |
|---------|--------------|
| **Vordefinierte Playbooks** | Response-Vorlagen |
| **Step-by-Step** | Schrittweise Ausführung |
| **Action Types** | Analyze, Containment, Eradication, Recovery, Safety Check |
| **Execution Tracking** | Status pro Schritt |
| **Time Estimates** | Geschätzte Dauer |

---

## BUSINESS IMPACT ASSESSMENT (BIA)

**5-dimensionale Auswirkungsanalyse mit Vererbung**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          BIA - 5 DIMENSIONEN                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐           │
│   │ SAFETY  │  │FINANCIAL│  │OPERATION│  │REPUTAT. │  │REGULAT. │           │
│   │  1-5    │  │  1-5    │  │  1-5    │  │  1-5    │  │  1-5    │           │
│   │         │  │         │  │         │  │         │  │         │           │
│   │ MTD     │  │ €/h     │  │ MTD     │  │ Media   │  │ Report  │           │
│   │ Hours   │  │ Loss    │  │ Cascade │  │ Visible │  │ Hours   │           │
│   └─────────┘  └─────────┘  └─────────┘  └─────────┘  └─────────┘           │
│                              │                                              │
│                              ▼                                              │
│                    Overall Impact Level = MAX(all)                          │
│                    MTD = MIN(applicable MTDs)                               │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Features:

| Feature | Beschreibung |
|---------|--------------|
| **Equipment BIA** | BIA pro Equipment/Anlage |
| **Process BIA** | BIA pro Prozess |
| **Aggregation** | Worst-Case (MAX) aus verlinkten Entitäten |
| **Inheritance** | Automatische Vererbung |
| **Gap Detection** | Fehlende BIA bei verlinkten Entitäten |
| **MTD** | Maximum Tolerable Downtime |
| **RTO/RPO** | Recovery Time/Point Objective |

### Regulatory Tracking:

| Regulierung | Abgedeckt |
|-------------|-----------|
| FDA 21 CFR Part 11 | ✓ |
| ISO 13485 | ✓ |
| ISO 22301 | ✓ |
| KRITIS | ✓ |
| NIS2 | ✓ |
| MDR | ✓ |
| IEC 62443 | ✓ |
| ISO 27001 | ✓ |
| GDPR/DSGVO | ✓ |
| BSI IT-Grundschutz | ✓ |

---

## VULNERABILITY MANAGEMENT

**CVE-Tracking und Asset-Korrelation**

| Feature | Beschreibung |
|---------|--------------|
| **NVD Integration** | Vollständige CVE-Datenbank |
| **EPSS Scores** | Exploit-Wahrscheinlichkeit |
| **CISA KEV** | Known Exploited Vulnerabilities |
| **CISA ICS Advisories** | OT-spezifische Advisories |
| **MSRC Integration** | Microsoft Security Updates |
| **CPE Matching** | Automatische Software-CVE-Korrelation |
| **Incident Linking** | CVE → Incident Verknüpfung |
| **Status Tracking** | Open, Investigating, Mitigated, Resolved |
| **Dashboard** | Vulnerability-Statistiken |
| **Export** | CVE-Listen exportieren |

---

## RISK CASES

**Risikoszenarien und Behandlung**

| Feature | Beschreibung |
|---------|--------------|
| **Risk Assessment** | Likelihood × Impact |
| **Risk Categories** | Security, Operational, Safety, Compliance |
| **Risk Treatment** | Accept, Mitigate, Transfer, Avoid |
| **Templates** | Vordefinierte Risikoszenarien |
| **Zone-basiert** | Risiken pro Zone |
| **Controls** | Zugeordnete Maßnahmen |
| **Status Tracking** | Open, In Progress, Closed |

---

## SYSTEM UNDER CONSIDERATION (SUC)

**Strukturierte Systemdokumentation für Assessments**

| Feature | Beschreibung |
|---------|--------------|
| **SUC Definition** | Name, Code, Beschreibung |
| **Scope** | Equipment, Networks, Zones, Assets, Conduits, Processes |
| **Versioning** | Draft → Published → Archived |
| **Change Notes** | Änderungsdokumentation pro Version |
| **Scope Validation** | Vollständigkeitsprüfung |
| **Gate Integration** | SUC-basierte Quality Gates |
| **Baseline Assignment** | Control Baselines pro SUC-Version |

---

# TEIL 5: INFRASTRUKTUR

---

## Dual-Zone-Architektur

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        IT ZONE (Purdue 4-5)                                 │
│                           Ports 80/443                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│   Browser ───► Nginx ───► FastAPI (3x) ───► PostgreSQL (Main + CVE)         │
│   (React)      (LB)       Backend           Redis (Queue + Sessions)        │
├─────────────────────── FIREWALL/DMZ ────────────────────────────────────────┤
│                        OT ZONE (Purdue 0-3)                                 │
│                         Ports 8080/8443                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│   WinAgent ───► Nginx ───► FastAPI (HMAC Auth, API Keys)                    │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Container-Stack (11 Services)

```yaml
├── postgres        # Main Database (213 Tables)
├── postgres_cve    # CVE Database
├── redis           # Queue & Sessions
├── backend_1/2/3   # FastAPI (Load Balanced)
├── worker_1/2      # RQ Workers (Agent Uploads)
├── cve_worker      # CVE Sync Worker
├── frontend        # React SPA
└── nginx           # Reverse Proxy (IT + OT Zones)
```

---

## BENUTZER & AUTHENTIFIZIERUNG

| Feature | Beschreibung |
|---------|--------------|
| **User Management** | CRUD für Benutzer (Admin-only) |
| **Role-based Access** | Tenant-basierte Zugriffskontrolle |
| **Server-side Sessions** | Redis-basierte Sessions |
| **Session Tracking** | IP, User-Agent, Expiry |
| **Multi-Session** | Mehrere Sessions pro User |
| **Logout All** | Alle Sessions invalidieren |
| **Rate Limiting** | 600/min Read, 60/min Write |
| **Audit Logging** | Vollständiges Audit Trail |

---

## DASHBOARD & ANALYTICS

| Feature | Beschreibung |
|---------|--------------|
| **OT Statistics** | Übersicht aller OT-Entitäten |
| **Incident KPIs** | Incident-Metriken |
| **Zone Completeness** | Vollständigkeits-Score pro Zone |
| **Network Status** | Dokumentationsstatus Netzwerke |
| **Assessment Progress** | Fortschritt SL-Assessments |
| **Quality Gate Status** | Gate-Readiness pro SUC |

---

# STATISTIKEN

| Metrik | Wert |
|--------|------|
| **Datenbank-Tabellen** | 213 |
| **Domain Packages** | 29 |
| **API Endpoints** | 300+ |
| **Frontend Pages** | 27 |
| **Frontend Components** | 167 |
| **Backend LOC** | ~50.000 |
| **Frontend LOC** | ~80.000 |
| **Compliance Standards** | 15+ |
| **Container Services** | 11 |


---

# ZUSAMMENFASSUNG

**bauVision OT-VAM** ist ein **vollständiges OT Asset Management & Versioning System** das:

| # | Feature | Beschreibung |
|---|---------|--------------|
| 1 | **OT Asset Management** | Vollständiges Asset-Lifecycle-Management für OT |
| 2 | **21 CFR Part 11 Versioning** | E-Signatur mit 4-Augen-Prinzip |
| 3 | **50+ OT-Dateitypen** | PLC, HMI, Robot, Recipe, Firmware, etc. |
| 4 | **IACS → Zone Automation** | Automatische Zone/Conduit-Ableitung |
| 5 | **Custom SL Assessment** | Vollständig anpassbare Fragenkataloge |
| 6 | **Quality Gates G1-G10** | IEC 62443-2-1 Meilensteine |
| 7 | **NCISS + NIS2** | CISA Scoring mit NIS2 Reporting |
| 8 | **5D BIA mit Vererbung** | Automatische Impact-Aggregation |
| 9 | **VDE/DGUV Prüfungen** | Integriertes Prüfmanagement |
| 10 | **Functional Safety** | SIL, PL, ISO 13849, IEC 62061 |
| 11 | **Runbook System** | OT Knowledge Management |
| 12 | **CVE Korrelation** | Automatisches Vulnerability Matching |


### Asset Management:
- **Standorte** nach ISA-95 Hierarchie verwaltet
- **Organisationen** mit automatischer Pfadberechnung abbildet
- **Prozesse** mit visuellen Flussdiagrammen dokumentiert
- **Netzwerke** mit vollständiger OT-Protokoll-Unterstützung erfasst
- **Systeme (IACS)** hierarchisch strukturiert
- **Equipment** mit Lifecycle und Functional Safety trackt
- **Assets** mit Software-Katalog und Telemetrie verwaltet

### Versioning:
- **21 CFR Part 11** konforme Versionierung bietet
- **50+ OT-Dateitypen** unterstützt
- **4-Augen-Prinzip** mit elektronischer Signatur implementiert
- **Check-In/Check-Out** mit exklusivem Locking ermöglicht

### Security & Compliance:
- **IEC 62443 Zones & Conduits** automatisch aus IACS ableitet
- **Custom SL Assessments** mit eigenem Fragenkatalog ermöglicht
- **Quality Gates G1-G10** nach IEC 62443-2-1 prüft
- **NIST/CISA Incident Management** mit NIS2 Compliance integriert
- **Vulnerability Management** mit automatischer CVE-Korrelation bietet

### Instandhaltung:
- **VDE/DGUV Prüfungen** vollständig abbildet
- **Runbook System** für OT Knowledge Management bereitstellt
- **Software Catalog** zentral verwaltet

---

## 📞 Kontakt

**Bauer Automation Solutions**  
Dennis Bauer

mail: dennis.bauer@bauer-automation-solutions.de
---

<p align="center">
  <strong>© 2026 Bauer Automation Solutions</strong>
</p>






