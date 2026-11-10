# Email, branding & settings

Admins configure how the organisation looks and how messages leave the system. Each area is a tab in the organisation admin console.

## What you can configure

| Tab | Effect for staff / patients |
|-----|-----------------------------|
| **Profile** | Organisation name, address, and contact details — used on letterheads and prints |
| **Branding** | App name, primary colour, logo, and support email shown in the portal |
| **Email server** | SMTP for invites, vendor mails, and clinic notices |
| **Communications** | WhatsApp Business connection — see <a href="#" data-hs-route="core/communications">WhatsApp & communications</a> |
| **Payment QR** | UPI QR for blood request payments in RakhtSetu |
| **Barcodes** | Label templates — see <a href="#" data-hs-route="core/barcodes">Barcodes & labels</a> |
| **ID cards** | Staff ID card designs |
| **Customize functionality** | Turn module screens and fields off, and add custom fields |
| **Configuration** | Lookup values the modules use (for example blood component types) |

## Email server

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/core-settings.png" alt="Email server settings" />
  <figcaption><strong>Email server</strong> tab: SMTP host, port, TLS, and from-address. Use <strong>Send test email</strong> after every change.</figcaption>
</figure>

The SMTP password is stored encrypted in HealthSetu Core. Re-enter it only when it changes.

## Payment QR

Payment QR shows a **UPI QR** when a blood request needs payment in RakhtSetu.

1. Set **Enabled** to Yes.
2. Enter the **UPI ID (VPA)** and payee name. HealthSetu then generates a dynamic QR with the amount filled in.
3. Optionally set a **reserve flat fee**.
4. If you have no UPI ID, give a **static QR image URL** instead (used only when the UPI ID is blank).
5. Check the preview, then **Save payment QR**.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/core-payment-qr.png" alt="Payment QR settings" />
  <figcaption>Payment QR: UPI ID, payee, reserve fee, and an optional static QR fallback.</figcaption>
</figure>

## ID cards

1. Pick a **vanilla format** (Clinical, Formal, Warm, Colorful, Quiet) and choose **Import vanilla** — or **Import all**.
2. Use **New version** on a row to copy a card before you change it.
3. Open the designer to adjust the layout, then print cards from the employee record.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/core-id-cards.png" alt="ID card formats" />
  <figcaption>ID cards: import a vanilla format first; each import adds a new version (Formal 2, Warm 2, and so on).</figcaption>
</figure>

## Customize functionality

Choose a module screen (for example **HRSetu → Employees → Employee form**). Then:

- Untick screens or built-in fields your organisation does not use.
- **Add custom field** for anything extra you need on the record.

Required fields (such as employee number and name) cannot be turned off.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/core-customize.png" alt="Customize functionality" />
  <figcaption>Customize functionality for the HRSetu employee form: screens across the top, built-in fields below.</figcaption>
</figure>

## Good practice

- Send a **test email** after changing SMTP.
- Keep the Profile address and phone accurate — CareSetu prints and certificates use organisation identity.
- Changes usually apply on the **next** request or login; tell staff if something looks cached.

<div class="callout callout--tip">
  Clinic letterhead gaps (name only, no address) are almost always empty organisation profile fields — fill them in the <strong>Profile</strong> tab.
</div>
