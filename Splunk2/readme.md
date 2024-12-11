# Splunk 2: Boos of the SOC TryHackMe room Walkthrough

Welcome to my walkthrough for the Splunk2 room on TryHackMe! This room provided an immersive experience in leveraging Splunk as a Security Information and Event Management (SIEM) tool to analyze and investigate a simulated cyberattack.

In this scenario, I utilized Splunk to trace the attack lifecycle, aligning the findings with the MITRE ATT&CK Framework. The attack began with a spear-phishing attachment that granted the attacker initial access. From there, the malicious activity unfolded across various stages:
  Execution: Leveraging PowerShell, scripting, Windows Management Instrumentation, and scheduled tasks.
  Persistence: Creating a rogue account for long-term access.
  Privilege Escalation: Abusing scheduled tasks to gain elevated permissions.
  Defense Evasion: Disabling security tools and clearing indicators of compromise.
  Lateral Movement: Exploiting remote file inclusion to spread through the network.
  Exfiltration and Collection: Extracting sensitive data for external use.
  Command and Control (C2): Using commonly used ports, data encoding, and remote file copy to maintain control.

This walkthrough highlights how Splunk's powerful log analysis capabilities and dashboards can be used to identify, correlate, and mitigate threats in real time. Whether you're new to Splunk or exploring its applications in incident response, this guide provides actionable insights and techniques to enhance your cybersecurity skillset.

Dive in to learn how I dissected this attack and mapped each stage to real-world tactics and techniques!
