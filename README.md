# Module 2 Exercises - Core Cybersecurity Concepts

## MITRE ATT&CK Framework & Cyber Kill Chain Practice

---

## 📚 Overview

These hands-on exercises reinforce the cybersecurity fundamentals from Chapter 2 by applying threat modeling frameworks to real-world scenarios. You'll work with the MITRE ATT&CK framework and Cyber Kill Chain to analyze threats, understand attacker behaviors, and build detection strategies.

**Part of:** Module 2 - Core Cybersecurity Concepts  
**Estimated Time:** 4-6 hours total  
**Difficulty:** Intermediate

**Prerequisites:**
- Completion of Chapter 2 (CIA Triad, Kill Chain, Security Frameworks)
- Basic Python programming skills
- Jupyter Notebook environment

---

## 🎯 Learning Objectives

By completing these exercises, you will:

✅ **Understand** the MITRE ATT&CK framework structure and data model  
✅ **Navigate** ATT&CK tactics, techniques, and procedures (TTPs)  
✅ **Map** security incidents to Cyber Kill Chain phases  
✅ **Query** ATT&CK data programmatically using Python  
✅ **Profile** threat actors by analyzing their behavioral patterns  
✅ **Build** basic detection rules for common attack techniques  
✅ **Analyze** security coverage gaps using ATT&CK  
✅ **Apply** threat intelligence concepts to practical scenarios

---

## 📂 Exercise Structure

### Exercise 1: ATT&CK Foundations (60-90 min)
**File:** `01_ATT&CK_Foundations.ipynb`

**What You'll Learn:**
- Introduction to threat modeling frameworks
- Cyber Kill Chain phases and their defensive applications
- MITRE ATT&CK overview: tactics, techniques, sub-techniques
- ATT&CK data model: Groups, Software, Mitigations, Data Sources
- Navigating ATT&CK matrices and understanding object relationships

**Key Activities:**
- Explore the ATT&CK matrix structure
- Examine specific techniques in detail (T1566 Phishing, T1059 Command Execution)
- Analyze how techniques map to multiple tactics
- Load and query ATT&CK data using Python
- Visualize tactic and technique relationships

**Practical Skills:**
- Navigate the ATT&CK website effectively
- Understand technique descriptions and metadata
- Query ATT&CK STIX data programmatically

---

### Exercise 2: Programmatic Analysis (45-60 min)
**File:** `02_Programmatic_Analysis.ipynb`

**What You'll Learn:**
- Building reusable ATT&CK query functions
- Threat actor profiling using TTP analysis
- Comparing multiple threat groups
- Analyzing technique popularity and prevalence
- Understanding software (malware/tools) capabilities
- Identifying detection coverage gaps

**Key Activities:**
- Profile specific threat groups (APT29, APT28, Lazarus Group)
- Identify most commonly used techniques across all threat actors
- Analyze malware families by their ATT&CK technique coverage
- Build functions to automate threat intelligence queries
- Visualize TTP distributions and patterns

**Practical Skills:**
- Write Python code to query ATT&CK data
- Extract and analyze threat group behaviors
- Compare adversary TTP profiles
- Automate common threat intelligence tasks

---

### Exercise 3: Applied Analysis & Detection (60-90 min)
**File:** `03_Applied_Analysis_Detection.ipynb`

**What You'll Learn:**
- Reconstructing attacks using Kill Chain + ATT&CK
- Real-world case studies: WannaCry ransomware, APT espionage campaigns
- Building detection rules for high-priority techniques
- Creating organizational coverage assessments
- Identifying security monitoring gaps

**Key Activities:**
- Map WannaCry attack to both Kill Chain phases and ATT&CK techniques
- Analyze APT29 espionage campaign behaviors
- Write 3-5 detection rules with query logic (pseudo-SIEM syntax)
- Create organizational technique coverage matrix
- Prioritize detection improvements based on threat landscape

**Practical Skills:**
- Map incidents to ATT&CK techniques
- Develop detection logic for specific behaviors
- Assess organizational security posture using ATT&CK
- Prioritize security investments based on threat data

---

### Exercise 4: Advanced Topics & Practical Challenge (60-90 min)
**File:** `04_Advanced_Topics_Challenge.ipynb`

**What You'll Learn:**
- TTP sequence analysis and behavioral patterns
- Technique co-occurrence and relationship networks
- Introduction to ML-based threat attribution
- Automated threat intelligence reporting
- Comprehensive incident analysis

**Key Activities:**
- Analyze common technique pairs used by adversaries
- Build simple ML classifier for threat group prediction
- Practice incident analysis with simulated breach scenario
- Generate structured threat intelligence report
- Complete practical challenge: analyze defense contractor incident

