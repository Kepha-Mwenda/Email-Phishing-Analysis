# Phishing Email Analysis Report

- **Date of Email:** 2023-12-22  
- **Subject:** `your parcel has been shipment`  
- **Sample ID:** `sample-2390.eml`  

---

## 1. Email Header Analysis
- **Sender Domain:** `skyfon-varna.eu`  
- **SPF Result:** None — no valid SPF record or Outlook could not verify.  
- **Relay Servers (Received chain):**  
  - `164.92.140.51` (DigitalOcean server, hostname `skyfon-varna.eu-NEW`)  
  - Passed through Microsoft SMTP protection (`BN8NAM11FT021.mail.protection.outlook.com`)  

**Suspicious Indicators:**  
- SPF failed (no authorized sender).  
- Sender domain mismatched Microsoft relay.  
- IP not consistent with expected Outlook mail servers.  

---

## 2. Email Body Analysis
- **Message Theme:** Fake package delivery failure.  

**Suspicious Elements:**  
- Urgency: Redelivery required within 48 hours.  
- Social Engineering: "Package team" fake branding.  
- Threat of fees & return.  
- Suspicious comments containing **MD5/SHA1-like strings** (likely markers or trackers).  

**Embedded Links:**  
- ```
  hxxps[://]skyfon-varna[.]eu/anti/

---

## 3. Extracted IOCs

### URLs
- `https://skyfon-varna.eu/anti/`

### IP Addresses
- `164.92.140.51`

### File Hashes
- `ea3fb9221bc639881aaea8d796515fad`  
- `667e0c30688ec02ee004ef7c13e65fd9`

---

## 4. Threat Intelligence
- **Domain Reputation:** `skyfon-varna.eu` flagged as suspicious (likely compromised or registered for phishing).  
- **IP WHOIS Info:** Hosted on **DigitalOcean** (Netherlands).  

---

## 5. Verdict
- **Classification:** Phishing attempt.  

**Reasoning:**  
- SPF check failed.  
- Domain impersonates delivery service.  
- Malicious link leads to suspicious `/anti/` path.  
- Confirmed suspicious by **VT/urlscan.io** scan results of `skyfon-varna.eu`.  

