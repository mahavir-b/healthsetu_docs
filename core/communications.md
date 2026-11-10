# WhatsApp & communications

HealthSetu Communications sends **appointment reminders**, **report and prescription delivery**, and keeps a **patient inbox** over WhatsApp.

## Who owns what

| Item | Owner |
|------|-------|
| WhatsApp Business Account, phone number, Meta billing | Your hospital / clinic |
| Message templates approved by Meta | Your hospital (HealthSetu helps you set them up) |
| Connection settings and secrets | Stored encrypted in HealthSetu Core |

HealthSetu adds no markup on WhatsApp messaging. Meta bills your business account directly.

## Connect WhatsApp (admins)

1. In the organisation admin console, open the **Communications** tab.
2. Set **Enabled** to Yes.
3. Enter the business name, display phone number, **Phone number ID**, and **WhatsApp Business Account ID (WABA)** from Meta Business Manager.
4. Paste the **access token**, **app secret**, and a **webhook verify token**.
5. **Save WhatsApp connection**.
6. Under **Send a test message**, send a template message to a test number and confirm it arrives.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/core-comms.png" alt="WhatsApp connection settings" />
  <figcaption>Communications tab: WhatsApp Business connection on top, test message below.</figcaption>
</figure>

## Template or free text?

| Message type | When it can be sent |
|--------------|---------------------|
| **Template** | Any time — needs a Meta-approved template |
| **Free text** | Only within 24 hours of the patient’s last message to you |

Reminders and report delivery use templates. Replies in the patient inbox can be free text while the 24-hour window is open.

<div class="callout callout--warn">
  Treat the access token and app secret like passwords. Paste them only into this screen, never into email or chat.
</div>

## Email

Invites, vendor emails, and clinic notices go out over the organisation’s **Email server** (SMTP). See <a href="#" data-hs-route="core/settings">Email, branding & settings</a>.
