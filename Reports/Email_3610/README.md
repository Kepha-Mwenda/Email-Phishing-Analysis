# Phishing Email Analysis Report  

- **Case ID:** `sample-3610.eml`  
- **Date of Analysis:** 26 August 2025  

---

## 1. Email Header Analysis  
- **From Address:** `Viagra/Cialis-0,36$/0,54$" <best.pharmacy.online@hotmail.com>`  
  - Spoofed Hotmail address to appear legitimate.  
- **Return-Path:** `best.pharmacy.online@hotmail.com`  
  - Domain/IP mismatch confirms spoofing.  
- **Received Path:** Suspicious relay hops  
  - `187.16.75.146` (failed SPF validation)  
  - `5.82.149.238` (unknown origin)  
  - `cfdenselr[.]com`  
  - `alkoholic[.]net`  
  - `mail.webhostings4u[.]com`  

**Authentication Checks:**  
- SPF: Fail / None  
- DKIM: None / Failed  
- DMARC: Fail  
- CompAuth: Fail  

**Conclusion:** Spoofed Hotmail address used. Email authenticity checks failed.  

---

## 2. Email Body Analysis  
- **Subject:** `Your 5% off rebate offer`  
- **Body Content:**  
  - Promotion of Viagra/Cialis with discount lure.  
  - **Malicious URL:**  
    - `hxxp://charlottewebvideo[.]com/f.html`  
  - **Harvesting Emails:**  
    - `ex.pharmacy.online@gmail.com`  
    - `ex.pharmacy.online4@gmail.com`  

**Obfuscation Techniques:**  
- Large `<style>` blocks with junk data to bypass spam filters.  
- Possible spam kit artifact (`phishing@pot`).  

---

## 3. Social Engineering Indicators  
- **Emotional Appeal:** Exploits financial savings temptation.  
- **Brand Abuse:** Uses Hotmail + “pharmacy” branding.  
- **Urgency:** “5% off rebate” creates artificial urgency.  

**Conclusion:** Classic pharmaceutical spam phishing.  

---

## 4. Indicators of Compromise (IOCs)  

| Type   | Value |
|--------|-------|
| **IP** | 187.16.75.146, 5.82.149.238 |
| **Domain** | cfdenselr[.]com, alkoholic[.]net, mail.webhostings4u[.]com, charlottewebvideo[.]com |
| **Email** | best.pharmacy.online@hotmail.com, ex.pharmacy.online@gmail.com, ex.pharmacy.online4@gmail.com |
| **URL** | hxxp://charlottewebvideo[.]com/f.html |

---

## 5. Findings  
- Pharmaceutical spam campaign with potential payload delivery.  
- SPF/DKIM/DMARC checks failed — spoofing confirmed.  
- Contains malicious external link + harvesting addresses.  
- Uses obfuscated HTML to bypass spam filters.  
- Employs social engineering through discount lure.  

---

## 6. Recommendations  

### 1. Immediate Actions  
- Block identified IOCs (IPs, domains, URLs).  
- Flag sender emails in filters.  

### 2. Detection & Monitoring  
- Ingest IOCs into SIEM.  
- Monitor outbound traffic to `charlottewebvideo[.]com`.  
- Hunt for compromised users (clicked/replied).  

### 3. Email Security Enhancements  
- Enforce strict SPF, DKIM, DMARC reject policies.  
- Deploy advanced spam filtering for obfuscated HTML.  

### 4. User Awareness  
- Train users on spotting **discount scams**.  
- Reinforce: *“Do not click suspicious links.”*  

### 5. Threat Intel Sharing  
- Share IOCs with ISACs / MISP platforms.  

---

## 7. Conclusion  
The analyzed email (`sample-3610.eml`) is a **pharmaceutical spam phishing attempt** leveraging spoofed Hotmail headers and failed authentication.  

It uses discount offers to lure victims into:  
- Clicking a malicious link: `charlottewebvideo[.]com/f.html`  
- Contacting attacker-controlled emails.  

This is part of a known spam/phishing campaign. **Blocking IOCs and raising awareness are critical mitigation steps.**  
