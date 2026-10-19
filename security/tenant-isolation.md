# Your own database (tenant isolation)

## The problem we solve

Many multi-tenant products put every customer into **one big shared database** and rely only on software filters (“show rows where organisation = X”). A bug or misconfiguration in that filter can expose another organisation’s data.

HealthSetu takes a stronger approach for customer data.

## One organisation → one database

When your organisation is set up on HealthSetu:

1. Platform admins **provision** your organisation.
2. The system creates a **dedicated database** for that organisation (named for your tenant).
3. Your modules — CareSetu, RakhtSetu, SupplySetu, HRSetu, and others you subscribe to — store operational data **in that database**.
4. Staff from other organisations authenticate to **their** tenants and **their** databases. They have no path into yours.

<div class="callout">
  <strong>Cross-contamination eliminated at the storage layer:</strong> there is no shared “all patients in India” table that every hospital queries. Your donors, visits, stock, and employees are not mixed with another customer’s rows.
</div>

<figure class="media-frame">
  <p><em>Screenshot / diagram placeholder — provisioning shows a dedicated database name for the organisation (read-only for clients)</em></p>
  <figcaption>Suggested: <code>assets/screenshots/security-org-database.png</code> — blur secrets; show only that a distinct DB exists</figcaption>
</figure>

## What stays separate

| Data type | Isolated per organisation? |
|-----------|----------------------------|
| Patients, visits, consents (CareSetu) | Yes |
| Donors, units, issue records (RakhtSetu) | Yes |
| Stock, assets, vendors, POs (SupplySetu) | Yes |
| Employees, attendance, salary (HRSetu) | Yes |
| Your users, roles, barcode templates, SMTP settings | Scoped to your organisation |

## What this is not

- It does **not** replace hospital SOPs, physical access control, or staff training.
- It does **not** mean one staff login can see everything inside your org — **roles and capabilities** still apply (see <a href="#" data-hs-route="core/users-roles">Users & roles</a>).
- Platform operators who provision systems follow separate operational controls; day-to-day clinical users only access their own organisation.

## Questions owners often ask

**Can another hospital on HealthSetu open our donors?**  
No. Their login resolves to their organisation and their database.

**If we add a second branch under the same organisation, do we get another database?**  
Branches under the **same** organisation typically share that organisation’s tenant database. A **separate legal / customer organisation** gets its own database when provisioned separately.

**What if we leave the platform?**  
Teardown and data-handover processes are handled with your HealthSetu account team — ask for the exit / export arrangement in your contract.

## Related

- <a href="#" data-hs-route="security/azure-cloud">Hosted on Microsoft Azure</a>
- <a href="#" data-hs-route="security/access-and-privacy">Access, privacy & good practice</a>
- <a href="#" data-hs-route="security/overview">Security & compliance overview</a>
