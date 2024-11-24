Context:
This proof of concept was created while working through the Zerologon room on TryHackMe. The room provides hands-on learning for understanding this vulnerability and its real-world implications.

Overview:
Zerologon (CVE-2020-1472) is a critical vulnerability found in the Microsoft NetLogon Remote Protocol (MS-NRPC), a key component of Active Directory used for authenticating users and machines. This proof of concept showcases how a flaw in the cryptographic implementation of the ComputeNetlogonCredential function can be exploited.

Root cause:
A poor implementation of AES-CFB8 encryption that uses a harcoded initialization vector set to all zeros.
