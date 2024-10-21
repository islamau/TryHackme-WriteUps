In this CTF challenge on TryHackMe, my objective was to investigate a Windows machine that had been compromised by an attacker. The task involved performing forensic analysis to uncover what actions the hacker may have taken, what methods were used for the compromise, and how the system was affected. This challenge simulated a real-world incident response scenario, requiring a methodical and multi-faceted approach to gather and analyze clues left behind by the intruder.

The investigation was carried out using various Windows-native tools such as PowerShell, Event Viewer, Task Scheduler, and Windows Firewall. These tools allowed me to gather valuable data from different parts of the system, including the system logs, scheduled tasks, and firewall rules. By piecing together the information from these sources, I was able to track the activities of the attacker, analyze any suspicious behavior, and understand the potential impact of the attack on the system.
Tools Used:

    PowerShell: For querying system information, retrieving event logs, and performing detailed investigative tasks.
    Event Viewer: To examine system, security, and application logs for signs of unusual activities.
    Task Scheduler: To identify any suspicious or unauthorized tasks that might have been scheduled by the attacker.
    Windows Firewall: To check for any firewall rule changes or network communications that could indicate malicious activity.

In this write-up, I will document the steps I followed during the investigation, share the key findings, and discuss how I pieced together the clues to understand the attacker’s tactics, techniques, and procedures (TTPs). The aim is to provide insights into a real-world incident response process and how you can use similar tools to analyze a compromised system effectively.
