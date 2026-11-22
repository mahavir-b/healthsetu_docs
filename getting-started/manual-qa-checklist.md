# Full manual QA checklist

Use this as a **single pass** from new organisation → setup → every role → day-to-day flows. For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>. Print this page or tick boxes in a copy while you test.

<div class="callout callout--tip">
  <strong>Staff entry (always):</strong> use the tenant portal — locally
  <code>http://{orgCode}.localhost:5174/...</code>.
  Platform admin: <code>http://localhost:5174/</code>.
  Patient app (if PatientSetu): <code>http://{orgCode}.localhost:5181/</code>.
  Do <strong>not</strong> log into standalone module ports (5173 Rakht · 5175 Supply · 5176 HR · 5177 Swastha · 5179 Care) for staff testing.
</div>

**Suggested test org code:** `qa{YYYYMMDD}` (e.g. `qa20261122`) → portal `http://qa20261122.localhost:5174/`

**Marking:** `[ ]` pending · `[x]` pass · `[!]` fail (note bug / screenshot / role / URL)

**Pass rule per item:** action completes, success banner or expected list refresh, no unexplained error banner, correct nav visibility for that role.

Also prepare worksheets from <a href="#" data-hs-route="getting-started/before-you-start">Before you start (paper & Excel)</a> before inventing masters live.

---

## 0. Pre-flight

- [ ] Core UI + Core API running (platform + tenant portal on **5174**)
- [ ] Module UIs running (embed targets): Care, Supply, Rakht, HR, Billing as needed
- [ ] Module APIs running for subscribed packs
- [ ] Platform admin login works at `http://localhost:5174/`
- [ ] SMTP / WhatsApp / UPI test credentials available *(or explicitly mark those sections N/A)*
- [ ] Password sheet ready for all test users (same known password OK for QA)

**Modules for this full round (tick what you will enable):**

- [ ] CARE (CareSetu)
- [ ] SUPPLY (SupplySetu)
- [ ] BLOOD_BANK (RakhtSetu)
- [ ] HR (HRSetu)
- [ ] BILLING (HealthSetu Billing)
- [ ] PATIENT (PatientSetu — requires CARE; not provisioned alone)

Skip Swastha unless an existing org still has `SWASTHA` (catalog treats it as retired).

---

## Phase 1 — Platform admin: create organization

**As:** Platform admin · **Where:** `http://localhost:5174/organizations`

### 1.1 Create org

- [ ] Open `/organizations` → **Create** / `/organizations/new`
- [ ] Fill **name**, **code** (slug), address, city, state, PIN, phone, email, contact
- [ ] Enable modules from the list above
- [ ] Save / create → lands on `/organizations/:id`
- [ ] Success banner shown
- [ ] Note org id: _______________ · code: _______________

### 1.2 Provision until READY

**Tab:** Provisioning (`?admin=provisioning` or Provisioning tab)

- [ ] Provision starts / status moves past DRAFT / PENDING
- [ ] Wait until status = **READY** (or document FAILED + error)
- [ ] If UI shows pending schema: **Apply DB migration / Apply schema updates**
- [ ] Re-check status = READY after apply
- [ ] **Seed configuration** (Care specialty seed if CARE enabled)
- [ ] COMMS / platform pieces present as expected for a new tenant

### 1.3 Import roles

**Tab:** Roles

- [ ] **Import recommended roles**
- [ ] Confirm roles appear for enabled modules only (see Phase 2 table)
- [ ] Disable roles this site will not use *(optional trim)*
- [ ] Spot-check one Care + one Supply + one HR + one Rakht + one Billing role has capabilities

### 1.4 First org admin user

**Tab:** Users → add · or `/organizations/:id/users/new`

- [ ] Create user: name, email, role = **organization_admin** (or **admin**)
- [ ] Invite path works (email and/or WhatsApp if configured later)
- [ ] Note credentials: email _______________ password _______________

