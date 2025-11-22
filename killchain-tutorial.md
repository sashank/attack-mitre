# Cyber Kill Chain & MITRE ATT&CK: Practical Guide

## Exercise Reference Material for Module 2

---

## 📖 Purpose

This guide provides the conceptual foundation for the Module 2 exercises. It explains the Cyber Kill Chain and MITRE ATT&CK frameworks that you'll apply programmatically in the Jupyter notebooks.

**Use this guide to:**
- Understand framework concepts before coding
- Reference during exercise completion
- Review theory while analyzing threats

---

## Part 1: Threat Modeling Frameworks

### Why We Need Structured Frameworks

**The Problem:**
- Cyber threats are complex and evolving
- Unstructured threat data is hard to analyze
- Communication gaps between security teams
- Difficulty measuring defensive effectiveness

**The Solution:**
Standardized frameworks provide:
- Common language for describing threats
- Structured approach to analysis
- Consistent methods for comparison
- Measurable metrics for improvement

### Evolution of Threat Models

1. **Signature-Based Detection** (1990s)
   - Simple pattern matching
   - Effective against known threats only
   - Easily evaded by polymorphism

2. **Cyber Kill Chain** (2011)
   - Linear attack progression model
   - Defensive opportunities at each phase
   - Strategic planning perspective

3. **MITRE ATT&CK** (2013-present)
   - Behavior-focused, non-linear
   - Detailed technical implementations
   - Operational detection emphasis

---

## Part 2: The Cyber Kill Chain

### Overview

Developed by Lockheed Martin in 2011, the Cyber Kill Chain models intrusion attempts as a sequential process with seven distinct phases.

**Key Principle:** "Breaking any link in the chain stops the attack"

### The Seven Phases

#### 1. Reconnaissance
**Goal:** Identify and research targets

**Attacker Activities:**
- Passive information gathering (OSINT, social media)
- Active scanning (network reconnaissance, vulnerability scanning)
- Social engineering research
- Supply chain analysis

**Defensive Opportunities:**
- Web application firewalls blocking scans
- Honeypots/honeytokens to detect reconnaissance
- Security awareness training
- Threat intelligence about targeting patterns

**ATT&CK Mapping:** TA0043 Reconnaissance tactics

---

#### 2. Weaponization
**Goal:** Create deliverable malicious payload

**Attacker Activities:**
- Coupling exploit with backdoor
- Creating malicious documents (weaponized PDFs, Office docs)
- Building custom malware or modifying existing tools
- Preparing watering hole infrastructure

**Defensive Opportunities:**
- Threat intelligence sharing (indicators of compromise)
- Sandbox analysis of suspicious files
- Understanding adversary tools and techniques

**ATT&CK Mapping:** TA0042 Resource Development tactics

**Note:** This phase typically occurs outside victim environment - hardest to detect!

---

#### 3. Delivery
**Goal:** Transmit weapon to target environment

**Delivery Methods:**
- Email (phishing, spear-phishing)
- Web (drive-by downloads, watering holes)
- USB/removable media
- Supply chain compromise
- Social engineering

**Defensive Opportunities:**
- Email filtering and sandboxing
- Web proxy blocking malicious sites
- User security awareness training
- Endpoint protection

**ATT&CK Mapping:** TA0001 Initial Access tactics

**Key Point:** Often the first detectable phase!

---

#### 4. Exploitation
**Goal:** Trigger vulnerability to gain initial access

**Exploitation Targets:**
- Software vulnerabilities (CVEs)
- Zero-day exploits
- Misconfigurations
- Weak authentication
- Social engineering (tricking users)

**Defensive Opportunities:**
- Patch management
- Vulnerability scanning
- Exploit prevention (DEP, ASLR)
- Application whitelisting

**ATT&CK Mapping:** TA0002 Execution tactics

---

#### 5. Installation
**Goal:** Install persistent backdoor or implant

**Installation Methods:**
- Registry modifications (Run keys)
- Scheduled tasks
- Services
- DLL side-loading
- Bootkit/rootkit installation

**Defensive Opportunities:**
- Host-based intrusion prevention
- Application whitelisting
- Integrity monitoring
- Privileged access management

**ATT&CK Mapping:** TA0003 Persistence tactics

**Critical Phase:** This is where attackers establish long-term foothold!

---

#### 6. Command and Control (C2)
**Goal:** Establish two-way communication channel

