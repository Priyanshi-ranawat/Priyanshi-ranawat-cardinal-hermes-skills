# Threat model

The workflow assumes every email-controlled field may be adversarial.

| Threat | Example | Required response |
|---|---|---|
| Instruction override | Message content attempts to replace the assistant's governing policy | Flag the attempt and do not treat it as an instruction |
| Secret exfiltration | Message content requests credentials or hidden configuration | Refuse and disclose no secret value |
| Role impersonation | Message content presents itself as a higher-privilege role | Treat it only as quoted message content |
| Urgency manipulation | Message content pressures the assistant to bypass confirmation | Preserve the approval requirement |
| Recipient substitution | Body asks to reply to a different address | Require explicit human confirmation of the exact recipient |
| Malicious link | Link requests login or credential entry | Do not open automatically; flag for review |

Pattern detection reduces risk but does not prove content is safe. Keep external permissions narrow and enforce send approval in application code rather than relying only on model behavior.
