### Email Authentication Methods

- **SPF (Sender Policy Framework)**  
  Defines which mail servers are authorized to send emails on behalf of a domain. Helps prevent email spoofing.  

- **DKIM (DomainKeys Identified Mail)**  
  Uses cryptographic signatures to verify that an email’s content has not been altered and that it was truly sent by the domain.  

- **DMARC (Domain-based Message Authentication, Reporting, and Conformance)**  
  Builds on SPF and DKIM, allowing domain owners to set policies on what to do if authentication fails (none, quarantine, reject) and provides reporting.  

- **ARC (Authenticated Received Chain)**  
  Preserves SPF, DKIM, and DMARC results when emails are forwarded through intermediate servers, ensuring trust in the original authentication.  

### Email Authentication Summary

- **SPF** → Who is allowed to send.  
- **DKIM** → Message integrity + authenticity.  
- **DMARC** → Policy enforcement + reporting.  
- **ARC** → Preserves authentication results across forwarders.

---

### Security Controls

- **SPF Pass/Fail**  
  - *Pass*: The sending server is authorized by the domain’s SPF record.  
  - *Fail*: The sending server is not listed in the SPF record → could be spoofed.  

- **DKIM Pass/Fail**  
  - *Pass*: The cryptographic signature is valid, confirming the message wasn’t altered and matches the domain.  
  - *Fail*: The signature doesn’t match or is missing → message may be forged or altered.  

- **DMARC Policy (none, quarantine, reject)**  
  - *None*: Only collects reports, no enforcement.  
  - *Quarantine*: Suspicious emails go to spam/junk.  
  - *Reject*: Emails that fail SPF/DKIM alignment are rejected outright.  

- **Mail Transfer Agents (MTAs)**  
  - Servers that send, relay, or deliver emails.  
  - They process authentication checks (SPF, DKIM, DMARC) during transmission.  

- **Quarantine / Reject**  
  - *Quarantine*: The receiving server accepts the email but delivers it to spam/junk instead of the inbox.  
  - *Reject*: The receiving server refuses the email → it never reaches the user.  

---

### Email Analysis

- **Headers**  
  Metadata about the path, sender, and authentication.  

- **Body HTML / Raw Body**  
  Where phishing links, malicious code, or social engineering content is embedded.  

- **IOCs (Indicators of Compromise)**  
  URLs, IPs, hashes, domains, attachments, etc.  

- **Defanging**  
  Altering malicious URLs/domains (e.g., `hxxp://bad[.]com`) to make them safe in reports.  

---

### Attack Techniques

- **Social Engineering**  
  Tricks used to manipulate recipients (urgency, fake offers, threats).  

- **Phishing**  
  Fraudulent attempt to steal sensitive info via fake emails.  

- **Spoofing**  
  Faking an email address/domain to look legitimate.  

- **Attachments**  
  Possible vectors for malware (PDF, Word, ZIP, EXE).  