**C2 Techniques:**
- HTTP/HTTPS beaconing
- DNS tunneling
- Encrypted channels
- Cloud services (legitimate services as C2)
- Peer-to-peer networks

**Defensive Opportunities:**
- Network traffic analysis
- DNS monitoring
- Proxy/firewall blocking suspicious connections
- Behavioral analytics

**ATT&CK Mapping:** TA0011 Command and Control tactics

**Key Insight:** Breaking C2 can stop attack even after compromise!

---

#### 7. Actions on Objectives
**Goal:** Achieve mission goals

**Objectives Vary by Attacker:**
- **Financial:** Ransomware, payment fraud
- **Espionage:** Data theft, intellectual property
- **Disruption:** DDoS, system destruction
- **Influence:** Disinformation, manipulation

**Defensive Opportunities:**
- Data loss prevention (DLP)
- Network segmentation
- Privileged access monitoring
- Backup and recovery planning

**ATT&CK Mapping:** Multiple tactics - Collection (TA0009), Exfiltration (TA0010), Impact (TA0040)

---

### Kill Chain Limitations

**Challenges:**
- **Linear model** - Modern attacks aren't always sequential
- **Single-phase focus** - Doesn't capture parallel activities
- **Limited detail** - High-level phases lack operational specificity
- **Outdated assumptions** - Cloud, insider threats, supply chain attacks don't fit well

**Solution:** Complement with MITRE ATT&CK for detailed behavioral analysis!

---

## Part 3: MITRE ATT&CK Framework

### What is ATT&CK?

**ATT&CK = Adversarial Tactics, Techniques, and Common Knowledge**

A globally-accessible knowledge base of adversary behaviors based on real-world observations.

**Key Characteristics:**
- **Behavior-focused** (not malware-focused)
- **Technology-agnostic** (where possible)
- **Community-driven** (continuously updated)
- **Freely available** (public knowledge base)

### ATT&CK vs. Kill Chain

| Aspect | Cyber Kill Chain | MITRE ATT&CK |
|--------|------------------|--------------|
| **Structure** | 7 linear phases | 14 tactics × ~200 techniques |
| **Granularity** | Strategic phases | Operational procedures |
| **Flexibility** | Sequential steps | Non-linear, parallel |
| **Focus** | Attack progression | Adversary behaviors |
| **Use Case** | Strategic planning | Detection & response |
| **Updates** | Static (2011) | Quarterly releases |

**Relationship:** Kill Chain provides strategic view, ATT&CK provides operational detail

---

### ATT&CK Data Model

#### Object Hierarchy

```
Tactics (14) - "WHY" adversaries do things
  ↓
Techniques (~200) - "HOW" they achieve tactical goals
  ↓
Sub-techniques (~400) - Specific implementation variants
  ↓
Procedures - Real-world examples from threat groups
```

#### Primary Object Types

**1. Tactics (TAxxxx)**
- Adversary's tactical goals
- 14 tactics in Enterprise matrix
- Answer "Why is the adversary doing this?"

Example: TA0003 Persistence - "Maintain foothold in environment"

**2. Techniques (T1xxx)**
- Methods to achieve tactical objectives
- ~200 techniques across all tactics
- Answer "How does the adversary do it?"

Example: T1053 Scheduled Task/Job - "Use task scheduler for execution"

**3. Sub-techniques (T1xxx.yyy)**
- Specific variants of techniques
- Introduced in 2020 for better granularity
- More precise behavioral descriptions

Example: T1053.005 Scheduled Task (Windows Task Scheduler specifically)

**4. Groups (G0xxx)**
- Threat actors, APT organizations
- Tracked by security industry
- Associated with specific TTP sets

Example: G0016 APT29 (Cozy Bear) - Russian state-sponsored group

**5. Software (S0xxx)**
- Malware families
- Legitimate tools used maliciously

Example: S0154 Cobalt Strike - Post-exploitation framework

**6. Mitigations (M1xxx)**
- Security controls to prevent techniques
- Maps techniques → defensive measures

Example: M1040 Behavior Prevention on Endpoint - Blocks malicious code execution

**7. Data Sources (DS0xxx)**
- Types of telemetry for detection
- Required logging/monitoring

Example: DS0009 Process - Monitor process creation and execution

---

### The 14 Enterprise Tactics

#### Pre-Attack Phase

**1. Reconnaissance (TA0043)**
- Gather information to plan operations
- Examples: Scanning, OSINT, social media research

