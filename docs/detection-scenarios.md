# Detection Scenarios

## Scenario 1 — SSH Reconnaissance

**Objective:** generate network reconnaissance activity and verify that Suricata telemetry reaches Wazuh.

**Observed result:** 13 Suricata events were recorded for the controlled SSH reconnaissance activity.

**Investigation focus:**
- Suricata alert signature
- SSH destination port
- Source/destination information
- Wazuh ingestion of IDS events

## Scenario 2 — SSH Password Guessing

**Objective:** generate a small number of controlled failed SSH authentication attempts and investigate them in Wazuh.

**Observed result:** five authentication attempts were generated and all five were visible in Wazuh. The controlled test found no valid password.

**Investigation focus:**
- `sshd` decoder
- Failed authentication events
- Source information
- Authentication-failure classification

## Scenario 3 — File Integrity Monitoring

**Objective:** demonstrate host-based detection of a suspicious configuration-file modification.

**Observed result:** Wazuh FIM detected the modification and reported changes to file size, timestamp and cryptographic hashes. The event was assigned rule level 7.

**Investigation focus:**
- Syscheck/FIM event
- Modified file path
- Integrity attributes
- Rule severity

## Scenario 4 — SQL Injection Detection

**Objective:** generate controlled web-application attack telemetry using DVWA and investigate it through Wazuh.

**Observed result:** Apache access telemetry was collected by Wazuh and classified as a Level-6 web attack. The event was associated with MITRE ATT&CK T1190.

**Investigation focus:**
- Apache access log
- Web-access decoder
- Suspicious request activity
- Wazuh rule classification
- ATT&CK mapping
