# Clinic setup & reports

Clinic administrators set these up **once before go-live**, then adjust them when fees, doctors, or hours change. Reception and doctors depend on them every day.

## Setup order

| Step | Screen (Administration menu) | Why it matters |
|------|------------------------------|----------------|
| 1 | **Department templates** | Installs illnesses, medicines, and care plans for the departments you run |
| 2 | **Doctors** | Doctors must exist before anyone can book them |
| 3 | **Schedules** | Booking only offers slots on a doctor’s working days |
| 4 | **Fee items** | Standard rates the billing picker uses |
| 5 | **Desktop Sync Devices** *(optional)* | Lets counter PCs send scanned documents to the Sync Inbox |

## Department templates

1. Open **Department templates**.
2. Tick the departments your clinic runs (General OPD, Dermatology & Cosmetology, ENT, Ophthalmology, and others).
3. Choose **Install selected**.

Installing writes the department’s illnesses, medicines, care plans, and aftercare. The medicine formulary is shared, so it is not repeated under every department. Rows your clinic has already edited are left as they are.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/care-templates.png" alt="Department templates" />
  <figcaption>Department templates: each department shows its installed version and illness count. Tabs below list Illnesses, Medicines, Cures / care plans, and Aftercare.</figcaption>
</figure>

## Doctors

Doctors are **employees in HRSetu**. CareSetu adds their specialty, consultation fees, and medical council registration.

1. Make sure the doctor exists in <a href="#" data-hs-route="hrsetu/employees">Employees</a>.
2. Open **Doctors** → **Register employee as doctor**.
3. Enter specialty, council and registration number, and new / follow-up consultation fees.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/care-doctors.png" alt="Doctors list" />
  <figcaption>Doctors: council registration and new / follow-up consultation fees for each doctor.</figcaption>
</figure>

## Schedules

**Weekly hours** set when each doctor sees patients:

1. Pick the doctor and tick the weekdays.
2. Set start and end time, slot length (minutes), maximum patients, and room.
3. **Save hours**.

Use **Leave or holiday** to block a doctor (or all doctors) for a date range. Booking then stops offering those days.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/care-schedules.png" alt="Doctor schedules" />
  <figcaption>Schedules: weekly sessions on the left, leave and holidays on the right.</figcaption>
</figure>

<div class="callout callout--tip">
  If reception says “no slots” for a doctor, check Schedules first. Do not force a booking around a missing schedule.
</div>

## Fee items

**Fee items** are the standard consultation, procedure, and service charges. Each has a code, name, default amount, and group (Consultation, Procedure, Service). The billing line picker uses this list.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/care-fee-items.png" alt="Fee items" />
  <figcaption>Fee master with code, item, and default amount.</figcaption>
</figure>

## Sync Inbox (desktop documents)

When **HealthSetu Desktop Sync** is installed on a clinic PC, it finds patient documents saved on that computer (scans, reports) and sends them to the **Sync Inbox**.

1. Open **My Work → Sync Inbox**.
2. Check each document’s suggested patient. Exact matches and unmatched files are listed separately.
3. **Approve** only when the patient is confirmed. The desktop agent uploads the file to the chart after approval.
4. **Reject** anything that is not a patient document.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/care-sync-inbox.png" alt="Sync Inbox" />
  <figcaption>Sync Inbox: counts for Ready for review, Exact matches, Unmatched, and Uploading. It asks you to install Desktop Sync if the agent is not found on this PC.</figcaption>
</figure>

Admins register counter PCs under **Administration → Desktop Sync Devices**.

## Clinic reports

Open **Insights & Reports → Clinic reports**, choose a report and a date range, then **Load report** and **Export CSV**.

| Report | Use it for |
|--------|-----------|
| Footfall | Visits per day / doctor |
| No-show rate | Booked patients who did not arrive |
| Top diagnoses | Most common illnesses in the period |
| Patient satisfaction (NPS) | Feedback scores |
| Wait time | Arrival to consultation time |
| Procedures and sittings | Courses and sittings done |

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/care-reports.png" alt="Clinic reports" />
  <figcaption>Clinic reports: pick a report, set From / To, then load and export.</figcaption>
</figure>