**2. Resource Development (TA0042)**
- Establish resources to support operations
- Examples: Acquire infrastructure, develop capabilities

#### Attack Execution Phase

**3. Initial Access (TA0001)**
- Get into the network
- Examples: Phishing, exploiting public-facing apps, valid accounts

**4. Execution (TA0002)**
- Run malicious code
- Examples: PowerShell, scripting, user execution

**5. Persistence (TA0003)**
- Maintain foothold across restarts
- Examples: Registry run keys, scheduled tasks, services

**6. Privilege Escalation (TA0004)**
- Gain higher-level permissions
- Examples: Process injection, access token manipulation

**7. Defense Evasion (TA0005)**
- Avoid detection
- Examples: File deletion, obfuscation, disabling security tools

**8. Credential Access (TA0006)**
- Steal account credentials
- Examples: Credential dumping, keylogging, brute force

**9. Discovery (TA0007)**
- Learn about target environment
- Examples: System info, network discovery, account discovery

**10. Lateral Movement (TA0008)**
- Move through the network
- Examples: Remote services, pass-the-hash, WMI

**11. Collection (TA0009)**
- Gather data of interest
- Examples: Data from local system, clipboard, screen capture

**12. Command and Control (TA0011)**
- Communicate with compromised systems
- Examples: Application layer protocols, encrypted channels

**13. Exfiltration (TA0010)**
- Steal data from network
- Examples: Exfil over C2, cloud accounts, physical media

**14. Impact (TA0040)**
- Disrupt, destroy, manipulate
- Examples: Data encryption (ransomware), defacement, DDoS

---

### Technique Deep Dive Example

**T1566: Phishing**

**Tactic:** Initial Access (TA0001)  
**Description:** Adversaries send messages to gain access or information

**Sub-techniques:**
- T1566.001: Spearphishing Attachment (malicious file)
- T1566.002: Spearphishing Link (malicious URL)
- T1566.003: Spearphishing via Service (social media, etc.)

**Detection Data Sources:**
- Application Log: Content
- Network Traffic: Content/Flow
- File: Creation

**Mitigation Strategies:**
- M1049: Antivirus/Antimalware
- M1031: Network Intrusion Prevention
- M1017: User Training
- M1054: Software Configuration (Office macro blocking)

**Real-World Usage:**
- Used by: APT28, APT29, Lazarus Group, FIN7, +100 other groups
- Common in: 85%+ of intrusions

**Why Important:** Most common initial access vector!

---

### Multiple Tactic Mapping

Some techniques achieve multiple tactical goals:

**Example: T1053 Scheduled Task/Job**

Maps to 3 tactics:
1. **Execution** - Runs scheduled code
2. **Persistence** - Survives reboots
3. **Privilege Escalation** - Can run with elevated permissions

**Lesson:** Blocking one technique can prevent multiple attack outcomes!

---

## Part 4: Practical Application

### Integrating Kill Chain + ATT&CK

**Use Kill Chain for:**
- Strategic communication with management
- High-level attack phase identification
- Breaking attacks into defensive phases
- Planning layered defense strategy

**Use ATT&CK for:**
- Detailed behavioral analysis
- Building specific detection rules
- Comparing threat actors
- Measuring detection coverage
- Operational security operations

### Example: Ransomware Attack Analysis

#### Kill Chain View:
1. Reconnaissance - Target research
2. Weaponization - Ransomware + exploit prepared
3. Delivery - Phishing email sent
4. Exploitation - Macro executes payload
5. Installation - Persistence established
6. C2 - Beacon to attacker infrastructure
7. Actions - Encrypt files, demand ransom

#### ATT&CK Detailed View:
- **Initial Access:** T1566.001 (Spearphishing Attachment)
- **Execution:** T1204.002 (User Execution: Malicious File)
- **Persistence:** T1547.001 (Registry Run Keys)
- **Defense Evasion:** T1027 (Obfuscated Files), T1070.004 (File Deletion)
- **Discovery:** T1082 (System Information), T1083 (File Discovery)
- **C2:** T1071.001 (Web Protocols)
- **Impact:** T1486 (Data Encrypted for Impact), T1490 (Inhibit System Recovery)

**Insight:** Kill Chain shows progression, ATT&CK shows specific behaviors to detect!

---

## Part 5: Detection & Defense

### Detection Strategy