### 1.5 Org configuration tabs (post-READY)

| Tab | Checks |
|-----|--------|
| Branding | [ ] App name, color, logo, support email saved |
| Email server | [ ] SMTP saved · [ ] **Send test email** OK *(or N/A)* |
| Payment QR | [ ] UPI + payee · [ ] Fee amounts *(or N/A)* |
| Communications | [ ] WhatsApp fields · [ ] **Send test message** OK *(or N/A)* |
| Barcodes | [ ] At least one template exists or create later on tenant |
| ID cards | [ ] At least one version exists or create later on tenant |
| Customize functionality | [ ] Flags match contract / QA intent |
| Configuration | [ ] Review defaults; note any required keys |

### 1.6 Platform handoff gate

- [ ] Org admin can open `http://{code}.localhost:5174/` and sign in
- [ ] Sidebar shows only subscribed modules
- [ ] `/settings/overview` loads

---

## Phase 2 — Roles catalog (verify after import)

**As:** Platform admin or org admin · Roles tab / tenant Users role picker

Check each role exists (for enabled modules). Then use Phase 3 to create a user per role you will test.

### Cross-product

- [ ] `admin`
- [ ] `organization_admin`

### Care (CARE)

- [ ] `clinic_admin`
- [ ] `clinic_receptionist`
- [ ] `clinic_doctor`
- [ ] `clinic_nurse`
- [ ] `clinic_pa`
- [ ] `clinic_procedure_tech`
- [ ] `clinic_counsellor`
- [ ] `clinic_cashier`

### Supply (SUPPLY)

- [ ] `supply_admin`
- [ ] `collection`
- [ ] `store_keeper`
- [ ] `request`
- [ ] `supplies`
- [ ] `inventory_supervisor`
- [ ] `inventory_manager`
- [ ] `supplies_manager`

### Rakht (BLOOD_BANK)

- [ ] `medical_director`
- [ ] `staff`
- [ ] `coordinator`
- [ ] `receptionist`
- [ ] `phlebotomist`
- [ ] `counsellor`
- [ ] `doctor`
- [ ] `testing_specialist`
- [ ] `technician_supervisor`
- [ ] `joint_secretary`
- [ ] `trustee`
- [ ] `technician`
- [ ] `quality_officer`

### HR (HR)

- [ ] `hr_admin`
- [ ] `hr_manager`
- [ ] `hr_payroll`
- [ ] `hr_employee`

### Billing (BILLING)

- [ ] `billing_cashier`
- [ ] `billing_supervisor`
- [ ] `billing_accountant`
- [ ] `billing_admin`

### Optional custom role test

- [ ] Create one custom role with a **subset** of capabilities
- [ ] Assign to a throwaway user
- [ ] Confirm denied screens show as hidden or blocked (not full access)

---

## Phase 3 — Create test users (every persona)

**As:** Org admin · Tenant: `/system/organization?admin=users`  
(or platform org Users tab)

Create users below for **enabled** modules. Use a naming pattern: `qa.{role}@{code}.test`

