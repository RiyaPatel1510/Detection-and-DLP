/* Purview DLP Alert Triage */
index=o365* sourcetype="o365:management:activity" Workload="DLP" Action=PolicyMatch
| eval label=coalesce(SensitivityLabel, FileLabel)
| stats count values(PolicyDetails) as policies values(UserId) as users by label, FilePath, Destination, Severity
| sort - count
