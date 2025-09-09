# M365 Purview DLP — Exfiltration Playbook

**Goal:** Prevent and respond to sensitive data egress via email, OneDrive/SharePoint, and endpoints.

## 1) Prereqs
- Purview DLP + Endpoint DLP onboarded
- Unified labeling client + Sensitivity labels (Confidential, Restricted)
- Catalog sensitive info types (SSN, PAN, PHI)

## 2) Policies
### Email (Exchange Online)
- Rule: External recipients + >= 1 Sensitive Info hit (e.g., 1× SSN OR 1× PAN)
- Action: Block send with user justification override; Alert to SecOps; Incident label = High

### SharePoint/OneDrive
- Rule: Sharing to external domains OR anonymous links on labeled files
- Action: Block, auto‑revoke sharing; Alert with file path + label + user

### Endpoint (Windows/macOS)
- Rule: Copy to USB/Cloud sync apps when label >= Confidential
- Action: Block with user justification; Capture evidence

## 3) Alerts → SIEM (Splunk)
- Ingest Purview DLP alerts (O365 Management API / M365 Defender)
- Normalize to `dlp_*` fields; sample SPL in `docs/splunk_dlp_spl.md`

## 4) Triage
- Validate true positive (file label/type, destination, business context)
- Scope: user’s last 24h activity; related assets; historical hits
- Risk: data volume, sensitivity, destination reputation

## 5) Respond
- Auto: Revoke sharing; Quarantine file; Notify user’s manager
- Manual: Interview user; Open IR ticket; Forensics (endpoint timelines)
- Contain: Temp block exfil channels (CASB session controls)

## 6) Lessons Learned
- Tune thresholds; Add exceptions for sanctioned workflows; Train users

**ATT&CK**: T1567, T1048