| # | Role slug | Email / login | Password | Created | Can sign in |
|---|-----------|---------------|----------|---------|-------------|
| 1 | organization_admin | | | [ ] | [ ] |
| 2 | clinic_admin | | | [ ] | [ ] |
| 3 | clinic_receptionist | | | [ ] | [ ] |
| 4 | clinic_doctor | | | [ ] | [ ] |
| 5 | clinic_nurse | | | [ ] | [ ] |
| 6 | clinic_pa | | | [ ] | [ ] |
| 7 | clinic_procedure_tech | | | [ ] | [ ] |
| 8 | clinic_counsellor | | | [ ] | [ ] |
| 9 | clinic_cashier | | | [ ] | [ ] |
| 10 | supply_admin | | | [ ] | [ ] |
| 11 | store_keeper | | | [ ] | [ ] |
| 12 | inventory_manager | | | [ ] | [ ] |
| 13 | request | | | [ ] | [ ] |
| 14 | medical_director | | | [ ] | [ ] |
| 15 | counsellor *(blood)* | | | [ ] | [ ] |
| 16 | phlebotomist | | | [ ] | [ ] |
| 17 | testing_specialist | | | [ ] | [ ] |
| 18 | technician | | | [ ] | [ ] |
| 19 | quality_officer | | | [ ] | [ ] |
| 20 | receptionist *(blood)* | | | [ ] | [ ] |
| 21 | hr_admin | | | [ ] | [ ] |
| 22 | hr_manager | | | [ ] | [ ] |
| 23 | hr_payroll | | | [ ] | [ ] |
| 24 | hr_employee | | | [ ] | [ ] |
| 25 | billing_admin | | | [ ] | [ ] |
| 26 | billing_cashier | | | [ ] | [ ] |
| 27 | billing_supervisor | | | [ ] | [ ] |
| 28 | billing_accountant | | | [ ] | [ ] |

**Per user smoke (after create):**

- [ ] Sign in at tenant portal
- [ ] Home / My Day loads
- [ ] Sidebar matches role (no unexpected admin-only items)
- [ ] Sign out cleanly

---

## Phase 4 — Tenant Settings / get ready

**As:** `organization_admin` · Start: `/settings/overview`

### 4.1 Getting started

- [ ] `/settings/overview` — task list + service readiness cards visible
- [ ] `/settings/recommended` — accept / trim recommendations
- [ ] Guided path if shown: Organization → Recommended → Workplaces → People & access → Get ready
- [ ] `/settings/get-ready` — activate services when tasks complete

### 4.2 Organization

- [ ] Organization details saved (type, GSTIN/PIN if prompted)
- [ ] Workplaces: create **MAIN** (code, name, state for PT, working week, address)
- [ ] Departments & job titles under MAIN (at least: Admin, Nursing/Clinical, Lab/Store as relevant)
- [ ] People & access / invite: link or invite core staff
- [ ] Barcodes: `/system/organization?admin=barcodes` — template → mapping → sample print path
- [ ] ID cards: `/system/organization?admin=id-cards` — version ready

### 4.3 Service readiness cards (per subscribed module)

| Service | Path hint | Ready / Active |
|---------|-----------|----------------|
| Patient care / Care | `/settings/pc-*` | [ ] |
| Billing (clinic or module) | `/settings/bl-*` | [ ] |
| Inventory / Supply | `/settings/inv-*` | [ ] |
| Blood bank | `/settings/bb-*` | [ ] |
| HR | `/settings/hr-*` | [ ] |
| Communications | `/settings/cm-*` | [ ] |

- [ ] Each enabled service reaches **Ready to activate** or **Active**
- [ ] Unrelated pending tasks do not block activating a ready service

---

## Phase 5 — Module masters (one-time data)

Do in this order when multiple modules are on: **HR → Supply → Care → Rakht → Billing → Patient**.

### 5.1 HRSetu masters

**As:** `hr_admin` · Portal HR / Settings HR pages

- [ ] Workplace MAIN complete (shifts: Morning / Evening; roles needed set)
- [ ] Departments with roles selected
- [ ] Holidays for current year
- [ ] Hire employees for every clinical/counter persona you will use (workplace + department + role)
- [ ] Doctors: council name + registration number filled
- [ ] Employment status **active** for selectable staff
- [ ] `/employees` list shows active staff
- [ ] Optional: print ID card for one employee

### 5.2 SupplySetu masters

**As:** `supply_admin`

- [ ] Locations: Main store (+ one department / BB location if relevant) — `/inventory/locations` or Settings inv
- [ ] Catalog types for go-live items — `/inventory/catalog`
- [ ] Parameters reviewed — `/inventory/parameters` *(or Settings)*
- [ ] Vendor document checklist — `/inventory/vendor-checklist`
- [ ] At least one vendor — `/inventory/vendors`
- [ ] Optional: custom fields, QC checklist templates
- [ ] Barcode labels for stock/assets smoke-printed *(if used)*

