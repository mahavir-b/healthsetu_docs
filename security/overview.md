# Security & compliance

HealthSetu is built so **your organisation’s data stays yours**. Clinics, blood banks, and hospitals on the same platform do not share a patient or donor database with each other.

<div class="callout callout--tip">
  <strong>In one line:</strong> each organisation gets its <strong>own database</strong> on <strong>Microsoft Azure</strong>, so another customer’s users cannot see or mix with your records.
</div>

## What this means for you

| Promise | What happens in practice |
|---------|---------------------------|
| **No cross-organisation contamination** | Clinic A’s patients, donors, stock, and payroll never live in Clinic B’s database |
| **Dedicated tenant database** | When your organisation is provisioned, HealthSetu creates a separate database for your data |
| **Azure cloud** | Applications and databases run on Microsoft Azure (enterprise cloud used worldwide for healthcare and government workloads) |
| **Access by role** | Even inside your organisation, staff only see screens their role allows |
| **Signed-in sessions** | Work requires a login; shared counters should sign out between users |

<figure class="media-frame">
  <p><em>Diagram placeholder — one organisation → one dedicated database (no shared patient tables across orgs)</em></p>
  <figcaption>Suggested: <code>assets/screenshots/security-tenant-isolation.png</code></figcaption>
</figure>

## Read next

1. <a href="#" data-hs-route="security/tenant-isolation">Your own database (tenant isolation)</a> — how we eliminate cross-contamination  
2. <a href="#" data-hs-route="security/azure-cloud">Hosted on Microsoft Azure</a> — where the platform runs  
3. <a href="#" data-hs-route="security/access-and-privacy">Access, privacy & good practice</a> — logins, roles, and day-to-day hygiene  

<figure class="video-frame">
  <p><em>Video placeholder — “Why your organisation has its own database” (3 min, for owners and admins)</em></p>
</figure>
