**Incident report analysis**

| Summary | The organization I work for suffered a DDoS attack, compromising the internal network for two hours. This attack was triggered by a flood of incoming ICMP packets that caused network services to be disrupted, exploiting a vulnerability in an unconfigured firewall. The incident management team responded quickly by blocking incoming ICMP packets, temporarily stopping non-critical network services and restoring critical network services. |  |  |
| :---- | :---- | ----- | ----- |
| Identify | To strengthen security posture and prevent future incidents, the organization must implement or reinforce proactive risk identification and asset management processes. This includes: Conducting regular security audits of the internal network, systems, and devices to identify potential security breaches and misconfigurations. Establishing a comprehensive and up-to-date inventory of all IT assets, classifying them by business criticality. Implementing continuous vulnerability assessments to detect configuration flaws or outdated software before they can be exploited. Periodically reviewing and updating security policies and access privileges to ensure they are aligned with best practices and the operating environment. |  |  |
| Protect | Following the incident and to strengthen the organisation's protection posture, the network security team has implemented and/or reinforced the following key measures to mitigate the possibility of future attacks and safeguard critical assets: Implementation of a new firewall rule to drastically limit the rate of incoming ICMP packets, thus preventing flooding attacks. Enabling source IP address verification in the firewall to detect and block spoofed IP addresses in incoming ICMP packets. Deployment of advanced network monitoring software for early detection of abnormal traffic patterns that may indicate an attack. Integration and configuration of an IDS/IPS (Intrusion Detection/Prevention System) system to proactively filter and block ICMP traffic based on suspicious characteristics. |  |  |
| Detect | To ensure early and effective detection of similar cyber security incidents, the organisation must strengthen and optimise its continuous monitoring capabilities. This will involve: The implementation and advanced configuration of network monitoring software and SIEM (Security Information and Event Management) systems for centralised collection and analysis of firewall logs, traffic logs (NetFlow/IPFIX), IDS/IPS alerts and other relevant data. Proactive monitoring of abnormal network traffic patterns, paying special attention to: The geographic/physical origin of incoming and outgoing packet requests. The times of the day when these unusual requests and/or deliveries occur. The number and frequency of IP addresses attempting to access networks, especially from unexpected locations. Correlation of events and establishment of baselines of normal traffic to quickly identify deviations. Defining priority alerts and thresholds that trigger notifications to the security team upon detection of these patterns or suspicious behaviour (such as a flood of ICMP packets). |  |  |
| Respond | A robust incident response plan is crucial to minimise the impact of future events. Based on the DDoS attack suffered, the organisation's response plan will focus on the following key phases: Response Planning: Develop and maintain a detailed Incident Response Plan (IRP) that defines clear roles, responsibilities and procedures for each stage of the incident. Communication: Establish clear internal and external communication protocols, including stakeholders (management, legal team, customers if applicable) and, if necessary, relevant authorities. Analysis: Once an incident is detected, conduct a thorough forensic analysis to determine the root cause (as was done for the unconfigured firewall), the extent of the impact, the systems affected and the data compromised. This includes analysis of logs, network traffic and malicious artefacts. Containment: Implement swift measures to limit the impact and spread of the incident. In the case of a DDoS, this involves blocking malicious source IPs, using DDoS mitigation services, and isolating network segments if necessary, as was done when blocking the incoming ICMP packets. Eradication: Eliminating the threat and the vulnerabilities that enabled it. This means not only blocking the attack, but correcting the root cause (e.g., properly configuring the firewall, applying patches). Recovery (as part of the response): Although there is a specific 'Recovery' phase, the response plan should have initial steps to restore critical services immediately and stabilise the operation (as was done in this incident). Improvements: Incorporate lessons learned from each incident to continuously improve the response process. This includes the subdivision of incidents into categories for faster resolution by specialised teams and the continuous upgrading and reinforcement of detection systems (SIEM, IDS/IPS) and countermeasures such as firewalls. |  |  |
| Recover | The recovery phase is essential to ensure that the organisation can restore its affected capabilities and services to operational normality efficiently and safely, minimising downtime and data loss. Key actions in this phase include: Systems and Data Restoration: Implement clear procedures for the restoration of systems, applications and data from reliable and verified backups. Prioritise the restoration of the most critical services for business continuity. Post-Recovery Verification and Testing: Once systems have been restored, perform thorough verification and functionality testing to ensure that they are operating correctly, that the threat has been completely eradicated and that no latent vulnerabilities remain. This will include intensive monitoring of servers to detect any unusual traffic or anomalies after restoration. Recovery Communication: Maintain clear and timely communication with internal and external stakeholders on the status of recovery and resumption of services. Lessons Learned and Continuous Improvement: Document the recovery process, identifying lessons learned to improve disaster recovery plans (DRP) and business continuity plans (BCP). This may include optimising backup procedures, improving recovery times (RTOs) and recovery points (RPOs), and incorporating the aforementioned protection and detection measures to prevent future incidents. |  |  |

