# Real World ICS Incidents

## Definitions
- OT: Voting machines, (I)IoT, [?] + ICS
- ICS (as defined by NIST): [?] + SCADA 

## Important People & Companies
- Michael Assante (+)
- Robert Lee (Dragos)
- Austin Scott (Dragos)
- Bryson Bort (SCYTHE)

## Purdue Reference Model

- OT Layers
  - L0: Physical Process / Field Network (Sensor & Actuators)
  - L1: Control Network (Programmable Logic Controller (PLC) & Remote Terminal Unit (RTU))
  - L2: Supervisory Network (Operational/SCADA)
  - L3: Operational Control Network (DMZ)
- IT Layers
  - L4 (Enterprise)
  - DMZ, Web/Email Servers, Internet

## Methodologies

### ICS Cyber Kill Chain (Robert Lee)
- Stage 1: Access to the environment
  - Recon
  - Weaponization / Targeting
  - Delivery
  - Exploit
  - Install / Modify
  - C2
  - Act
- Stage 2: Develop insights/knowledge or malicious software
  - Develop
  - Test
  - Deliver
  - Install / Modify
  - Execute ICS attack

- A lot of ICS attacks are not exploit-based

## Incidents

- RISI Database: https://www.risidata.com
- ICS-CERT Alerts from the US Government: https://www.us-cert.gov/ics/alerts

### BlackEnergy in Ukraine 2015
- Electric Power System in West Ukraine
- First known cyberattack on civilian infrastructure
- First time a cyber attack caused an electrical outage (67 substations disconnected at distribution level)
- 230.000-250.000 people without power in freezing temperatures
- BlackEnergy malware used for recon
- No ICS/SCADA protocol or PLC payloads, but mostly on the IT side
- Initial infiltration via macro documents -> user credential compromise for access, manual manipulation of SCADA controls (HMI/rdesktop)
- Firmware attacks (Uninterruptable Power Supply (UPS), serial-to-ethernet)
- Stage 2: 6 months learning about the environment (looking for assets and found 700 Windows PCs).
- The attackers effectively became remote operators.
- After 6 months (dwell time) the attackers started to disconnect power and uploaded malware to serial-to-ethernet devices.
- Not a scalable attack.

### Industroyer/CRASHOVERRIDE (Electric Power System) in Ukraine 2016
- Kiev (capital)
- 700.000 people (1/5 of Kiev) without power in freezing temp (?)
- Much more complex than Blackenergy
- CRASHOVERRIDE framework used
- Required significant pre-positioning
- Many ICS/SCADA protocol payloads, many behaviors on both IT & OT side
- Credential capture via Mimikatz (could be detected with a signature-based approach) -> Compromised user accounts & attacker created accounts
- Used LoL (?) commands to pivot into ICS/SCADA via Windows LM/SQL
- Spoofed ICS/SCADA command messages
- At transmission level
- The attackers learned from 2015 and made the attack scalable
- Blueprint, not a targeted attack
- Unclear why it was not more widespread
- Infection vector (kill chain stage 1) is unknown
- Threat actors involved:
  - ELECTRUM

### 2017 Triton/Trisis/Hatman (Saudi Arabia)
- A lot of information about this incident is incorrect
- Petrochemical plant
- Attack was designed to kill people
- Attacker got a second chance and failed again
- Contained Safety PLC (SPLC) / Safety Instrumented System (SIS) payloads, relied on operator placement & execution
- Modified control logic (reprogrammed SPLC/SIS to allow unsafe conditions to persist)
- Exploited a vulnerability (injected custom PowerPC payload exploiting a vulnerability in the device firmware to escalate privileges disabling RAM/ROM consistency checking etc.)

## Problems / Challenges
- ICS systems become more and more homogeneous -> attacks become scalable and replicable
- Companies often solely adopt IT security controls
- Most of the attackers accessed the ICS directly from the internet
- Wrong or out-dated documentation (architecture diagrams etc.)
- Poor visibility for IR (e.g. no aggregated logging)
- Accidental malware infection crossing over from IT
- Shared network access with supply chain providers
- Most of the ICS which think they are air-gapped aren't

## Countermeasures
- We should focus more on behaviors and TTPs instead of anomalies
- MFA wherever possible for remote access
- Risk-based vulnerability patching

## Vulnerabilities
- 24% related to the ICS protocols, the rest is "deep" in the ICS
- 74% are exploitable over the network
- 55% have an available patch but no alternative remediation
- 26% have no patch available

## Threat Actors
- Could maybe be used for splitting up incidents
- 11 in total
- 7 activity groups operate across verticals
- Parisite (since 2017)
- Wassonite (since 2018)

## Nation-state Threat Actors
- USA
- UK
- China
- Israel
- Russia
- North Korea
- Iran

## MITRE ATT&CK for ICS
- Knowledgebase of adversary tactics and technics based on intelligence-driven data
- There is a mapping from activity groups to MITRE ATT&CK ICS designation number (+ common tactic)
- Top tactics observed:
  - Persisting using compromised accounts and identity management services
  - Modify control logic
  - Multiple specialized (international) threat actor teams which work together
- Most dangerous tactics:
  - Safety system compromise
  - Engineering destructive events triggered during the recovery process
  - Increased use of ransomware
  - OSINT collection and analysis of regulatory information release

## Certifications
- [GRID Certification](https://www.giac.org/certification/response-industrial-defense-grid)

## Misc Thoughts
- The time from initial compromise to the actual ransomware attack -- known as a "dwell time" -- is, on average, three days, according to FireEye. (https://www.zdnet.com/article/most-ransomware-attacks-take-place-during-the-night-or-the-weekend/)