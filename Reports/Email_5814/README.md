# Phishing Email Analysis Report  

- **Sample:** `sample-5814.eml`  
- **Classification:** Phishing / Crypto Scam (BONK token)  
- **Analysis Tools:** Thunderbird, REMnux  

---

## 1. Overview  
This email attempts to trick the recipient into clicking on links to claim a **BONK cryptocurrency airdrop**.  

It leverages **SendGrid tracking links** for redirection and uses **mismatched headers/domains**.  

---

## 2. Header Analysis  
- **From:** `bonkcoinsolana@metafisicaguarani[.]com`  
- **Message-ID:** `<f799e034-25af-4a63-bb5d-d9d9c52b2ed8@resimpli[.]com>`  
- **Date:** Sat, 14 Sep 2024 21:05:15 +0000  
- **Importance:** High  
- **Reply-To:** *(not set, relies on From address)*  
- **Received Chain:** Routed through Microsoft Outlook infrastructure but originating from a suspicious external domain (`esab.edu.br`).  

**Observation:**  
Headers show misalignment:  
- From = `metafisicaguarani[.]com`  
- Message-ID = `resimpli[.]com`  
- Delivery via **SendGrid** (`ct.sendgrid[.]net`)  

---

## 3. Indicators of Compromise (IOCs)  

### Malicious / Suspicious Domains  
- `metafisicaguarani[.]com` – spoofed sender domain  
- `ct.sendgrid[.]net` – abused for link tracking and redirection  
- `stripocdn[.]email` – used for hosting images  
- `resimpli[.]com` – appears in Message-ID (misaligned)  

### Suspicious URLs  
1. `hxxps://u54903417.ct.sendgrid[.]net/asm/unsubscribe/?user_id=54903417&data=...`  
2. `hxxps://u54903417.ct.sendgrid[.]net/wf/open?upn=...`  
3. `hxxps://u54903417.ct.sendgrid[.]net/ss/c/...` *(Likely the phishing CTA)*  
4. `hxxps://etreozs.stripocdn[.]email/content/guids/.../rfgff.png` *(image only)*  

### Malicious Email Address  
- `bonkcoinsolana@metafisicaguarani[.]com`  

---

## 4. Techniques (MITRE ATT&CK Mapping)  
- **T1566.002** – Spearphishing via Service (SendGrid abuse)  
- **T1036** – Masquerading (crypto giveaway theme)  
- **T1204.002** – User Execution: Malicious Link  

---

## 5. Risk Assessment  
- **Phishing Risk:** High  
- **User Impact:** Possible credential theft or wallet compromise  
- **Technical Risk:** Redirects to attacker-controlled site hidden behind SendGrid tracking  

---

## 6. Recommendations  

1. **Block** the sender domain `metafisicaguarani[.]com` at the email gateway.  
2. **Detonate and analyze** SendGrid URLs in a sandbox to reveal the true phishing landing page.  
3. **Educate users** about ongoing *crypto airdrop* phishing scams.  
4. **Enforce** SPF, DKIM, and DMARC checks to reduce spoofed email entry.  
5. **Monitor mail logs** for other activity tied to `ct.sendgrid[.]net` campaigns.  
6. Always **defang malicious URLs** before sharing in reports.  

---

## 7. Final Verdict  
**Classification:** Phishing / Crypto Scam Campaign  

The message abuses **SendGrid redirection** to mask malicious URLs and impersonates a cryptocurrency airdrop.  
It is **not legitimate**.  