**Practical Skills:**
- Recognize attack patterns and behavioral sequences
- Apply basic ML to security problems
- Conduct thorough incident analysis
- Communicate findings in professional threat intel format

---

## 🛠️ Setup Instructions

### 1. Environment Setup

**Option A: Using Existing Course Environment**
```powershell
# If you already have the course environment from Chapter 3/4 exercises
cd Module_02_Core_Cybersecurity_Concepts/Exercises
jupyter lab
```

**Option B: Create New Environment**
```powershell
# Create virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# Install dependencies
pip install jupyter pandas numpy matplotlib seaborn requests stix2 mitreattack-python

# Launch Jupyter
jupyter lab
```

**Option C: Google Colab (No local setup)**
1. Upload notebooks to Google Drive
2. Open with Google Colab
3. Install packages in first cell:
   ```python
   !pip install stix2 mitreattack-python
   ```

### 2. Verify Installation

```python
# Test imports
import pandas as pd
import matplotlib.pyplot as plt
from stix2 import MemoryStore
import requests
print("✓ All libraries ready!")
```

---

## 📖 How to Use These Exercises

### Recommended Approach

1. **Complete exercises in sequence** (1 → 2 → 3 → 4)
   - Each builds on previous concepts
   - Don't skip ahead!

2. **Read markdown cells carefully**
   - Context and explanations are important
   - Understand the "why" not just the "how"

3. **Run all code cells**
   - Don't just read the code
   - Observe outputs and results
   - Experiment by modifying values

4. **Complete practice problems**
   - Each notebook has embedded exercises
   - Try solving before looking at solutions
   - Learn from mistakes

5. **Take notes**
   - Document insights and questions
   - Note techniques relevant to your interests
   - Build your own reference materials

### Time Allocation

- **Exercise 1:** 60-90 minutes (foundation is critical!)
- **Exercise 2:** 45-60 minutes (coding practice)
- **Exercise 3:** 60-90 minutes (applied analysis)
- **Exercise 4:** 60-90 minutes (challenge problems)

**Total:** ~4-6 hours (can be split across multiple sessions)

---

## 🔑 Key Concepts Reference

### Cyber Kill Chain Phases

1. **Reconnaissance** - Identify targets, gather information
2. **Weaponization** - Create malicious payload/exploit
3. **Delivery** - Transmit weapon to target environment
4. **Exploitation** - Trigger vulnerability, gain initial access
5. **Installation** - Install persistent backdoor/implant
6. **Command & Control** - Establish two-way communication
7. **Actions on Objectives** - Achieve mission goals

### ATT&CK Tactics (14 in Enterprise Matrix)

1. **Reconnaissance (TA0043)** - Gather information for targeting
2. **Resource Development (TA0042)** - Establish operational resources
3. **Initial Access (TA0001)** - Enter target network
4. **Execution (TA0002)** - Run malicious code
5. **Persistence (TA0003)** - Maintain foothold
6. **Privilege Escalation (TA0004)** - Gain higher permissions
7. **Defense Evasion (TA0005)** - Avoid detection
8. **Credential Access (TA0006)** - Steal account credentials
9. **Discovery (TA0007)** - Learn about target environment
10. **Lateral Movement (TA0008)** - Move through network
11. **Collection (TA0009)** - Gather target data
12. **Command and Control (TA0011)** - Communicate with compromised systems
13. **Exfiltration (TA0010)** - Steal data
14. **Impact (TA0040)** - Disrupt, destroy, or manipulate systems

### ATT&CK Object Types

- **Tactics (TAxxxx)** - Adversary goals ("why")
- **Techniques (T1xxx)** - Methods to achieve goals ("how")
- **Sub-techniques (T1xxx.yyy)** - Specific implementation variants
- **Groups (G0xxx)** - Threat actors/APT organizations
- **Software (S0xxx)** - Malware and legitimate tools used maliciously
- **Mitigations (M1xxx)** - Defensive security controls
- **Data Sources (DS0xxx)** - Telemetry needed for detection

---

## 💡 Tips for Success

### Before Starting

- [ ] Review Chapter 2 content (CIA Triad, Security Frameworks)
- [ ] Ensure Python and libraries are installed
- [ ] Have ATT&CK website open for reference: https://attack.mitre.org
- [ ] Set aside uninterrupted time (60-90 min per exercise)

### While Working

✅ **Read carefully** - Markdown cells provide essential context  
✅ **Run sequentially** - Execute cells in order, don't skip  
✅ **Experiment** - Modify code, try different queries, break things!  
✅ **Take notes** - Document insights and new concepts  
✅ **Ask questions** - Use comments or discussion forums  
✅ **Think critically** - How would you apply this in practice?

### Common Pitfalls

❌ Skipping Exercise 1 (foundation is essential!)  
❌ Just reading without running code  
❌ Rushing through exercises  
❌ Ignoring error messages  
❌ Not attempting practice problems  
❌ Focusing on tools instead of concepts