### 5.3 CareSetu masters

**As:** `clinic_admin`

- [ ] Specialty / seed done (from provision or Settings)
- [ ] Clinic settings: name, address, registration no., logo — `/clinic/settings`
- [ ] Doctors linked to **active HR employees** — `/clinic/doctors`
- [ ] Schedules / appointment hours published
- [ ] Fee items entered — `/clinic/fee-items`
- [ ] Templates reviewed — note / Rx
- [ ] Individuals path: `/people` works; open chart `/clinic/patients/person/:personId`

### 5.4 RakhtSetu masters

**As:** `medical_director` or blood admin

- [ ] Institutions / hospitals — `/hospitals`
- [ ] Configuration values reviewed — `/admin/configuration-values` *(or Settings bb)*
- [ ] Equipment configuration — `/admin/equipment-configuration`
- [ ] Donor questionnaire / workflows approved — `/admin/workflows`
- [ ] Blood label barcodes mapped + sample print
- [ ] Supply locations/catalog exist for consumables *(if SUPPLY on)* — do **not** add supply catalog inside Rakht

### 5.5 Billing module masters *(if BILLING subscribed)*

**As:** `billing_admin` · `/billing/...`

- [ ] Masters / charge setup
- [ ] Packages *(if used)*
- [ ] Settings / day-close prerequisites
- [ ] Cashier can open desk

### 5.6 PatientSetu *(if PATIENT)*

**As:** `clinic_admin`

- [ ] Portal settings — `/clinic/settings?pane=portal`
- [ ] Portal requests list opens — `/clinic/portal-requests`
- [ ] Patient app loads — `http://{code}.localhost:5181/`

---

## Phase 6 — Happy paths (day-to-day)

Run with the **primary** role for each step; re-run critical steps with alternate roles in Phase 7.

### 6.1 Care clinic path

**Roles:** receptionist → doctor → nurse → cashier

- [ ] **Receptionist:** `/people` → add Individual (demographics)
- [ ] Book appointment — `/clinic/appointments` (today or later)
- [ ] Waitlist optional — add / promote if UI present
- [ ] **Doctor:** `/clinic/opd` or doctor desk → open visit
- [ ] Write note / Rx / plan; save
- [ ] **Nurse:** nursing / vitals path for same patient
- [ ] **Cashier:** `/clinic/billing` — charge fee item, collect / mark paid
- [ ] Optional WhatsApp: appointment or Rx message path with consent
- [ ] Refills path if used — `/clinic/refills`
- [ ] Reports / audit spot-check — `/clinic/reports` or audit screen

### 6.2 Supply path

**Roles:** store_keeper → requestor → inventory_manager / supply_admin

- [ ] Add stock for a catalog item into Main store — `/inventory`
- [ ] Create stock **request** — request user
- [ ] **Approve** request
- [ ] Movement / issue to location
- [ ] Vendor → draft **PO** — `/inventory/purchase-orders`
- [ ] Receive against PO (or simulate receive path)
- [ ] Assets: add one asset — `/inventory/assets`
- [ ] Daily QC — `/daily-qc` *(if templates exist)*
- [ ] Staff tasks — `/staff-tasks` assign/complete one

### 6.3 Rakht blood path

**Roles:** counsellor → phlebotomist → testing → technician → issue desk / doctor

- [ ] Register donor — `/donors` or donor workstation
- [ ] Counselling / deferral decision path
- [ ] Collection — `/collections` or workstation
- [ ] Testing — `/testing` / lab workstation
- [ ] Separation / processing
- [ ] Component QC
- [ ] Crossmatch — `/crossmatch`
- [ ] Institution request → issue path — `/requests` or `/workstation/issue`
- [ ] Camp path smoke — `/camps` (create or open camp → register one)
- [ ] Label print on a unit
- [ ] Tasks / compliance spot-check

