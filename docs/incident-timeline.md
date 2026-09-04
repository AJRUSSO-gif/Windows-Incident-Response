# Incident Timeline

**Incident ID:** IR-2026-0001  
**Classification:** Unauthorized Remote Access  
**Severity:** High  
**Status:** Resolved  
**Time Zone:** EDT

> **Disclosure Notice:** This timeline is based on a real-world cybersecurity incident. Organizational identifiers, usernames, hostnames, network information, and other sensitive details have been removed or generalized. The incident identifier is fictional and used solely for portfolio documentation.

---

## 08:02 — Incident Reported

- End user reported unexpected workstation behavior after interacting with what appeared to be a QuickBooks confirmation prompt.
- Unauthorized ScreenConnect remote-access software had been downloaded and installed without the user's informed authorization.
- An external actor successfully established interactive remote control of the workstation.

## 08:04 — Initial Indicators of Compromise

Initial indicators included:

- Unauthorized ScreenConnect installation.
- Active remote-control session.
- Loss of exclusive user control over the workstation.
- Unexpected software installation associated with the deceptive prompt.

Based on these observations, the event was treated as an active cybersecurity incident.

## 08:05 — Immediate Containment

Because the responding technician was not physically present at the location, containment instructions were provided to the end user by telephone.

The user was instructed to:

1. Immediately disconnect the workstation from the corporate network.
2. Power down the workstation.

These actions terminated the observed remote session and prevented continued network communication from the affected endpoint.

The workstation remained isolated pending on-site investigation.

## 08:10 — Incident Response Initiated

- Responding technician was off-site when the incident occurred.
- Travel to the affected location was initiated.
- Remote administrative access to the environment was not available.
- Detailed infrastructure and endpoint investigation therefore could not begin until on-site arrival.
- The affected workstation remained powered down and disconnected from the network.

## 11:30 — On-Site Arrival

- Verified that the affected workstation remained powered off.
- Verified that the endpoint remained disconnected from the corporate network.
- Began infrastructure assessment and endpoint investigation.

## 11:35 — Infrastructure Assessment

Available Active Directory, DNS, and Windows authentication information was reviewed for indications of:

- Unauthorized account activity.
- Unexpected privileged authentication.
- Administrative account usage.
- Authentication originating from unexpected systems.
- Potential credential abuse.
- Evidence suggesting lateral movement.

The available evidence did not identify unauthorized privileged or administrative logons.

Observed authentication activity was consistent with known user credentials and expected domain activity.

No evidence of lateral movement was identified within the telemetry available during the investigation.

## 11:45 — Credential Remediation

Because the unauthorized actor had obtained interactive access to the user's workstation, the affected credentials were treated as potentially exposed.

Actions included:

- Resetting the affected user's domain password.
- Allowing the credential change to replicate through the domain.
- Preparing a known-clean workstation for continued business operations.

## 12:00 — Endpoint Examination

Examination of the affected workstation identified three ScreenConnect installation directories and associated services.

The investigation examined:

- Installed remote-access components.
- Running and configured services.
- Persistence mechanisms.
- Startup entries.
- Scheduled tasks.
- Installation artifacts.
- Remaining executables and supporting files.

## 12:10 — Persistence Removal

- Identified ScreenConnect services were stopped.
- Associated services were disabled to prevent automatic restart.
- Two ScreenConnect installation directories were successfully removed.

## 12:20 — Locked Component Investigation

A remaining application component could not initially be removed because of system permissions and/or an active file lock.

Remediation included:

- Adjusting file ownership and permissions as required.
- Renaming the affected component to break the application dependency.
- Rebooting the workstation to release active file locks.
- Continuing removal after restart.

## 12:45 — Eradication

- Remaining ScreenConnect components were removed.
- Associated installation package was deleted.
- Endpoint was examined for remaining ScreenConnect services, executables, installation directories, scheduled tasks, startup entries, and installation artifacts.

No remaining ScreenConnect components were identified during validation.

## 12:55 — Post-Eradication Validation

Post-remediation checks confirmed that:

- Identified ScreenConnect installations had been removed.
- Associated ScreenConnect services were no longer present or active.
- Identified persistence mechanisms had been removed.
- The previously observed unauthorized remote-access mechanism was no longer operational.

Available Active Directory, DNS, and authentication evidence was reviewed again as part of scope validation.

No evidence of compromise involving additional endpoints, privileged accounts, Active Directory, or DNS infrastructure was identified within the available telemetry.

## 13:00 — Recovery

- Affected user's newly reset credentials were applied to a known-clean workstation.
- Original endpoint remained under administrative control until remediation and validation were completed.
- Normal business operations were restored.
- Incident was classified as contained, eradicated, recovered, and resolved based on the evidence available during the investigation.

---

## Investigation Limitations

The environment did not have centralized SIEM telemetry or enterprise EDR forensic capabilities available during the investigation.

Scope determination therefore relied on available Windows endpoint artifacts, Active Directory authentication information, Windows event information, DNS and infrastructure observations, configured services, persistence mechanisms, and direct endpoint examination.

Accordingly, statements such as **"no evidence of lateral movement was identified"** indicate that no such activity was discovered within the telemetry and artifacts available during the investigation. They should not be interpreted as proof that additional malicious activity was technically impossible.

---

[Return to main case study](../README.md)
