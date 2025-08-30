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
