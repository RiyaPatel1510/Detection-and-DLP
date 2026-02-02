# M365 DLP – Email Data Exfiltration Playbook

## Alert Description
Triggered when sensitive data is sent externally via email.

## Initial Checks
- Sender email address
- Recipient domain
- File attachment type
- DLP policy triggered

## Evidence to Collect
- Email headers
- Attachment metadata
- User activity history

## Decision Criteria
- Business justification?
- Sensitive data classification?
- Repeated behavior?

## Response Actions
- Block email (if pending)
- Notify user
- Escalate to Tier-2 if confirmed

## Escalation Criteria
- Repeated violations
- Sensitive data confirmed
- External malicious recipient