---

## 🔗 Integration with Course

### Chapter 2 Connections

These exercises directly reinforce:
- **Section 2.1**: CIA Triad applied to threat analysis
- **Section 2.2**: Cyber Kill Chain practical application
- **Section 2.3**: Security frameworks in operational context
- **Section 2.4**: Threat intelligence fundamentals

### Preparation for Later Modules

- **Module 4**: Feature engineering for security (TTP-based features)
- **Module 7**: Network intrusion detection (ATT&CK-aligned signatures)
- **Module 10**: Adversarial ML (understanding attacker behaviors)

---

## 📚 Additional Resources

### Official MITRE Resources

- **ATT&CK Website:** https://attack.mitre.org
- **ATT&CK Navigator:** https://mitre-attack.github.io/attack-navigator/
- **Getting Started Guide:** https://attack.mitre.org/resources/getting-started/
- **GitHub Repository:** https://github.com/mitre-attack

### Tools & Libraries

- **mitreattack-python:** https://github.com/mitre-attack/mitreattack-python
- **ATT&CK Scripts:** https://github.com/mitre-attack/attack-scripts
- **Atomic Red Team:** https://github.com/redcanaryco/atomic-red-team
- **STIX/TAXII Documentation:** https://oasis-open.github.io/cti-documentation/

### Practice Datasets

- **Mordor Dataset:** Pre-recorded security events labeled with ATT&CK
- **Cyber Analytics Repository (CAR):** Detection analytics and rules
- **BRAWL Dataset:** Windows events tagged with techniques

---

## 🎓 Assessment & Next Steps

### Self-Assessment Questions

After completing the exercises, you should be able to answer:

1. What's the difference between ATT&CK tactics and techniques?
2. How does the Kill Chain relate to ATT&CK matrices?
3. Why do some techniques appear under multiple tactics?
4. How can you programmatically query threat group TTPs?
5. What data sources are needed to detect credential dumping?
6. How do you assess organizational ATT&CK coverage?

### Next Steps

1. **Review your work** - Go back through notebooks, check understanding
2. **Explore ATT&CK Navigator** - Create custom heatmaps and visualizations
3. **Apply to your context** - Think about your organization's threat landscape
4. **Continue to Module 3** - Apply these frameworks in ML feature engineering

### Going Deeper

**Optional Advanced Topics:**
- Map your organization's security controls to ATT&CK mitigations
- Build detection rules for your SIEM/EDR platform
- Analyze recent threat intelligence reports using ATT&CK
- Contribute to open-source ATT&CK projects

**Recommended Reading:**
- MITRE ATT&CK Design and Philosophy whitepaper
- "Practical Threat Intelligence and Data-Driven Threat Hunting" (O'Reilly)
- Verizon Data Breach Investigations Report (DBIR) - Annual publication

---

## ❓ Troubleshooting

**Problem:** Package import errors  
**Solution:** Ensure all packages installed: `pip list | grep stix2`

**Problem:** ATT&CK data download fails  
**Solution:** Check internet connection; notebooks cache data for offline use

**Problem:** Jupyter kernel crashes  
**Solution:** Restart kernel (`Kernel > Restart`), reduce dataset size if needed

**Problem:** Visualizations not displaying  
**Solution:** Ensure `%matplotlib inline` is executed at start of notebook

---

## 📞 Support

**Technical Issues:**
- Check troubleshooting section above
- Review notebook error messages carefully
- Consult Python library documentation

**Content Questions:**
- Refer to Chapter 2 textbook content
- Visit MITRE ATT&CK documentation
- Use course discussion forums

**ATT&CK Framework:**
- Website: https://attack.mitre.org
- Email: attack@mitre.org
- Twitter: @MITREattack

---

## 📝 Exercise Checklist

### Completion Tracker

- [ ] Setup environment and verify installation
- [ ] Complete Exercise 1: ATT&CK Foundations
- [ ] Complete Exercise 2: Programmatic Analysis  
- [ ] Complete Exercise 3: Applied Analysis & Detection
- [ ] Complete Exercise 4: Advanced Topics & Challenge
- [ ] Review self-assessment questions
- [ ] Document key insights and takeaways

### Ready to Start?

**Begin with:** `01_ATT&CK_Foundations.ipynb`

1. Open Jupyter Lab/Notebook
2. Navigate to the exercises folder
3. Open the first notebook
4. Read introduction carefully
5. Execute cells sequentially
6. Complete practice problems

**Good luck, and enjoy applying Chapter 2 concepts hands-on!** 🛡️

---

**Last Updated:** November 2025  
**Exercise Version:** 2.0  
**Course:** AI/ML Techniques in Cybersecurity (Module 2)