**Layered Approach:**
1. **Signature-based** - Known malware, IOCs
2. **Behavior-based** - ATT&CK technique patterns
3. **Anomaly-based** - Deviations from baseline

### Building Detection Rules

**Template:**
```
Technique: [ATT&CK ID and Name]
Tactic: [Which tactical goal]
Data Source: [Required telemetry]
Detection Logic: [Query/rule pseudocode]
False Positive Likelihood: [Low/Medium/High]
Priority: [Critical/High/Medium/Low]
```

**Example - Detecting Credential Dumping:**
```
Technique: T1003.001 (LSASS Memory)
Tactic: Credential Access
Data Source: Process Monitoring
Detection Logic:
  - Process accessing lsass.exe memory
  - Creation of .dmp files
  - Execution of known credential tools (mimikatz, procdump)
False Positive: Low (legitimate tools rare)
Priority: Critical
```

### Coverage Assessment

**Questions to Ask:**
1. Which techniques can we detect with current tools?
2. What data sources are we missing?
3. Which high-priority techniques have detection gaps?
4. How do we compare to peer organizations?

**ATT&CK Navigator Tool:**
- Visualize coverage as heatmap
- Export/share organizational layers
- Track improvements over time

---

## Part 6: Applying to Exercises

### Exercise 1: Foundations
You'll explore ATT&CK structure programmatically:
- Load ATT&CK data via STIX/TAXII
- Query tactics, techniques, relationships
- Understand object connections

### Exercise 2: Programmatic Analysis
You'll build analysis functions:
- Profile threat groups by TTPs
- Compare multiple adversaries
- Analyze technique popularity
- Identify detection gaps

### Exercise 3: Applied Analysis
You'll map real attacks:
- WannaCry ransomware → Kill Chain + ATT&CK
- APT espionage campaign → Detailed TTP mapping
- Build detection rules
- Assess organizational coverage

### Exercise 4: Advanced Topics
You'll perform practical analysis:
- Pattern recognition in TTP sequences
- Introduction to ML-based attribution
- Comprehensive incident analysis
- Threat intelligence reporting

---

## Part 7: Key Takeaways

### Conceptual Understanding

✅ **Frameworks complement each other**
- Kill Chain: Strategic, high-level
- ATT&CK: Operational, detailed

✅ **Behavior over indicators**
- IOCs change constantly
- Behaviors are more persistent

✅ **Defense in depth**
- No single control prevents all attacks
- Layer defenses across kill chain phases

✅ **Continuous improvement**
- Threat landscape evolves
- Detection must adapt quarterly

### Practical Skills from Exercises

After completing the notebooks, you'll be able to:
- Navigate ATT&CK matrices confidently
- Query threat data programmatically
- Map incidents to frameworks
- Build basic detection rules
- Assess security coverage gaps
- Communicate using common language

---

## 📚 Additional Reading

### Essential Resources

- **MITRE ATT&CK Website:** https://attack.mitre.org
- **ATT&CK Design Philosophy:** https://attack.mitre.org/docs/ATTACK_Design_and_Philosophy_March_2020.pdf
- **Cyber Kill Chain Paper:** Hutchins, Cloppert, Amin (2011) - Lockheed Martin

### Tools

- **ATT&CK Navigator:** https://mitre-attack.github.io/attack-navigator/
- **Atomic Red Team:** Testing techniques locally
- **MITRE Caldera:** Automated adversary emulation

### Practice

- **Mordor Dataset:** Pre-recorded events with ATT&CK labels
- **Cyber Analytics Repository (CAR):** Detection analytics
- **BRAWL Dataset:** Windows events tagged with techniques

---

## ❓ Study Questions

Test your understanding before the exercises:

1. What's the difference between a tactic and a technique?
2. Why do some techniques map to multiple tactics?
3. How does the Kill Chain relate to ATT&CK tactics?
4. What's the most common initial access technique?
5. Which kill chain phase is hardest to detect? Why?
6. What data sources are needed to detect credential dumping?
7. How would you assess your organization's ATT&CK coverage?

**Answers:** Revisit relevant sections above, then verify in exercises!

---

**Ready for hands-on practice?** Proceed to `01_ATT&CK_Foundations.ipynb`!

**Remember:** Theory enables practice. Use this guide as reference while working through exercises.

---

**Last Updated:** November 2025  
**Version:** 2.0  
**Course:** Module 2 - Core Cybersecurity Concepts