### 6.4 HR path

**Roles:** hr_admin → hr_manager → hr_employee → hr_payroll

- [ ] Hire one new employee end-to-end
- [ ] Assign shift / roster
- [ ] Mark **attendance** — `/attendance`
- [ ] Apply / approve **leave** — `/leave`
- [ ] Employee self-service: `/employee/me` or My day — check-in / leave view
- [ ] Salary / statutory / reports spot-check (payroll role)
- [ ] Document library upload/view one file *(if used)*

### 6.5 Billing module path *(if BILLING)*

**Roles:** billing_cashier → supervisor → accountant

- [ ] Open cashier desk — `/billing`
- [ ] Post a charge / package
- [ ] Approval path if required
- [ ] Credit note / refund path
- [ ] Day close
- [ ] Reports

### 6.6 Patient portal path *(if PATIENT)*

- [ ] Patient signs in / registers on `:5181`
- [ ] Book visit / appointment
- [ ] View records / medicines / bills as available
- [ ] Staff sees request in `/clinic/portal-requests`
- [ ] Staff action updates patient-visible status

### 6.7 Cross-module bundles

**Blood centre bundle**

- [ ] HR hire lab tech → Supply receive consumable → Rakht donor → print label → stock location used

**Clinic bundle**

- [ ] HR hire doctor (active + registration) → Care doctor picker shows them → book → OPD → bill

**Campus**

- [ ] One smoke path per live module without logging into standalone ports

---

## Phase 7 — Role-by-role capability smoke

For each user: sign in → confirm **can** do listed actions → confirm **cannot** reach admin-only / other-module admin screens.

### 7.1 Org / clinic admin

| Role | Must can | Must not (typical) |
|------|----------|-------------------|
| organization_admin | [ ] Settings, Users, all subscribed modules | — |
| clinic_admin | [ ] Clinic settings, doctors, fees, users for clinic | [ ] Supply org-wide admin if not granted |
| hr_admin | [ ] Workplaces, employees, HR settings | [ ] Blood medical policy approve if not granted |
| supply_admin | [ ] Catalog, vendors, PO, locations | [ ] Care clinical note write if not granted |
| medical_director | [ ] BB policies / clinical config | [ ] Unrelated payroll edit if not granted |
| billing_admin | [ ] Billing masters / settings | [ ] HR hire if not granted |

### 7.2 Care line roles

| Role | Smoke |
|------|-------|
| clinic_receptionist | [ ] Individuals + book + cannot edit clinic masters |
| clinic_doctor | [ ] OPD / Rx; limited admin |
| clinic_nurse | [ ] Nursing / vitals; no fee master edit |
| clinic_pa | [ ] PA desk actions available |
| clinic_procedure_tech | [ ] Procedures path |
| clinic_counsellor | [ ] Counsellor screens |
| clinic_cashier | [ ] Clinic billing collect; no doctor schedule edit |

### 7.3 Supply line roles

| Role | Smoke |
|------|-------|
| store_keeper | [ ] Stock in/out; limited procurement |
| inventory_manager | [ ] Approvals + stock oversight |
| request | [ ] Raise request; cannot approve own if policy forbids |
| collection / supplies / supervisors | [ ] Matching nav + one happy action each |

### 7.4 Rakht line roles

| Role | Smoke |
|------|-------|
| receptionist | [ ] Front / donor intake |
| counsellor | [ ] Counselling |
| phlebotomist | [ ] Collection |
| testing_specialist | [ ] Testing |
| technician | [ ] Processing / separation |
| quality_officer | [ ] QC / compliance |
| doctor | [ ] Clinical / issue support screens |
| coordinator / staff / trustee / joint_secretary | [ ] Nav + one read or allowed action |

### 7.5 HR / Billing line roles

