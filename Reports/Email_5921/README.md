# Phishing Email Analysis Report  

- **Case ID:** `sample-5821.eml`  
- **Date of Analysis:**  24/07/25 

---

## 1. Metadata & Header Analysis  
- **From:** `Het Nationale Energie Onderzoek <info.OLCVQD@omahamobiletruckrepairservice.com>`  
- **Sender:** `[CloudStorageSecurity] <info.QWVVCZ@omahamobiletruckrepairservice.com>`  
- **Return-Path:** `Bounce-TTTJUNPJVYKDKS@omahamobiletruckrepairservice.com`  
- **Message-ID:** `<783227476780902.9.TPN5031488552@draftpunk8.com>`  
- **Subject:** `Bevestig uw deelname aan het Nationale Energie Onderzoek`  
- **Originating IP:** `162.243.75.230`  

**Authentication Results**  

| Mechanism | Result    |
|-----------|-----------|
| SPF       | SoftFail  |
| DKIM      | None      |
| DMARC     | Fail      |
| CompAuth  | Fail      |

**Conclusion:** Email authentication failed — spoofed sender domain, unauthorized sending server.  

---

## 2. Body Content Analysis  
- **Theme:** Pretends to be *Het Nationale Energie Onderzoek* (National Energy Research).  

**Social Engineering Lures:**  
- **Authority:** “Official National Survey”  
- **Urgency:** “Selected in your postcode area”  
- **Reward:** “Win great prizes”  
- **Trust Abuse:** Banner states *“This message is from a trusted sender”*  

**Other Observations:**  
- **Primary CTA:** Bright orange button → external malicious link.  
- **Tracking:** Multiple hidden images (0x0 beacons) and affiliate-style tracking URLs.  

**Conclusion:** Classic reward-based phishing using **authority + urgency + reward + trust deception**.  

---

## 3. Indicators of Compromise (IOCs)  

### Domains  
- `draftpunk8.com` (originating domain)  
- `omahamobiletruckrepairservice.com` (spoofed sender domain)  
- `storage.googleapis.com/newera1/zzzzzzzzzcadosss.html` (malicious landing page)  
- `trkng.nl` (tracking)  
- `dondomatos.online` (tracking beacon)  
- `vesselwindplant.com` (fake unsubscribe)  
- `go2speed.org` (remote branding/tracking assets)  

### URLs  
- `hxxps[://]storage[.]googleapis[.]com/newera1/zzzzzzzzzcadosss[.]html`  
- `hxxps[://]som[.]trkng[.]nl/aff_i?offer_id=3147&file_id=5019&aff_id=1458`  
- `hxxps[://]hnerta[.]dondomatos[.]online/track/3FfFOW0wQeJ2gototrweuj0PFXXDNBSMBZKFYH0VBTR1943x0`  
- `hxxps[://]www[.]vesselwindplant[.]com/o-tgfg-t17-dcc45763532fbe2f0e127b9cf6640268`  
- `hxxps[://]media[.]go2speed[.]org/brand/files/sendt/3147/`  

### IPs  
- `162.243.75.230`  

---

## 4. Threat Assessment  
- **Type:** Phishing  
- **Goal:** Credential/data theft via malicious survey page  
- **Risk Level:** High  
- **Target Region:** Netherlands (Dutch-language lure)  

---

## 5. Recommendations  

### 1. Block IOCs  
- Blocklist all identified domains, IPs, and URLs.  

### 2. User Awareness  
- Train users not to trust unsolicited survey invitations or prize offers.  

### 3. Email Security  
- Strengthen **SPF**, **DKIM**, and **DMARC** enforcement for your organization.  

### 4. Incident Response  
- Review mail logs for other attempts from `162.243.75.230`.  
- Quarantine or delete similar messages.  
- Report abused services (Google Cloud Storage, affiliate trackers) to providers.  

---

## 6. Conclusion  
The analyzed sample (`sample-5821.eml`) is a **phishing email campaign** impersonating *Het Nationale Energie Onderzoek*.  

It leverages:  
- Spoofed headers  
- Cloud-hosted payloads  
- Reward-based lures  

to trick users into clicking a malicious link and providing personal information.  
