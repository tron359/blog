---
title: DMARC, DKIM, SPF, and Email Validation
---

Spending more time today on email security investigational skills, a lot more straightforward than yesterday's SIEM honeypot setup.


Reading into how DKIM, DMARC, and SPF came to be.


The modernized version of SPF came first, but only verified the validity of the most recent sender's ip, provides no inherent protection against Return-Path/mailfrom modification, and doesn't work well for forwarded emails.


DKIM tries to lock down illicit usage and modification of domains by implementing cryptographic comparison of each email header against a central DNS record, both generated using a private/public key pair, proving the identity of the original sender.


Unfortunately, DKIM replay attacks take advantage of the check-once nature of the signature, allowing an attacker with access to the mail domain to send malicious (or legitimate) messages out to a controlled second address, then re-use the signed email for their design. 


DMARC doesn't entirely fix the above issues, but it allows for nuance by cooperating with DNS to convey treatment rules, enables easier forensics, improves filtering capabilities, and overall makes spoofing and misusing domains a more technically challenging exercise for a given actor.


None of these measures stop users from clicking links, but they do ease the OSINT process for personnel tasked with investigating phishing campaigns.
