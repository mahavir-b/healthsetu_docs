# Hosted on Microsoft Azure

HealthSetu runs on **Microsoft Azure** — Microsoft’s cloud platform used by enterprises and public-sector organisations worldwide.

## Why Azure matters to clients

| Topic | What you get |
|-------|----------------|
| **Enterprise cloud** | Applications and databases are hosted in Azure data centres, not on a random shared PC under someone’s desk |
| **Managed databases** | Organisation databases are provisioned and operated as Azure SQL / cloud database resources as part of the HealthSetu platform |
| **Scale & availability** | Capacity and uptime are designed around cloud operations (patches, failover patterns, and monitoring as operated by the HealthSetu team) |
| **Network & identity** | Traffic and admin access follow Azure-oriented security practices used for the HealthSetu deployment |

<figure class="media-frame">
  <p><em>Diagram placeholder — Users → HealthSetu apps on Azure → your organisation’s dedicated database</em></p>
  <figcaption>Suggested: <code>assets/screenshots/security-azure-architecture.png</code></figcaption>
</figure>

## How this pairs with tenant isolation

Azure hosts the **platform**. Your **dedicated organisation database** sits in that cloud environment as a **separate database** for your tenant.

```
Your staff (browser)
        ↓
HealthSetu apps (Azure)
        ↓
Your organisation’s database only  ←  not another hospital’s database
```

So you get both:

1. **Cloud hosting** (Azure) — professional infrastructure  
2. **Data isolation** (own database) — no cross-customer mixing  

## What clients do not need to run

You do **not** need to install SQL Server on a clinic PC for the production HealthSetu service, or manage Azure subscriptions yourself, unless your contract says otherwise (for example a special private deployment).

Day-to-day, staff only need:

- A supported browser  
- Your organisation’s HealthSetu URL  
- Their login  

## Region & residency

Ask your HealthSetu account contact for the **Azure region** used for your deployment and any data-residency commitments in your agreement. Document the answer in your organisation’s IT / compliance file.

<div class="callout callout--tip">
  For RFPs and audits, pair this page with <a href="#" data-hs-route="security/tenant-isolation">tenant isolation</a>: “Dedicated per-organisation database on Microsoft Azure.”
</div>

## Related

- <a href="#" data-hs-route="security/tenant-isolation">Your own database (tenant isolation)</a>
- <a href="#" data-hs-route="security/access-and-privacy">Access, privacy & good practice</a>
- <a href="#" data-hs-route="security/overview">Security & compliance overview</a>
