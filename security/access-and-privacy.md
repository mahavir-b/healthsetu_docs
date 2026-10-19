# Access, privacy & good practice

Technical isolation (own database + Azure) is only half of security. The other half is **how your staff use the system**.

## Inside your organisation

| Control | What to do |
|---------|------------|
| **Named logins** | Every staff member has their own user — do not share passwords at the counter |
| **Roles** | Give reception, doctor, lab, and HR only the capabilities they need (<a href="#" data-hs-route="core/users-roles">Users & roles</a>) |
| **Disable leavers** | Turn off access the same day someone leaves |
| **Sign out** | On shared PCs, sign out between users |
| **Least privilege for admins** | Limit who can change SMTP, roles, and organisation settings |

## Privacy when using HealthSetu

- Do not paste real patient / donor identifiers into public tickets or WhatsApp groups.
- Prefer demo data when capturing **training screenshots** for this help site.
- Treat prints, consent PDFs, and salary slips as confidential physical documents.

## Indian healthcare context

HealthSetu modules are designed for Indian clinical and operational workflows (including areas such as consent, ABDM-related flows where enabled, and HR/payroll practices). Your organisation remains responsible for:

- Policies under applicable law (including privacy obligations such as DPDP where they apply to you)  
- Medical and blood-bank licence requirements  
- Internal audit and SOP compliance  

Use HealthSetu as the **system of record** your SOPs describe — isolation and Azure hosting support that; they do not replace your licence conditions.

<div class="callout callout--warn">
  Never send production database credentials, SMTP passwords, or API keys to staff chat or email threads that are not secured for secrets.
</div>

## Related

- <a href="#" data-hs-route="security/tenant-isolation">Your own database (tenant isolation)</a>
- <a href="#" data-hs-route="security/azure-cloud">Hosted on Microsoft Azure</a>
- <a href="#" data-hs-route="security/overview">Security & compliance overview</a>
