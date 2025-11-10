# OT/ICS Asset Management System - Vollständiges System-Konzept

Bauer Automation Solutions | 2025

---

## System-Übersicht

Das OT/ICS Asset Management System ist eine vollständig integrierte Plattform für die Verwaltung, Dokumentation, Analyse und Absicherung industrieller Assets. Das System  bietet eine durchgängige Lösung von der Asset-Discovery bis zur Compliance-Dokumentation.

**Kernphilosophie:**
- **Alles aus einer Hand** - Keine fragmentierten Tools mehr
- **ISA-95 Native** - Nicht aufgesetzt, sondern von Grund auf standardkonform
- **Security First** - Entwickelt für OT-Umgebungen mit höchsten Sicherheitsanforderungen

---

## Architektur

### Komponenten-Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                    FRONTEND LAYER (React)                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📊 DASHBOARDS                    🔧 MANAGEMENT                │
│  ├─ Executive Overview            ├─ Asset Management           │
│  ├─ Operations Dashboard          ├─ Location Hierarchy         │
│  ├─ Security Dashboard            ├─ Equipment Management       │
│  ├─ Compliance Dashboard          ├─ Process Management         │
│  ├─ Financial Dashboard           ├─ Organization Management    │
│  └─ Maintenance Dashboard         └─ User Management            │
│                                                                 │
│  🛡️ SECURITY & RISK              📈 ANALYTICS                  │
│  ├─ Security Assessment Wizard    ├─ Financial Analysis         │
│  ├─ Risk Assessment Wizard        ├─ Performance Analysis       │
│  ├─ Vulnerability Management      ├─ Trend Analysis             │
│  ├─ Compliance Reports            ├─ Predictive Maintenance     │
│  └─ Audit Trail Viewer            └─ Cost Optimization          │
│                                                                 │
│  🔄 VERSION CONTROL              📋 REPORTING                  │
│  ├─ Asset Version Browser         ├─ Custom Report Builder      │
│  ├─ Check-Out/Check-In            ├─ Template Library           │
│  ├─ Approval Workflow             ├─ Scheduled Reports          │
│  ├─ Diff Viewer                   ├─ Export (Excel/PDF/CSV)     │
│  └─ History Timeline              └─ Distribution Lists         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    API LAYER (FastAPI)                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🔐 AUTHENTICATION & AUTHORIZATION                             │
│  ├─ Zone-aware Auth (IT Zone / Shopfloor Zone)                  │
│  ├─ Multi-mode: None / Basic / API Key / mTLS                   │
│  ├─ Role-based Access Control (RBAC)                            │
│  ├─ Group-based Permissions                                     │
│  └─ LDAP/Active Directory Integration                           │
│                                                                 │
│  🎫 LICENSE SYSTEM                                             │
│  ├─ 4 License Types (Demo/Starter/Professional/Enterprise)      │
│  ├─ Module-based Features (10+ Modules)                         │
│  ├─ Asset Packs (50/100/150/200/250/500/unlimited)              │
│  ├─ Feature-level Control                                       │
│                                                                 │
│                                                                 │
│  🔌 REST API ENDPOINTS                                         │
│  ├─ Asset Management (/api/v1/assets)                           │
│  ├─ Location Management (/api/v1/locations)                     │
│  ├─ Equipment Management (/api/v1/equipment)                    │
│  ├─ Process Management (/api/v1/processes)                      │
│  ├─ Organization Management (/api/v1/organizations)             │
│  ├─ Network Management (/api/v1/networks)                       │
│  ├─ Version Control (/api/v1/versions)                          │
│  ├─ Security Assessments (/api/v1/security)                     │
│  ├─ Risk Assessments (/api/v1/risk)                             │
│  ├─ CVE Management (/api/v1/cves)                               │
│  ├─ Agent Management (/api/v1/agents)                           │
│  ├─ Reports & Analytics (/api/v1/reports)                       │
│                                                                 │
│                                                                 │
│  💾 BUSINESS LOGIC & SERVICES                                  │
│  ├─ Asset Service (Lifecycle Management)                        │
│  ├─ Version Control Service (Check-in/Check-out)                │
│  ├─ Financial Rollup Service (Recursive Calculations)           │
│  ├─ Discovery Service (Auto-population)                         │
│  ├─ Security Service (Assessment Automation)                    │
│  ├─ Risk Service (Risk Calculations)                            │
│  ├─ Vulnerability Service (CVE Matching)                        │
│  ├─ Compliance Service (Standards Mapping)                      │
│  ├─ Analytics Service (ML/AI Features)                          │
│  └─ Integration Service (External Systems)                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                 DATA COLLECTION LAYER                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🔍 WINDOWS AGENT                                              │
│  ├─ System Information (WMI Queries)                            │
│  ├─ Hardware Detection (CPU, RAM, Disks, NICs)                  │
│  ├─ Software Inventory (Installed Programs)                     │
│  ├─ Network Configuration (IPs, MACs, VLANs)                    │
│  ├─ Service Status Monitoring                                   │
│  ├─ Performance Metrics Collection                              │
│  ├─ Event Log Analysis                                          │
│  └─ Scheduled Scans with REST Push                              │
│                                                                 │
│  🏭 OT NETWORK SCANNER                                         │
│  ├─ PROFINET Discovery (DCP Protocol)                           │
│  ├─ Siemens S7 Scanner (ISO-on-TCP)                             │
│  ├─ Modbus TCP Scanner                                          │
│  ├─ SNMP Discovery (v1/v2c/v3)                                  │
│  ├─ SSH Scanner (System Info)                                   │
│  ├─ ARP/ICMP Network Discovery                                  │
│  ├─ Protocol Detection & Fingerprinting                         │
│  ├─ Manufacturer Detection (OUI Lookup)                         │
│  ├─ Model & Firmware Detection                                  │
│  └─ Auto-population to Database                                 │
│                                                                 │
│  🔗 INTEGRATION CONNECTORS                                     │
│  ├─ NVD API (Vulnerability Database)                            │
│  ├─ Vendor Advisories (Siemens, Rockwell, etc.)                 │
│  └─ Custom REST/ODBC Connectors                                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                DATABASE LAYER (PostgreSQL)                      │
├─────────────────────────────────────────────────────────────────┤
│  [Details siehe unten]                                          │
└─────────────────────────────────────────────────────────────────┘
```

---

## ISA-95 Datenmodell

### Die vier Hierarchien

Das System implementiert die vollständigen ISA-95 Hierarchien als **separate, unabhängige Bäume**. Dies ermöglicht:
- Flexible Zuordnungen (N:M Relationen)
- Unterschiedliche Detaillierungsgrade je Hierarchie
- Historisierung ohne Datenverlust
- Parallele Organisationsformen

#### 1. Physical Location Hierarchy (Wo?)

**10 Location Types:**

```
Enterprise              → Konzern/Holding-Ebene
├── Site                → Werk/Standort (Hamm, Berlin, etc.)
    ├── Building        → Gebäude (Halle A, Verwaltung)
        ├── Floor       → Etage (EG, 1.OG, 2.OG)
            ├── Area    → Bereich (Produktion, Lager)
                ├── Room    → Raum (Raum 101, Labor)
                    ├── Zone    → Zone (Gefahrenzone, Clean Room)
                        ├── Cabinet → Schaltschrank (NK01, SK-02)
                            ├── Rack    → Rack (Rack 1, 19" Rack)
                                └── Slot    → Slot/Position (Slot 3, Position 4)
```

**Datenfelder (45+ pro Location):**
- Basis: Name, Type, Description, Parent
- Adresse: Address, City, State, ZIP, Country
- GPS: Latitude, Longitude, Altitude
- Sicherheit: Hazardous Area (ja/nein), Classification (Zone 0/1/2/20/21/22), Security Level (0-4)
- Umgebung: Environmental Zone, Temperature Range, Humidity Range
- Organisation: Responsible Person, Department, Cost Center
- Notfall: Emergency Contact, Assembly Point, Evacuation Route
- Dokumentation: Floor Plans, Access Restrictions, Notes
- Custom: Custom Attributes (JSONB)

**Besonderheiten:**
- Automatische Full Path Generation (`/Enterprise/Site-Hamm/Halle-A/EG/Produktion/Raum-101`)
- Gefahrenbereich-Tracking (Ex-Schutz Zonen)
- Security Level Vererbung
- GPS-Koordinaten für Outdoor Assets

#### 2. Equipment Hierarchy (Was?)

**13 Equipment Classes:**

```
Enterprise              → Gesamtunternehmen
├── Site                → Werk-Ebene
    ├── Area            → Produktionsbereich
        ├── Production_Line    → Fertigungslinie
            ├── Work_Center    → Arbeitszentrum
                ├── Work_Cell    → Arbeitszelle
                    ├── Production_Unit    → Produktionseinheit
                        ├── Process_Cell    → Prozesszelle
                            ├── Unit    → Einheit
                                ├── Machine    → Maschine
                                    ├── Equipment_Module    → Equipment-Modul
                                        ├── Control_Module    → Steuerungsmodul
                                            └── Component    → Komponente
```

**Datenfelder (60+ pro Equipment):**
- Basis: Name, Class, Description, Parent
- Location: Physical Location Link
- Finanzen: Acquisition Cost, Current Book Value, Annual Operating Cost, Annual Maintenance Cost, Depreciation
- Performance: OEE Target/Actual, Availability Target/Actual, Performance Target/Actual, Quality Target/Actual
- Reliability: MTBF Hours, MTTR Hours, Failure Count, Downtime Minutes
- Energie: Power Rating (kW), Energy Consumption (kWh/year)
- Kapazität: Throughput (Units/hour), Max Production Rate
- Organisation: Cost Center, Profit Center, Responsible Person, Operator
- Custom: Custom Attributes (JSONB)

**Financial Rollup - Das Killer-Feature:**

Automatische, rekursive Kostenberechnung über die gesamte Equipment-Hierarchie:

```sql
-- Beispiel: Fertigungslinie mit 4 Maschinen
Fertigungslinie A (500.000 EUR Anschaffung)
├── Maschine M01 (125.000 EUR + 5 Assets à 15.000 EUR)
├── Maschine M02 (125.000 EUR + 5 Assets à 15.000 EUR)
├── Maschine M03 (125.000 EUR + 5 Assets à 15.000 EUR)
└── Maschine M04 (125.000 EUR + 5 Assets à 15.000 EUR)

SELECT calculate_equipment_asset_value('Fertigungslinie A');
→ 800.000 EUR (Equipment + alle zugeordneten Assets, rekursiv)

SELECT calculate_equipment_operating_cost('Fertigungslinie A');
→ 120.000 EUR/Jahr (Operating + Maintenance Costs, rekursiv)
```

**Funktionen:**
- `calculate_equipment_asset_value(equipment_name)` - Total Asset Value
- `calculate_equipment_operating_cost(equipment_name)` - Jährliche Betriebskosten
- `calculate_equipment_oee(equipment_name)` - Gewichteter OEE
- `count_equipment_assets(equipment_name, recursive)` - Asset-Anzahl

#### 3. Process Segment Hierarchy (Wie?)

**7 Segment Types:**

```
Enterprise              → Unternehmensprozesse
├── Site                → Werk-Prozesse
    ├── Area            → Bereichs-Prozesse
        ├── Process_Cell    → Prozesszelle
            ├── Unit_Procedure    → Verfahrenseinheit
                ├── Operation    → Operation
                    └── Phase    → Phase
```

**5 Execution Types:**
- `Continuous` - Durchlaufprozess (24/7, z.B. Raffinerie)
- `Batch` - Chargenprozess (Pharma, Chemie)
- `Discrete` - Stückgut (Automotive, Elektronik)
- `Semi_Continuous` - Hybrid
- `Campaign` - Kampagnenfertigung (Food & Beverage)

**Datenfelder (50+ pro Process Segment):**
- Basis: Name, Type, Execution Type, Description, Parent
- Material: Input Materials (JSON), Output Materials (JSON), Material Balance
- Parameter: Process Parameters (JSON: Sollwerte, Toleranzen, Grenzwerte)
- Timing: Standard Duration, Actual Duration, Cycle Time, Changeover Time
- Durchsatz: Throughput (Units/hour), Batch Size
- Performance: OEE Target/Actual, Yield Target/Actual, Scrap Rate, First Pass Yield
- Kosten: Cost per Run, Labor Cost per Run, Material Cost per Run
- Ressourcen: Required Personnel Count, Required Equipment (JSON), Required Tools (JSON)
- Qualität: Quality Parameters (JSON), Inspection Points, Test Requirements
- Custom: Custom Attributes (JSONB)

**Prozess-Dokumentation:**
```json
{
  "input_materials": [
    {"material": "Rohmaterial A", "quantity": 100, "unit": "kg"},
    {"material": "Additiv B", "quantity": 5, "unit": "kg"}
  ],
  "output_materials": [
    {"material": "Produkt X", "quantity": 95, "unit": "kg"},
    {"material": "Abfall", "quantity": 10, "unit": "kg"}
  ],
  "process_parameters": {
    "temperature": {"target": 180, "tolerance": 5, "unit": "°C"},
    "pressure": {"target": 2.5, "tolerance": 0.2, "unit": "bar"},
    "duration": {"target": 120, "tolerance": 10, "unit": "min"}
  }
}
```

#### 4. Organizational Hierarchy (Wer?)

**9 Organization Types:**

```
Corporation             → Konzern
├── Company             → Unternehmen
    ├── Business_Unit   → Geschäftsbereich
        ├── Division    → Sparte
            ├── Department    → Abteilung
                ├── Team    → Team
                    ├── Cost_Center       → Kostenstelle
                    ├── Profit_Center     → Profit Center
                    └── Investment_Center → Investment Center
```

**Datenfelder (35+ pro Organization):**
- Basis: Name, Type, Description, Parent
- Finanzen: Cost Center Number, Profit Center Number, Investment Center Number
- Budget: Budget Yearly, Actual Spending Yearly, Budget Utilization %
- Personal: Manager Name, Deputy Manager, Contact Email/Phone
- Headcount: Employee Count, Contractor Count, Temporary Count
- Verantwortung: Area of Responsibility, Asset Count
- Custom: Custom Attributes (JSONB)

---

## Asset-Datenmodell

### Assets - Haupttabelle (~100 Felder)

**Basis-Daten:**
- Name (UNIQUE), Type, Status, Description, UUID

**Identifikation:**
- Manufacturer (ENUM: 50 Hersteller)
- Model, Serial Number, Order Number, Asset Tag
- Firmware Version, Hardware Revision, Software Version

**Network (Primary):**
- IP Address (IPv4/IPv6), MAC Address, Hostname
- Subnet Mask, Gateway, DNS Servers
- VLAN ID, Network Zone, Purdue Level

**Lifecycle:**
- Purchase Date, Delivery Date, Installation Date, Commissioning Date
- Warranty Start/End Date, Extended Warranty End
- Maintenance Last/Next Date, Maintenance Interval Days
- Expected Lifetime Years, Planned Retirement Date
- Decommissioning Date, Disposal Date, Disposal Method

**Finanzen:**
- Purchase Price, Current Book Value, Residual Value
- Depreciation Method (Linear/Declining/etc.), Depreciation Rate, Accumulated Depreciation
- Operating Cost Yearly, Maintenance Cost Yearly
- Supplier, Invoice Number, Leasing Company

**Verantwortlichkeiten:**
- Owner, Operator, Responsible Person, Technical Contact
- Department, Cost Center, Profit Center

**Sicherheit & Compliance:**
- Safety Category (ISO 13849: B/1/2/3/4)
- Performance Level (ISO 13849: a/b/c/d/e)
- SIL Level (IEC 61508: 0/1/2/3/4)
- CE Marking, Certificates
- Inspection Last/Next Date, Inspector Name

**Technische Daten:**
- Dimensions (Width/Height/Depth), Weight
- Power Rating (kW), Voltage (V), Current (A), Frequency (Hz)
- Operating Temperature Min/Max, Storage Temperature Min/Max
- Protection Class (IP Rating)

**Standort:**
- Building, Floor, Room, Cabinet, Rack Position
- GPS Coordinates (Latitude, Longitude)
- QR Code, Barcode

**Dokumentation:**
- Manual URL, Datasheet URL, Drawing URL, P&ID Location
- Photos (JSON Array), Documents (JSON Array)
- Notes, Internal Comments

**Nutzung:**
- Operating Hours Total, Operating Hours Last Reset
- Cycles Count, Utilization Rate, Availability Percentage
- Last Used Date

**Produktion:**
- Production Capacity, Performance Rating
- Uptime Percentage, Downtime Minutes
- OEE Score, Energy Consumption (kWh)
- Production Line Assignment

**Custom:**
- Context Data (JSONB) - Beliebige zusätzliche Felder

### Asset Inventory - OT Extended (~135 Felder)

**1:1 Erweiterung zu Assets mit OT-spezifischen Feldern:**

**Classification Extended:**
- Asset Class (Control_System, Field_Device, Network_Equipment, Safety_System, etc.)
- Asset Subclass, Asset Category
- Criticality (Mission_Critical / Business_Critical / High / Medium / Low / Not_Critical / Unknown)
- Business Function, Process Relevance
- Redundancy Available (Boolean), Redundancy Type, Redundancy Partner
- Is Safety Critical, Is Cyber Physical System

**Hardware Extended:**
- Vendor Name, Product Family, Product Line
- Hardware Revision, Firmware Version Detail, BIOS Version, Bootloader Version
- Asset Tag, Inventory Number, License Key

**Network Extended:**
- Primary IP, Secondary IP, Management IP, BMC IP
- VLAN ID, Network Zone (11 Zonen-Typen), Purdue Level (0-5 + Cloud)
- Protocol Suite (ARRAY: 45 industrial protocols)
- Ports Used, Open Ports, Closed Ports
- DMZ Usage, Internet Exposure, Remote Access Enabled

**Location Extended:**
- Site Name, Site Code, Building Name, Floor Level
- Room ID, Zone ID, Physical Coordinates
- Rack ID, Rack Unit Position, Cabinet ID
- Environmental Zone (Clean Room, Hazardous Area, etc.)

**Function:**
- Primary Function, Secondary Function
- Process Step, Production Line ID, Work Center ID
- Automation Level (ENUM: Manual/Semi-Auto/Fully-Auto/Autonomous)
- Control Loop ID, Interlock Group
- PLC Program Name, HMI Config File, SCADA Tag List
- MES Integration (Boolean), ERP Integration (Boolean)

**Lifecycle Extended:**
- Procurement Date, Acceptance Date, FAT Date, SAT Date
- Go-Live Date, Commissioning Status (14 Status-Werte)
- Warranty Start Date, Warranty Duration Months, Extended Warranty End
- Planned EOL Date, Actual EOL Date
- Decommissioning Date, Replacement Planned, Replacement Asset ID
- Lifecycle Phase (14 Phasen: Planning → Archived → Disposed)

**Maintenance Extended:**
- Maintenance Strategy (8 Strategien: Preventive/Predictive/Corrective/etc.)
- Maintenance Type (9 Typen: Routine/Preventive/Emergency/etc.)
- PM Schedule, Last PM Date, Next PM Date, PM Frequency Days
- Calibration Required, Last Calibration Date, Next Calibration, Calibration Interval Months
- Maintenance Window (z.B. "Sonntag 02:00-06:00")
- Spare Parts Required (JSON), Spare Parts Location
- Maintenance Vendor, Maintenance Contract Number, Support Contract End Date
- MTBF Hours, MTTR Hours, Failure Count

**Documentation Extended:**
- Technical Manual Location, Operational Manual Location, Maintenance Manual Location
- Wiring Diagram Location, P&ID Location, Software Documentation Location
- As-Built Drawings Location, Configuration Backup Location, Change History Location
- Training Materials Location, Video Tutorials URL

**Ownership:**
- Asset Owner, Asset Custodian
- Technical Responsible, Operational Responsible, Maintenance Responsible
- Business Owner, Procurement Contact
- Vendor Contact, Vendor Support Email/Phone
- Integrator Contact

**Data Quality:**
- Completeness Score (0-100), Accuracy Verified (Boolean)
- Last Verification Date, Verified By
- Data Source (Discovery/Manual/Import/Agent/Scanner)
- Confidence Level (High/Medium/Low/Unknown)

**Custom:**
- Custom Field 1-5 (String)
- Custom JSON (JSONB) - Beliebige Struktur

### Asset Network Adapters (~45 Felder)

**N:1 Relation - Ein Asset kann mehrere Netzwerkschnittstellen haben:**

**Identifikation:**
- Adapter Name (z.B. "eth0", "eth1", "en0", "PROFINET Port 1")
- Adapter Type (Ethernet/WiFi/Fiber/Industrial_Ethernet/Fieldbus/Serial/Virtual/LoopBack/Bridge)
- Is Primary (Boolean - nur eine pro Asset)
- Adapter Order (Sortierung)
- Description

**Network Configuration:**
- IP Address (IPv4), IPv6 Address
- MAC Address (validated format)
- Subnet Mask, CIDR Notation, Gateway
- DNS Primary, DNS Secondary

**VLAN & Segmentierung:**
- VLAN ID, Network Zone, Purdue Level, Network Segment Name

**Protokolle:**
- Protocols (ARRAY von 45 industrial_protocol)
  - PROFINET_RT/IRT, PROFIBUS_DP/PA
  - EtherNet/IP, DeviceNet
  - Modbus_TCP/RTU/ASCII
  - S7, S7_Plus, OPC_UA
  - MQTT, AMQP, CoAP
  - DNP3, IEC_60870_5_104
  - BACnet, LonWorks, KNX
  - CANopen, EtherCAT
  - POWERLINK, SERCOS_III
  - CC-Link, MECHATROLINK
  - etc.
- Ports Used (Array), Protocol Details (JSON)

**Performance:**
- Speed (z.B. "1000Mbps", "100Mbps")
- Duplex (Full/Half/Auto/Unknown)
- MTU (Maximum Transmission Unit)
- Bandwidth Limit, QoS Priority

**Physical:**
- Port Number, Switch Port, Patch Panel
- Cable Type (CAT5/CAT6/CAT7/Fiber_MM/Fiber_SM)
- Cable Length (Meters)

**Status & Health:**
- Status (Active/Inactive/Disabled/Error/Maintenance)
- Link Status (Boolean)
- Last Seen (Timestamp)
- Uptime Hours, Errors Count, Packets Sent, Packets Received

**Security:**
- Encryption Enabled, Encryption Type
- Firewall Rules (JSON), Access Control List (JSON)

---

## ENUMs - Validierte Wertelisten

Das System verwendet **50+ ENUMs** für standardisierte, validierte Werte:

### Asset & Hardware

**asset_type** (32 Werte):
- PLC, HMI, SCADA_Server, DCS_Controller, RTU, IED
- Robot_Controller, CNC_Controller, Drive, VFD, Soft_Starter
- Motor, Pump, Valve, Actuator
- Sensor, Transmitter, Analyzer, Meter
- Switch, Router, Firewall, Gateway, Access_Point
- Field_Device, IO_Module, Safety_PLC, Remote_IO
- Server, Workstation, Panel_PC
- Camera, RFID_Reader, Barcode_Scanner

**asset_status** (9 Werte):
- active, inactive, maintenance, planned, commissioned
- decommissioned, defect, testing, standby, unknown

**manufacturer** (50 Top-OT-Hersteller):
- Siemens, Rockwell_Automation, Allen_Bradley
- Schneider_Electric, ABB, Phoenix_Contact
- Mitsubishi_Electric, Omron, Beckhoff
- Emerson, Honeywell, Yokogawa
- Endress_Hauser, VEGA, Pepperl_Fuchs
- SICK, Turck, Balluff, IFM, Leuze
- Bosch_Rexroth, SEW_Eurodrive, Danfoss
- Yaskawa, FANUC, KUKA, Universal_Robots
- Cisco, Moxa, Hirschmann, Weidmuller
- B&R, Festo, SMC, Norgren
- Rittal, Eaton, Legrand
- Advantech, Kontron, Siemens_IPC
- etc.

### Networking

**industrial_protocol** (45 Werte):
- PROFINET_RT, PROFINET_IRT, PROFIBUS_DP, PROFIBUS_PA
- EtherNet/IP, DeviceNet, ControlNet
- EtherCAT, CANopen, CAN
- Modbus_TCP, Modbus_RTU, Modbus_ASCII
- S7, S7_Plus, TIA_Portal
- OPC_UA, OPC_Classic
- MQTT, MQTT_Sparkplug, AMQP, CoAP
- DNP3, IEC_60870_5_101, IEC_60870_5_104
- IEC_61850, IEC_61850_GOOSE, IEC_61850_MMS
- BACnet_IP, BACnet_MSTP, LonWorks, KNX
- POWERLINK, SERCOS_III
- CC-Link, CC-Link_IE, MECHATROLINK
- Foundation_Fieldbus_H1, Foundation_Fieldbus_HSE
- HART, WirelessHART
- IO-Link, AS-Interface
- PROFINET_CBA, PROFINET_PROFIsafe

**network_zone** (11 Werte):
- Production_Network, Control_Network, Safety_Network
- Field_Network, Sensor_Network
- Office_Network, Management_Network
- DMZ, External_Network
- Wireless_Network, Guest_Network

**purdue_level** (8 Werte):
- Level_0_Physical_Process
- Level_1_Basic_Control
- Level_2_Supervisory_Control
- Level_3_Site_Operations
- Level_3_5_DMZ
- Level_4_Enterprise_Logistics
- Level_5_Enterprise_Network
- Level_6_Cloud

**adapter_type** (9 Werte):
- Ethernet, WiFi, Fiber, Industrial_Ethernet
- Fieldbus, Serial, Virtual, LoopBack, Bridge

### Standards & Classification

**criticality** (7 Werte):
- Mission_Critical - System-critical, failure = production stop
- Business_Critical - Business-critical, major impact
- High - Important, significant impact
- Medium - Standard importance
- Low - Minor impact
- Not_Critical - No impact
- Unknown - Not assessed

**asset_class** (12 Werte):
- Control_System, Field_Device, Network_Equipment
- Safety_System, Monitoring_System, Analysis_System
- Drive_System, Robot_System, CNC_System
- Energy_Management, Building_Automation
- IT_Infrastructure

**safety_category** (6 Werte - ISO 13849):
- CAT_4 - Highest (PL e)
- CAT_3 - High (PL d)
- CAT_2 - Medium (PL c)
- CAT_1 - Low (PL b)
- CAT_B - Basic (PL a)
- Not_Safety_Related

**performance_level** (6 Werte - ISO 13849):
- PLe - Highest
- PLd, PLc, PLb, PLa
- Not_Applicable

**sil_level** (6 Werte - IEC 61508):
- SIL_4 - Highest
- SIL_3, SIL_2, SIL_1, SIL_0
- Not_Safety_Related

**protection_class** (7 Werte):
- IP67, IP65, IP54, IP44, IP20, IP00, Not_Rated

### Lifecycle & Maintenance

**lifecycle_phase** (14 Werte):
- Planning - In Planung
- Procurement - Beschaffung läuft
- Installation - Installation läuft
- Commissioning - Inbetriebnahme
- Active_Production - Aktiv im Einsatz
- Warranty_Period - Innerhalb Garantiezeit
- Extended_Support - Erweiterte Unterstützung
- Limited_Support - Eingeschränkte Unterstützung
- End_of_Life - EOL erreicht
- End_of_Support - Support beendet
- Obsolete - Veraltet
- Decommissioning - Außerbetriebnahme läuft
- Archived - Archiviert
- Disposed - Entsorgt

**commissioning_status** (7 Werte):
- Not_Started, In_Progress, Testing, Validation
- Completed, Failed, On_Hold

**maintenance_strategy** (8 Werte):
- Preventive - Vorbeugende Wartung
- Predictive - Zustandsbasierte Wartung
- Corrective - Korrektive Wartung
- Condition_Based - Condition Monitoring
- Time_Based - Zeitbasiert
- Risk_Based - Risikobasiert
- Run_To_Failure - Bis zum Ausfall
- Total_Productive_Maintenance - TPM

**maintenance_type** (9 Werte):
- Routine - Routinewartung
- Preventive - Vorbeugende Wartung
- Corrective - Reparatur
- Emergency - Notfall-Reparatur
- Overhaul - Überholung
- Calibration - Kalibrierung
- Firmware_Update - Firmware-Update
- Security_Patch - Sicherheits-Patch
- Inspection - Inspektion

### Process & Organization

**process_segment_type** (7 Werte):
- Enterprise, Site, Area, Process_Cell
- Unit_Procedure, Operation, Phase

**process_execution_type** (5 Werte):
- Continuous - Durchlaufprozess
- Batch - Chargenprozess
- Discrete - Stückgut
- Semi_Continuous - Hybrid
- Campaign - Kampagnenfertigung

**organization_type** (9 Werte):
- Corporation, Company, Business_Unit, Division
- Department, Team
- Cost_Center, Profit_Center, Investment_Center

---

## Version Control System

### Check-Out / Check-In Workflow

**Konzept:**
Assets und deren zugehörige Dateien (SPS-Programme, EPLAN-Projekte, Dokumentation) werden versioniert. Änderungen durchlaufen einen definierten Workflow mit 4-Augen-Prinzip.

**Asset-Daten-Kategorien:**

1. **SPS-Programme**
   - TIA Portal Projekte (.ap17, .zap17)
   - Step 7 Classic (.s7p)
   - CODESYS Projekte (.project)
   - Logix5000 (.ACD)
   - Structured Text, Ladder Logic, Function Blocks

2. **EPLAN-Projekte**
   - EPLAN Electric P8 (.elk, .epj)
   - Stromlaufpläne, Schaltpläne
   - Kabellisten, Stücklisten
   - Klemmenstreifen-Belegung

3. **Dokumentation**
   - Betriebsanleitungen (PDF, DOCX)
   - Wartungshandbücher
   - Schaltpläne (PDF, DWG)
   - P&IDs (PDF, DWG, VSD)
   - Parameterlisten (Excel, CSV)
   - Kalibrier-Zertifikate
   - Prüfprotokolle

4. **HMI-Projekte**
   - WinCC Projekte
   - FactoryTalk View
   - Zenon Projekte
   - Custom Web-HMIs

5. **Konfigurationsdateien**
   - Network Configs (Switch, Router)
   - Firewall Rules
   - SCADA Tag Databases
   - Recipe Files
   - Alarm Configs

### Version Control Features

**Version Status Workflow:**

```
DRAFT              → Entwurf, in Bearbeitung
    ↓
REVIEW             → Zur Prüfung eingereicht, Check-In
    ↓
APPROVED           → Freigegeben (4-Augen-Prinzip)
    ↓
PRODUCTIVE         → Aktiv im Einsatz
    ↓
WITHDRAWN          → Zurückgezogen, nicht mehr gültig
    ↓
ARCHIVED           → Archiviert, historisch
```

**Change Types:**
- Bugfix - Fehlerbehebung
- Feature - Neue Funktion
- Parameter - Parameteränderung
- Safety - Safety-relevante Änderung
- Optimization - Optimierung
- Documentation - Dokumentation
- Refactoring - Code-Refactoring
- Maintenance - Wartung

**Semantic Versioning:**
- Major.Minor.Patch (z.B. V1.2.3)
- Major: Breaking Changes, inkompatibel
- Minor: Neue Features, kompatibel
- Patch: Bugfixes, kompatibel

**Check-Out Process:**

```sql
-- User möchte Asset "PLC-Line-A-01" bearbeiten
1. Check if asset is already checked out → Nein
2. Create checkout record
   - Asset ID
   - User (Dennis.Baier)
   - Checkout Time
   - Reason ("Update S7 program for new sensor")
   - Expected Duration
3. Lock asset (exclusive lock)
4. Return success → User kann bearbeiten
```

**Check-In Process:**

```sql
-- User checkt Asset "PLC-Line-A-01" wieder ein
1. Verify checkout exists for this user
2. User provides:
   - Version Number (V1.2.3)
   - Description ("Added sensor integration")
   - Change Type (Feature)
   - Files (Upload: PLC_Program.zap17, Documentation.pdf)
3. Create new version
   - Status: REVIEW
   - Store files in versioned directory
   - Calculate file hash (SHA256)
4. Release checkout lock
5. Notify reviewers
```

**Approval Process (4-Augen-Prinzip):**

```sql
-- Reviewer (Manager, Senior Engineer) prüft Version
1. Load version from REVIEW status
2. Download files, review changes
3. Reviewer decides:
   - APPROVE:
     - Set status to APPROVED
     - Add approval comment
     - Record approver & timestamp
     - Version is now readonly
   - REJECT:
     - Set status back to DRAFT
     - Add rejection reason
     - Notify creator
```

**Deployment to Productive:**

```sql
-- Approved version wird produktiv gesetzt
1. Load version with status APPROVED
2. User confirms deployment
3. Set status to PRODUCTIVE
   - Record deployment timestamp
   - Record deploying user
4. Previous PRODUCTIVE version → set to WITHDRAWN
5. Notify operations team
```

**Version History & Comparison:**

```sql
-- Zeige alle Versionen eines Assets
SELECT * FROM asset_versions 
WHERE asset_id = 'PLC-Line-A-01' 
ORDER BY version_major DESC, version_minor DESC, version_patch DESC;

-- Vergleiche zwei Versionen (Diff)
- File-Level Diff (welche Files geändert)
- Content Diff (Line-by-Line für Text-Files)
- Binary Diff (für kompilierte Programme)
```

**File Storage Structure:**

```
/storage/versions/
├── PLC-Line-A-01/
│   ├── V1.0.0/
│   │   ├── PLC_Program.zap17
│   │   ├── Documentation.pdf
│   │   └── manifest.json
│   ├── V1.1.0/
│   │   ├── PLC_Program.zap17
│   │   ├── Documentation.pdf
│   │   ├── HMI_Config.smc
│   │   └── manifest.json
│   └── V1.2.3/
│       ├── PLC_Program.zap17
│       ├── Documentation.pdf
│       └── manifest.json
```

**Audit Trail:**

Jede Aktion wird geloggt:
- Who: User
- What: Action (checkout, checkin, approve, deploy)
- When: Timestamp
- Why: Reason/Comment
- Where: Asset ID, Version ID

---

## Security & Risk Assessment

### Security Assessment (IEC 62443 / NIS2)

**13 Assessment Categories:**

1. **Architecture & Segmentation**
   - Network segmentation level
   - Purdue model compliance
   - Zone/conduit architecture
   - DMZ implementation
   - Firewall deployment

2. **CIA Requirements & Business Criticality**
   - Confidentiality requirements
   - Integrity requirements
   - Availability requirements
   - Business impact assessment
   - Recovery time objectives (RTO)

3. **Legacy Status & Support**
   - Age of system
   - Vendor support status
   - Patch availability
   - End-of-life status
   - Upgrade path available

4. **Safety Integration**
   - Safety-critical function
   - Safety integrity level (SIL)
   - Safety PLC integration
   - Emergency stop implementation
   - Safety monitoring

5. **Access Control & Authentication**
   - Authentication methods
   - Password policy
   - Multi-factor authentication
   - Privilege escalation controls
   - Account management

6. **Remote Access & VPN**
   - Remote access availability
   - VPN implementation
   - Remote access logging
   - Jump server usage
   - Vendor remote access

7. **Patch Management & Vulnerability**
   - Patch management process
   - Vulnerability scanning
   - Patch deployment testing
   - Patch deployment schedule
   - Compensating controls

8. **Monitoring & Logging**
   - Security event logging
   - Log retention
   - Log analysis
   - Intrusion detection
   - Anomaly detection

9. **Backup & Business Continuity**
   - Backup frequency
   - Backup testing
   - Offsite backup storage
   - Disaster recovery plan
   - Business continuity plan

10. **Resilience & Redundancy**
    - System redundancy
    - Failover capabilities
    - Spare parts availability
    - MTTR targets
    - Recovery procedures

11. **Physical Security**
    - Physical access controls
    - Surveillance systems
    - Asset tracking
    - Environmental monitoring
    - Tamper protection

12. **Governance & Policies**
    - Security policies
    - Change management
    - Configuration management
    - Documentation completeness
    - Training & awareness

13. **Incident Readiness**
    - Incident response plan
    - Incident response team
    - Communication procedures
    - Forensics capabilities
    - Post-incident reviews

**Scoring:**
- 0-10 Punkte pro Kategorie
- Overall Security Score (0-100)
- Status: Draft/Completed/Approved/Expired

**Automatische Analysen:**
- Schwachstellen-Identifikation
- Priorisierung nach Criticality
- Handlungsempfehlungen
- Compliance-Gap-Analyse

### Risk Assessment (ISO 27005 / IEC 62443)

**Risk Dimensions:**

**1. Likelihood (Eintrittswahrscheinlichkeit):**
- 0-10 Score
- Rating: Very_Low / Low / Medium / High / Very_High
- Faktoren:
  - Threat Actor Capability
  - Motivation
  - Asset Exposure
  - Existing Controls
  - Historical Incidents

**2. Impact (Auswirkung):**

Fünf Impact-Dimensionen (jeweils 0-10):

- **Confidentiality Impact**
  - Data exposure severity
  - Sensitive information loss
  - Competitive disadvantage

- **Integrity Impact**
  - Data manipulation severity
  - Process manipulation impact
  - Safety implications

- **Availability Impact**
  - Downtime duration
  - Production loss
  - Recovery complexity

- **Safety Impact**
  - Personnel injury risk
  - Environmental damage
  - Public safety risk

- **Financial Impact**
  - Direct financial loss
  - Production loss value
  - Recovery costs
  - Regulatory fines
  - Reputation damage

- **Reputation Impact**
  - Brand damage
  - Customer confidence loss
  - Media attention

**Overall Impact:** Gewichteter Durchschnitt oder Maximum

**3. Risk Calculation:**

```
Risk Score = Likelihood × Impact
Risk Score Range: 0-100

Risk Level:
- 80-100: Critical
- 60-79:  High
- 40-59:  Medium
- 20-39:  Low
- 10-19:  Very_Low
- 0-9:    Negligible
```

**4. Risk Treatment:**

**Treatment Options:**
- **Avoid** - Activity stoppen, Asset aussondern
- **Mitigate** - Risiko reduzieren durch Controls
- **Transfer** - Risiko übertragen (Versicherung, Outsourcing)
- **Accept** - Risiko akzeptieren (dokumentiert)

**Controls:**
- Existing Controls (JSON) - Was ist bereits implementiert
- Planned Controls (JSON) - Was wird implementiert
- Control Effectiveness (0-10)

**5. Residual Risk:**

```
Residual Risk Score = Risk Score × (1 - Control_Effectiveness/10)
Residual Risk Level = (entsprechend der Skala)
```

**6. Risk Acceptance:**

- Risk Owner (Person)
- Acceptance Status (Pending/Accepted/Rejected)
- Acceptance Date
- Review Date (jährlich/halbjährlich)
- Acceptance Justification

**Automatische Risk Aggregation:**

```sql
-- Risiko für Equipment-Hierarchie
SELECT calculate_equipment_risk('Fertigungslinie A');
→ Aggregiertes Risiko aller zugeordneten Assets

-- Top 10 Risiken
SELECT * FROM asset_risk_assessments 
ORDER BY risk_score DESC 
LIMIT 10;

-- Risiko-Matrix
SELECT 
  likelihood_rating,
  impact_rating,
  COUNT(*) as asset_count,
  AVG(risk_score) as avg_risk
FROM asset_risk_assessments
GROUP BY likelihood_rating, impact_rating;
```

---

## Dashboards (React Frontend)

### 1. Executive Dashboard

**Zielgruppe:** Management, C-Level

**KPIs:**
- Total Asset Value (€)
- Total Assets Count
- Assets by Status (Active/Maintenance/Defect)
- Assets by Criticality (Mission-Critical Count)
- Security Score (0-100)
- Overall Risk Level
- Compliance Status (%)
- Top 10 Risks

**Charts:**
- Asset Value Trend (Line Chart)
- Assets by Type (Pie Chart)
- Assets by Location (Tree Map)
- Security Score Trend (Line Chart)
- Risk Distribution (Heat Map)
- Budget vs Actual (Bar Chart)

**Alerts:**
- Critical Vulnerabilities Detected
- High-Risk Assets
- Warranty Expiring Soon
- Maintenance Overdue

### 2. Operations Dashboard

**Zielgruppe:** Operations Manager, Plant Manager

**KPIs:**
- OEE (Overall Equipment Effectiveness)
- Availability (%)
- Performance (%)
- Quality (%)
- Downtime Today/This Week/This Month
- MTBF (Mean Time Between Failures)
- MTTR (Mean Time To Repair)
- Production Throughput

**Charts:**
- OEE Trend (Multi-Line Chart)
- Downtime Pareto (Bar Chart)
- Failure Analysis (Pie Chart)
- Production vs Target (Gauge)
- Equipment Status (Real-time Grid)

**Live Status:**
- Equipment Running/Stopped/Maintenance
- Active Alarms
- Performance Bottlenecks

### 3. Security Dashboard

**Zielgruppe:** CISO, Security Team

**KPIs:**
- Overall Security Score
- Critical Vulnerabilities Count
- High Risk Assets Count
- Unpatched Assets Count
- Assets in DMZ
- Assets with Remote Access
- Security Assessments Completed (%)

**Charts:**
- Security Score by Location (Heat Map)
- Vulnerability Severity Distribution (Stacked Bar)
- Patch Status (Pie Chart)
- Security Assessment Status (Progress Bars)
- Threat Actor Activity (Timeline)

**Alerts:**
- New Critical CVE
- Security Assessment Expired
- Failed Login Attempts
- Unauthorized Network Access

### 4. Compliance Dashboard

**Zielgruppe:** Compliance Officer, Auditor

**Standards:**
- IEC 62443 Compliance (%)
- NIS2 Compliance (%)
- ISO 27001 Compliance (%)
- ISO 13849 Safety Assets (Count)
- CE Marking Status

**Charts:**
- Compliance Status by Standard (Multi-Bar)
- Non-Compliant Assets (List)
- Certification Expiry (Gantt)
- Audit Findings (Trend)

**Documents:**
- Compliance Reports (PDF Export)
- Audit Trails
- Certifications Database

### 5. Financial Dashboard

**Zielgruppe:** CFO, Controlling

**KPIs:**
- Total Asset Value
- Total Depreciation
- Annual Operating Costs
- Annual Maintenance Costs
- Budget vs Actual
- Cost per Production Unit
- ROI per Equipment

**Charts:**
- Asset Value by Location (Tree Map)
- Cost Breakdown (Waterfall Chart)
- Depreciation Forecast (Area Chart)
- Budget Utilization (Gauge)
- Cost Center Comparison (Bar Chart)

**Financial Rollup:**
- Drill-down from Enterprise → Site → Line → Machine
- Real-time Cost Aggregation
- What-If Scenarios

### 6. Maintenance Dashboard

**Zielgruppe:** Maintenance Manager, Technicians

**KPIs:**
- Maintenance Overdue Count
- Preventive Maintenance Compliance (%)
- Calibration Due Count
- MTBF/MTTR per Asset
- Spare Parts Availability
- Work Orders Open/Closed

**Charts:**
- Maintenance Schedule (Calendar)
- MTBF Trend (Line Chart)
- Failure Modes (Pareto)
- Maintenance Costs (Bar Chart)
- PM Compliance (Gauge)

**Features:**
- QR Code Scanner (Mobile)
- Work Order Management
- Maintenance History Timeline
- Spare Parts Lookup

### 7. Network Topology Dashboard

**Zielgruppe:** Network Engineer, OT Engineer

**Features:**
- Interactive Network Map (D3.js/Cytoscape)
- Purdue Level Visualization
- VLAN Segmentation View
- Protocol Distribution
- Live Asset Status
- Network Performance Metrics

**Filters:**
- By Location
- By Network Zone
- By Purdue Level
- By Protocol
- By Criticality

**Export:**
- Network Diagram (PDF/PNG)
- Asset Inventory (Excel)
- Network Documentation

### 8. Vulnerability Management Dashboard

**Zielgruppe:** Security Team, OT Engineers

**KPIs:**
- Total Vulnerabilities
- Critical/High/Medium/Low Count
- Unpatched Vulnerabilities
- Mean Time to Patch (MTTP)
- Vulnerability Trend

**Charts:**
- CVSS Score Distribution (Histogram)
- Vulnerabilities by Vendor (Bar Chart)
- Patch Status Timeline (Gantt)
- Exploitability Analysis (Scatter Plot)

**Features:**
- CVE Database Integration
- Auto-Matching to Assets
- Patch Prioritization
- Remediation Workflow

---

## Automatische Analysen

### 1. Asset Discovery & Auto-Population

**OT Scanner läuft automatisch:**
- Nightly Scans (02:00-06:00)
- Protocol Detection
- Manufacturer Recognition (OUI Lookup)
- Model Detection (Protocol-specific)
- Firmware Detection
- Network Configuration

**Auto-Population Logic:**
```python
1. Scan findet Device: IP 192.168.1.100
2. MAC: 00:1B:1B:xx:xx:xx → OUI: Siemens
3. Protocol: S7 → Device Type: PLC
4. S7 Query → Model: S7-1500, Firmware: V2.9
5. Prüfe: Asset existiert? (IP/MAC Match)
6. Nein → Create new asset
   - Name: Auto-generated (PLC-192-168-1-100)
   - Manufacturer: Siemens
   - Model: S7-1500
   - Firmware: V2.9
   - IP: 192.168.1.100
   - MAC: 00:1B:1B:xx:xx:xx
   - Status: discovered
   - Discovery_Date: NOW()
7. Ja → Update existing asset
   - Last_Seen: NOW()
   - Firmware: V2.9 (wenn geändert)
```

### 2. Vulnerability Scanning & CVE Matching

**Automatischer Ablauf:**

```python
# Nightly Job: 03:00
1. Load all assets with (Manufacturer + Model + Firmware)
2. Generate CPE strings
   Example: "cpe:2.3:h:siemens:simatic_s7-1500:2.9:*:*:*:*:*:*:*"
3. Query NVD API for matching CVEs
4. Match results:
   - CVE-2023-12345: CVSS 9.8 (Critical)
   - CVE-2023-12346: CVSS 7.5 (High)
5. Create asset_cve_mapping entries
6. Calculate risk_score per asset
7. Send alerts for Critical/High CVEs
8. Update vulnerability dashboard
```

**Vendor Advisory Integration:**
- Siemens ProductCERT RSS Feed
- Rockwell Security Advisories
- Schneider Electric Cybersecurity Advisories
- Parsing & Matching

### 3. Financial Rollup & Cost Analysis

**Automatische Berechnungen:**

```sql
-- Jede Nacht: 01:00
1. Recalculate equipment_asset_value() für alle Equipment
2. Recalculate equipment_operating_cost()
3. Update depreciation für alle Assets
4. Calculate budget utilization per Cost Center
5. Generate cost variance reports
6. Predict next year's costs (Trend Analysis)
```

**Predictive Cost Analysis:**
- Linear Regression auf Operating Costs
- Seasonal Adjustments (Energiekosten)
- Maintenance Cost Forecasting (MTBF-based)

### 4. Risk Aggregation & Prioritization

**Automatische Risk Calculation:**

```python
# Bei jeder Risk Assessment Änderung
1. Calculate asset_risk_score
2. Aggregate risks für:
   - Location (all assets in location)
   - Equipment (all assets assigned)
   - Process (all assets in process)
   - Organization (all assets owned)
3. Update risk_level für Hierarchien
4. Identify Top 10 Risks (system-wide)
5. Notify Risk Owners (if threshold exceeded)
```

**Risk Heatmap:**
- Likelihood × Impact Matrix
- Color-coded (Green/Yellow/Orange/Red)
- Drill-down to Asset Level

### 5. Performance Analysis & OEE Calculation

**OEE Berechnung:**

```
OEE = Availability × Performance × Quality

Availability = (Operating Time / Planned Production Time) × 100
Performance = (Actual Output / Target Output) × 100
Quality = (Good Units / Total Units) × 100
```

**Automatische Analysen:**
- OEE Trend Analysis (Daily/Weekly/Monthly)
- Bottleneck Detection (welche Machine ist Limiting Factor)
- Downtime Pareto (Top Loss Reasons)
- Predictive Maintenance Alerts (MTBF-based)

### 6. Compliance Monitoring

**Automatische Checks:**

```python
# Daily Compliance Check: 06:00
1. Check all Safety-Critical Assets:
   - Safety Category assigned?
   - Performance Level assigned?
   - Last Inspection < 1 year?
   - Certificates valid?
2. Check all Assets:
   - Warranty expired? → Alert
   - Calibration due? → Alert
   - Maintenance overdue? → Alert
   - EOL reached? → Alert
3. Generate Compliance Report
4. Update Compliance Dashboard
```

**Standards Tracking:**
- IEC 62443: Security Assessments completed?
- ISO 13849: Safety Categories assigned?
- NIS2: Essential/Important Entity Compliance?


### 7. License Utilization & Optimization

**Automatische Analysen:**

```python
# Daily License Check
1. Count active assets → vs License Limit
2. Count active agents → vs License Limit
3. Count active users → vs License Limit
4. Forecast usage (next 3/6/12 months)
5. Recommend License Pack:
   - Current: 100 assets, using 95
   - Forecast: 110 assets in 3 months
   - Recommendation: Upgrade to 150-asset pack
6. Calculate cost savings (annual vs on-demand)
```

---

## License System

### License Types (4 Tiers)

### Module System (10+ Modules)

**Core Modules:**
1. **Asset Management** (immer inkludiert)
2. **Security Assistant** (Starter+)
3. **Risk Assistant** (Professional+)
4. **Compliance** (Professional+)
5. **Advanced Reporting** (Enterprise)
6. **Versioning** (Starter+, max versions depends on tier)
7. **CVE Management** (Professional+)
8. **Integration Hub** (Professional+)
9. **Analytics & ML** (Enterprise)
10. **Multi-Tenancy** (Enterprise)

**Add-On Modules (à la carte):**
- Additional Asset Packs (50/100/150/200/250/500/unlimited)
- Advanced Scanner Modules (PROFINET Pro, S7 Pro, etc.)
- Custom Dashboards
---

## Reporting System

### Built-In Reports (20+)

**Asset Reports:**
1. Asset Inventory Report (Full/Summary)
2. Asset by Location Report
3. Asset by Type Report
4. Asset Lifecycle Report
5. Asset Financial Report

**Financial Reports:**
6. Equipment Financial Rollup
7. Cost Center Analysis
8. Budget vs Actual Report
9. Depreciation Schedule
10. Total Cost of Ownership (TCO)

**Security Reports:**
11. Security Assessment Report
12. Vulnerability Report
13. Patch Status Report
14. Compliance Gap Analysis
15. Audit Trail Report

**Operations Reports:**
16. OEE Report
17. MTBF/MTTR Report
18. Maintenance Report
19. Downtime Analysis
20. Production Performance

### Custom Report Builder

**Features:**
- Drag & Drop Interface
- Field Selection (from all tables)
- Filter Builder (complex conditions)
- Grouping & Aggregation
- Sorting
- Chart Integration (10+ chart types)
- Template Library (50+ templates)

**Output Formats:**
- Excel (.xlsx)
- PDF
- CSV
- HTML

**Scheduling:**
- Once/Daily/Weekly/Monthly
- Email Distribution Lists
- FTP/SFTP Upload
- Webhook Trigger

---

## Standards Compliance

**Implementiert:**
- ✅ ISA-95 / IEC 62264 (Production Hierarchies)
- ✅ IEC 62443 (OT Security)
- ✅ ISO 13849 (Safety Categories)
- ✅ IEC 61508 (SIL Levels)
- ✅ ISO 27005 (Risk Management)
- ✅ NIS2 (Network & Information Security)
- ✅ Machinery Directive 2006/42/EC
- ✅ GDPR (Data Protection)

---

## Zusammenfassung

**Das OT/ICS Asset Management System bietet:**

✅ **Vollständige ISA-95 Compliance** - 4 separate Hierarchien  
✅ **React Frontend** - Modern, responsive, intuitiv  
✅ **8 Dashboards** - Executive, Operations, Security, Compliance, Financial, Maintenance, Network, Vulnerability  
✅ **Versionierung mit Check-Out/Check-In** - SPS, EPLAN, Doku, HMI, Configs  
✅ **Security & Risk Assessments** - IEC 62443, NIS2, ISO 27005  
✅ **Vulnerability Management** - Auto-CVE-Matching, Patch-Tracking  
✅ **Financial Rollup** - Rekursive Kostenberechnung  
✅ **10+ Automatische Analysen** - Discovery, Risk, Performance, Compliance, ML  
✅ **License System** - 4 Tiers, Module-basiert, flexibel  
✅ **Integrationen** - CMDB, SIEM, ERP, PLM  
✅ **Reporting** - 20+ Built-In, Custom Builder, Scheduling  
✅ **50+ ENUMs** - Standardisierte Werte  
✅ **~280 Asset-Felder** - Comprehensive  
✅ **Multi-Protocol Scanner** - PROFINET, S7, Modbus, SNMP, SSH  
✅ **Zone-Aware Architecture** - IT / Shopfloor getrennt  

**Ein System. Alles drin.**

---

**Bauer Automation Solutions**  
Hoher Weg 28, 59073 Hamm, Germany  
Owner: Dennis Bauer  
2025
