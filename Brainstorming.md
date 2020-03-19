# Real World ICS Incidents

## Definitions
- ICS: 

## Important People & Companies
- Michael Assante (+)
- Robert Lee (Dragos)
- Austin Scott (Dragos)

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

### Electric Power System in Ukraine 2015
- First time a cyber attack caused an electrical outage (67 substations disconnected at distribution level)
- 250.000 people in the dark
- Stage 2: 6 months learning about the environment (looking for assets and found 700 Windos PCs).
- The attackers effectively became remote operators.
- After 6 months the attackers started to disconnect power and uploaded malware to serial-to-ethernet devices.
- Not a scalable attack.

### "CRASHOVERRIDE" (Electric Power System) in Ukraine 2016
- At transmission level
- The attackers leraned from 2015 and made the attack scalable
- Blueprint, not a targeted attack

### 2017 TRISIS (Saudi Arabia)
- A lot of information about this incident is incorrect
- Petrochemical plant
- Attack was designed to kill people
- Attacker got a second chance and failed again

## Problems / Challenges
- ICS systems become more and more homogeneous -> attacks become scalable and replicatable
- Companies often solely adopt IT security controls
- Most of the attackers accessed the ICS directly from the internet
- Wrong or out-dated documentation (architecture diagrams etc.)
- Poor visibility for IR (e.g. no aggregated logging)
- Accidental malware infection crossing over from IT
- Shared network access with supply chain providers
- Most of the ICS which think they are air-gapped aren't

## Countermeasures
- We should focus more on behaviours and TTPs instead of anomalies
- MFA wherever possible for remote access
- Risk based vulnerability patching

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

## MITRE ATT&CK for ICS
- Knowledge base of adversary tactics and technics based on intelligence-driven data
- There is a mapping from activity groups to MITRE ATT&CK ICS designation number (+ common tactic)
- Top tactics observed:
  - Persisting using compromised accounts and identity management services
  - Modify control logic
  - Multiple specialized (international) threat actor teams which work together
- Most dangerous tactics:
  - Safety system compromise
  - Engineering destructive events triggered during recovery process
  - Increased use of ransomware
  - OSINT collection and analysis of regulatory information release

## Resources

### Whitepapers
- Hacking Chemical Plants for Competition and Extortion
- Dragos ICS Vulnerabilities / Threat Landscape / Front-Line Lessons Learned

## Certifications
- [GRID Certification](https://www.giac.org/certification/response-industrial-defense-grid)