| Role | Smoke |
|------|-------|
| hr_manager | [ ] Employees / leave approve |
| hr_payroll | [ ] Salary / statutory views |
| hr_employee | [ ] Self-service only |
| billing_cashier | [ ] Desk charges |
| billing_supervisor | [ ] Approvals / day close assist |
| billing_accountant | [ ] Reports / accounting views |

---

## Phase 8 — UI / safety / regression gates

- [ ] Every list: title + count left; Refresh (+ Add) on same header row
- [ ] Destructive actions use ConfirmDialog (delete user, discard unit, day close, data reset)
- [ ] No `window.confirm` / raw alert for those paths
- [ ] Form errors via in-page banner (not silent fail)
- [ ] Dates display / pick as **DD/MM/YYYY** where date pickers exist
- [ ] Empty lists show short empty state (not long essays)
- [ ] Individuals stay on `/people` (no Care-only patients list as entry)
- [ ] Deep links from portal sidebar open iframe content (if snapshot empty: stay on 5174, use sidebar — do not switch to 5179 etc.)

### Admin-only / dangerous

- [ ] Data reset *(Rakht admin)* — confirm dialog + only authorized role
- [ ] Merge duplicates *(Care)* — confirm + correct surviving person
- [ ] Disable / delete user — confirm + cannot sign in after
- [ ] Day close — cannot post freely after close without reopen policy

---

## Phase 9 — Sign-off sheet

| Area | Tester | Date | Pass? | Notes / bugs |
|------|--------|------|-------|--------------|
| Phase 1 Provision READY | | | [ ] | |
| Phase 2 Roles import | | | [ ] | |
| Phase 3 Users created | | | [ ] | |
| Phase 4 Settings ready | | | [ ] | |
| Phase 5 Masters | | | [ ] | |
| Phase 6 Care path | | | [ ] | |
| Phase 6 Supply path | | | [ ] | |
| Phase 6 Rakht path | | | [ ] | |
| Phase 6 HR path | | | [ ] | |
| Phase 6 Billing path | | | [ ] | |
| Phase 6 Patient path | | | [ ] | |
| Phase 7 Role matrix | | | [ ] | |
| Phase 8 Safety gates | | | [ ] | |

**Org code:** _______________  
**Build / branch / env:** _______________  
**Overall:** Pass / Fail / Pass with issues  

---

## Quick URL cheat sheet

| What | URL |
|------|-----|
| Platform orgs | `http://localhost:5174/organizations` |
| Tenant home | `http://{code}.localhost:5174/` |
| Settings overview | `.../settings/overview` |
| Users | `.../system/organization?admin=users` |
| Barcodes | `.../system/organization?admin=barcodes` |
| ID cards | `.../system/organization?admin=id-cards` |
| Individuals | `.../people` |
| Care chart | `.../clinic/patients/person/:personId` |
| Appointments | `.../clinic/appointments` |
| Inventory stock | `.../inventory` |
| Purchase orders | `.../inventory/purchase-orders` |
| Donors | `.../donors` |
| Employees | `.../employees` |
| Billing desk | `.../billing` |
| Patient app | `http://{code}.localhost:5181/` |

---

## Related help pages

- <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>
- <a href="#" data-hs-route="getting-started/before-you-start">Before you start (paper & Excel)</a>
- <a href="#" data-hs-route="getting-started/by-role">Guides by role</a>
- <a href="#" data-hs-route="core/users-roles">Users & roles</a>
- <a href="#" data-hs-route="core/settings">Email, branding & settings</a>
- <a href="#" data-hs-route="caresetu/setup">Clinic setup & reports</a>
- <a href="#" data-hs-route="supplysetu/catalog-stock">Catalog, stock & locations</a>
- <a href="#" data-hs-route="hrsetu/employees">Employees & onboarding</a>
- <a href="#" data-hs-route="rakhtsetu/overview">RakhtSetu overview</a>
