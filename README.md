# Riya Patel — Open Detection Rulepack & DLP Playbook

![Status](https://img.shields.io/badge/status-0.1.0-lightgrey)
![License](https://img.shields.io/badge/license-MIT-black)
![Build](https://github.com/<YOUR_GH_USERNAME>/riya-detections-and-dlp/actions/workflows/ci.yml/badge.svg)

A curated set of **Sigma** rules (portable to many SIEMs) with companion **Splunk SPL** and an **M365 Purview DLP playbook** for quick wins against common exfiltration and living‑off‑the‑land techniques. Mapped to **MITRE ATT&CK**.

---

## Contents
- `rules/sigma/` — Portable detections in Sigma YAML
- `rules/splunk/` — Native Splunk SPL queries
- `splunk/savedsearches.conf` — Example Splunk ES correlation searches
- `playbooks/dlp/m365/` — DLP policy & response guide
- `docs/` — Usage, mapping tables, and adopters
- `.github/` — CI and testimonial issue template

## Quick Start
```bash
# Clone
git clone https://github.com/RiyaPatel1510/Detections-and-Dlp
cd Detections-and-Dlp

# (Optional) Validate Sigma rules locally
pipx install sigma-cli || pip install --user sigma-cli
echo "Validating…" && sigma validate rules/sigma
```

### Use Sigma rules in your SIEM
- Use `sigma convert -t splunk -r rules/sigma -o build/splunk/` to generate SPL.
- Or copy ready‑made SPL from `rules/splunk/`.

### Import to Splunk ES
1. Copy stanzas from `splunk/savedsearches.conf` into your app’s `local/savedsearches.conf`.
2. Verify index/sourcetype/field names match your environment.

### DLP Playbook (M365 Purview)
Follow `playbooks/dlp/m365/Playbook.md` to:
- Classify data (sensitive info types, labels)
- Block/override risky egress (Exchange, SharePoint/OneDrive, Endpoints)
- Alerting + incident workflow
- Correlate DLP alerts in Splunk

## MITRE ATT&CK Coverage (sample)
- T1059.001 PowerShell — LoL download cradles
- T1105 Ingress Tool Transfer
- T1567 Exfiltration over Web Services
- T1048 Exfiltration over Alternative Protocol

See `docs/mapping.md`.
## 👥 Contributors

- [Ram Badhiwala](https://github.com/rambadhiwala) – Detection logic, DLP playbooks, SOC documentation

  
## Testimonials & Adopters
We welcome short quotes + impact metrics (FP↓, MTTR↓, scale). See `TESTIMONIALS.md` or open a **“Testimonial”** issue.

## License
MIT — see `LICENSE`.

## Security
Found a bug? See `SECURITY.md`.

## Citing
If you use this work, please cite via `CITATION.cff`.
