# Full manual QA checklist

Walk this **in order**. Each section starts with **who to log in as**, then the exact steps for that user. Sign out before the next login.

For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>.

<div class="callout callout--tip">
  <strong>Where to log in (Azure)</strong><br/>
  Platform admin: <code>https://admin.healthsetu.com/</code><br/>
  Staff (every role below): <code>https://qaYYYYMMDD.healthsetu.com/</code><br/>
  Patient app: <code>https://qaYYYYMMDD.patient.healthsetu.co.in/</code><br/>
  Use only the Azure hosts above for this QA round.
</div>

**Replace `YYYYMMDD`** with today’s date (e.g. `20261122`).  
After provision, tenant DNS should resolve to `https://qaYYYYMMDD.healthsetu.com/` (alias `*.healthsetu.co.in` is OK if that is what Azure DNS serves).  
**Password for every QA staff user:** `QaTest@2026`  
**Marking:** `[ ]` pending · `[x]` pass · `[!]` fail  

---

## Seed values (copy from here while typing)

| What | Value |
|------|-------|
| Org name / code | `QA HealthSetu Campus YYYYMMDD` / `qaYYYYMMDD` |
| Address | `12 SG Highway`, Ahmedabad, Gujarat, `380054` |
| Org phone / email | `9876500001` / `admin@qaYYYYMMDD.test` |
| Modules | CARE + SUPPLY + BLOOD_BANK + HR + BILLING + PATIENT |
| Brand | App `QA Campus` · support `support@qaYYYYMMDD.test` |
| UPI *(optional)* | `qacampus@upi` · payee `QA HealthSetu Campus` · fee `500` |
| Workplace | Code `MAIN` · name `Main Campus` · PT Gujarat · Mon–Sat |
| Shifts | `Morning` 08:00–16:00 · `Evening` 16:00–22:00 |
| Holiday | `26/01/YYYY` Republic Day |
| Doctor employee | `Dr Anita Shah` · GMC `G-12345` · Active |
| Patient | `Test Patient One` · F · DOB `15/03/1990` · phone `9876511111` |
| Fees | New consult ₹500 · Follow-up ₹300 · Dressing ₹200 · ECG ₹400 |
| Schedule | Mon–Sat 09:00–13:00 · 15 min · room `OPD-1` |
| Locations | `Main store` · `OT store` · `Blood bank fridge room` |
| Catalog | `Surgical gloves M` · `Disposable syringe 5ml` · `HBsAg ELISA kit 96T` |
| Stock | Gloves **50** boxes · lot `LOT-GLOVE-01` · expiry `31/12/2027` |
| Vendor | `MedSupply Gujarat Pvt Ltd` · GSTIN `24AAAAA0000A1Z5` |
| PO | Gloves × **20** @ ₹180 |
| Institution | `City General Hospital` · Dr Patel · `9876533333` |
| Donor | `Donor Ramesh Kumar` · M · DOB `10/05/1988` · O+ · 72 kg · `9876544444` |
| Billing package | `OPD day package` ₹800 |

### Login sheet (create these in Step B)

| Login | Role |
|-------|------|
| `qa.admin@qaYYYYMMDD.test` | organization_admin |
| `qa.hradmin@qaYYYYMMDD.test` | hr_admin |
| `qa.hrmgr@qaYYYYMMDD.test` | hr_manager |
| `qa.payroll@qaYYYYMMDD.test` | hr_payroll |
| `qa.employee@qaYYYYMMDD.test` | hr_employee |
| `qa.clinicadmin@qaYYYYMMDD.test` | clinic_admin |
| `qa.reception@qaYYYYMMDD.test` | clinic_receptionist |
| `qa.doctor@qaYYYYMMDD.test` | clinic_doctor |
| `qa.nurse@qaYYYYMMDD.test` | clinic_nurse |
| `qa.cashier@qaYYYYMMDD.test` | clinic_cashier |
| `qa.supply@qaYYYYMMDD.test` | supply_admin |
| `qa.store@qaYYYYMMDD.test` | store_keeper |
| `qa.invmgr@qaYYYYMMDD.test` | inventory_manager |
| `qa.request@qaYYYYMMDD.test` | request |
| `qa.meddir@qaYYYYMMDD.test` | medical_director |
| `qa.bbreception@qaYYYYMMDD.test` | receptionist |
| `qa.bbcounsellor@qaYYYYMMDD.test` | counsellor |
| `qa.phlebo@qaYYYYMMDD.test` | phlebotomist |
| `qa.testing@qaYYYYMMDD.test` | testing_specialist |
| `qa.tech@qaYYYYMMDD.test` | technician |
| `qa.qo@qaYYYYMMDD.test` | quality_officer |
| `qa.billadmin@qaYYYYMMDD.test` | billing_admin |
| `qa.billcash@qaYYYYMMDD.test` | billing_cashier |
| `qa.billsup@qaYYYYMMDD.test` | billing_supervisor |
| `qa.billacct@qaYYYYMMDD.test` | billing_accountant |

---

## Step 0 — Pre-flight (no login)

- [ ] Azure reachable: `https://admin.healthsetu.com/` sign-in works; tenant DNS for new org will be `https://qaYYYYMMDD.healthsetu.com/`
- [ ] Open help site home: https://mahavir-b.github.io/healthsetu_docs/ — sidebar loads
- [ ] Password ready: `QaTest@2026`

---

## Step A — Now log in as **Platform admin**

**URL:** `https://admin.healthsetu.com/`  
**User:** your platform admin account  

### Create the org

- [ ] Go to **Organizations** → Create
- [ ] Name `QA HealthSetu Campus YYYYMMDD` · code `qaYYYYMMDD` · address from seed pack
- [ ] Enable CARE + SUPPLY + BLOOD_BANK + HR + BILLING + PATIENT → Save
- [ ] Note org id: _______________

### Provisioning tab

- [ ] Wait until status **READY**
- [ ] Apply DB / schema updates if shown → READY again
- [ ] Seed configuration → General OPD

### Roles tab

- [ ] **Import recommended roles**
- [ ] Confirm these exist: `organization_admin`, `clinic_*`, `supply_admin`, `store_keeper`, `hr_*`, blood roles, `billing_*`

### Users tab — first tenant admin

- [ ] Add user `qa.admin@qaYYYYMMDD.test` · role **organization_admin** · password `QaTest@2026`

### Other org tabs

- [ ] **Branding** → app `QA Campus` · support email → Save
- [ ] **Email server** → save + Send test *(or N/A)*
- [ ] **Payment QR** → UPI / payee / fee 500 *(or N/A)*
- [ ] **Communications** → WhatsApp test *(or N/A)*
- [ ] **Barcodes** → open one template → mapping → designer
- [ ] **ID cards** → open one version → designer
- [ ] **Customize functionality** → flags match modules
- [ ] **Configuration** → review defaults
- [ ] **ABDM** tab opens *(or N/A)*
- [ ] Platform **Users** list `/users` opens · New user form loads

### Sign out of platform admin

- [ ] Sign out

---

## Step B — Now log in as **QA Org Admin**

**URL:** `https://qaYYYYMMDD.healthsetu.com/`  
**User:** `qa.admin@qaYYYYMMDD.test`  
**Role:** `organization_admin`  
**Password:** `QaTest@2026`

### Portal chrome

- [ ] Home loads · branding shows `QA Campus`
- [ ] Sidebar shows Care, Supply, Rakht, HR, Billing
- [ ] Open `/inbox` · Refresh
- [ ] Open `/user-preference` · Save one preference
- [ ] Open `/insight/reports` · `/insight/clicks`

### Settings hub — open every page and Save/Continue where shown

- [ ] `/settings/overview` · `/settings/get-ready` · `/settings/recommended` · `/settings/smart-setup` · `/settings/all-settings`
- [ ] `/settings/organization` — confirm Ahmedabad / Gujarat / 380054
- [ ] `/settings/workplaces` — create **MAIN** / Main Campus · Morning + Evening shifts
- [ ] `/settings/inheritance` · `/settings/departments` — add Administration, Front Desk, Clinical, Laboratory, Counseling, Stores, Medical Office
- [ ] `/settings/job-title` · `/settings/people` · `/settings/invite`
- [ ] `/settings/documents` · `/settings/access-profiles` · `/settings/approvals`
- [ ] `/settings/integrations` · `/settings/data-import` · `/settings/audit` · `/settings/template-updates` · `/settings/impact`
- [ ] Patient care: `/settings/pc` · `pc-doctors` · `pc-appointments` · `pc-clinical` · `pc-portal`
- [ ] Billing settings: `/settings/bl` · `bl-charges` · `bl-invoices` · `bl-payments`
- [ ] Inventory settings: `/settings/inv` · `inv-catalog` · `inv-vendors` · `inv-assets`
- [ ] Blood bank settings: `/settings/bb` · `bb-facility` · `bb-policies` · `bb-policy` · `bb-components` · `bb-storage`
- [ ] HR settings: `/settings/hr` · `hr-employment` · `hr-leave` · `hr-docs` · `hr-time` · `hr-shifts` · `hr-eligibility` · `hr-holidays` · `hr-checkin` · `hr-payroll` · `hr-training`
- [ ] Comms: `/settings/cm` · `cm-auto` · `cm-channels` · `cm-wa` · `cm-templates` · `cm-template` · `cm-prefs`
- [ ] `/settings/dx` opens

### Create every QA login user

Go to `/system/organization?admin=users` → Add each from the login sheet (password `QaTest@2026`).

- [ ] All users from the login sheet created
- [ ] Barcodes: `/system/organization?admin=barcodes` → mapping → designer
- [ ] ID cards: `/system/organization?admin=id-cards` → designer · print sample for later employee

### Redirect sanity (stay logged in as admin)

- [ ] `/setup` → settings overview
- [ ] `/patients` and `/clinic/patients` → `/people`
- [ ] `/account` → `/user-preference`

### Sign out

- [ ] Sign out of `qa.admin@…`

---

## Step C — Now log in as **QA HR Admin**

**User:** `qa.hradmin@qaYYYYMMDD.test`  
**Role:** `hr_admin`

- [ ] Home loads · HR items visible · Care clinical write not available (or read-only)
- [ ] `/hr/dashboard` · `/hr/reports` open
- [ ] `/workplaces` → MAIN complete · holidays `26/01` Republic Day
- [ ] `/departments` or workplace depts → roles attached per seed pack
- [ ] `/shifts` → Morning + Evening
- [ ] `/employees` → **Hire** each:
  - [ ] `Dr Anita Shah` · Clinical · clinic_doctor · GMC `G-12345` · **Active**
  - [ ] `Nurse Priya Mehta` · Clinical · clinic_nurse · Active
  - [ ] `Ravi Patel` · Front Desk · clinic_receptionist · Active
  - [ ] `Sneha Desai` · Front Desk · clinic_cashier · Active
  - [ ] `Amit Joshi` · Stores · store_keeper · Active
  - [ ] `Lab Tech Kiran Shah` · Laboratory · technician · Active
  - [ ] `Counsellor Meera Shah` · Counseling · counsellor · Active
  - [ ] `Phlebotomist Neha Rana` · Laboratory · phlebotomist · Active
  - [ ] `MO Dr Vikram Patel` · Medical Office · medical_director · GMC `G-67890` · Active
  - [ ] Extra: `Temp Staff One` · Front Desk · clinic_receptionist · Active
- [ ] Open employee detail for Dr Anita Shah
- [ ] `/onboarding` · `/training` · `/bgv` · `/salary` · `/statutory` · `/fnf` open
- [ ] `/attendance` — mark Temp Staff One present today
- [ ] `/leave` — list opens
- [ ] `/employee-setup` hub tabs · `/document-library` · `/employee-files` · `/work-clearances` · `/holidays`
- [ ] Assign Morning shift to Temp Staff One
- [ ] Sign out

---

## Step D — Now log in as **QA HR Manager**

**User:** `qa.hrmgr@qaYYYYMMDD.test`  
**Role:** `hr_manager`

- [ ] `/employees` list loads
- [ ] `/leave` — approve a leave for Temp Staff One (create one if needed: 1 day next week)
- [ ] Cannot open org Customize / platform tabs
- [ ] Sign out

---

## Step E — Now log in as **QA Payroll**

**User:** `qa.payroll@qaYYYYMMDD.test`  
**Role:** `hr_payroll`

- [ ] `/salary` · `/statutory` · `/hr/reports` open
- [ ] Open a salary run if one exists (`/salary/runs/:id`)
- [ ] Cannot hire employees
- [ ] Sign out

---

## Step F — Now log in as **QA Employee (self-service)**

**User:** `qa.employee@qaYYYYMMDD.test`  
**Role:** `hr_employee`

- [ ] `/employee/me` (My day) loads
- [ ] `/employee/checkin` · `/employee/leave` · `/employee/salary` · `/employee/documents`
- [ ] `/employee/attendance` · `/employee/shifts` · `/employee/holidays` · `/employee/clearances` · `/employee/profile`
- [ ] No admin Settings / hire screens
- [ ] Sign out

---

## Step G — Now log in as **QA Supply Admin**

**User:** `qa.supply@qaYYYYMMDD.test`  
**Role:** `supply_admin`

- [ ] `/dashboard/inventory` · `/reports` · `/staff-tasks` · `/daily-qc` open
- [ ] `/inventory/locations` — Main store, OT store, Blood bank fridge room
- [ ] `/inventory/catalog` — Add Surgical gloves M, Disposable syringe 5ml, HBsAg ELISA kit 96T
- [ ] `/inventory/catalog/new` and edit gloves
- [ ] `/inventory/custom-fields` · `/inventory/parameters` · `/inventory/vendor-checklist` (GST + Drug licence required)
- [ ] `/inventory/vendors` — add MedSupply Gujarat · GSTIN `24AAAAA0000A1Z5`
- [ ] `/inventory/stock/new` — gloves **50** · lot `LOT-GLOVE-01` · expiry `31/12/2027` → Main store
- [ ] `/inventory` stock list shows gloves · edit stock row
- [ ] `/inventory/assets` — add `BP Monitor QA-01` · open detail · `/inventory/assets/import` wizard opens
- [ ] `/inventory/service-contracts` · `/inventory/asset-workflow-mapping` · `/inventory/reorder` · `/inventory/receive` · `/inventory/stock-intake` · `/inventory/movement`
- [ ] `/inventory/purchase-orders/new` — MedSupply · gloves ×20 @ ₹180 · save draft · open detail
- [ ] `/inventory/quotations/new` — form opens · list `/inventory/quotations`
- [ ] `/inventory/vendor-returns/new` · `/admin/qc-checklist-templates` · `/inventory/checklists/new`
- [ ] Hub tabs: `/inventory?tab=stock|checklists|qc|quotations|invoices|purchase-orders`
- [ ] `/admin/supply-data-reset` — ConfirmDialog appears · **Cancel** (do not wipe)
- [ ] Sign out

---

## Step H — Now log in as **QA Store Keeper**

**User:** `qa.store@qaYYYYMMDD.test`  
**Role:** `store_keeper`

- [ ] `/inventory` — gloves stock visible · Refresh
- [ ] Stock in/out or movement for gloves works
- [ ] Limited or no vendor master edit (per capabilities)
- [ ] Sign out

---

## Step I — Now log in as **QA Requester**

**User:** `qa.request@qaYYYYMMDD.test`  
**Role:** `request`

- [ ] `/inventory/request` — request **5** boxes Surgical gloves M for OT store → Submit
- [ ] Cannot approve own request (if policy forbids)
- [ ] Sign out

---

## Step J — Now log in as **QA Inventory Manager**

**User:** `qa.invmgr@qaYYYYMMDD.test`  
**Role:** `inventory_manager`

- [ ] `/inventory/approvals` — **Approve** the gloves request
- [ ] Confirm movement / issue path Main store → OT store
- [ ] Sign out

---

## Step K — Now log in as **QA Clinic Admin**

**User:** `qa.clinicadmin@qaYYYYMMDD.test`  
**Role:** `clinic_admin`

- [ ] `/clinic` dashboard · `/clinic/settings` — name `QA Campus OPD` · reg `QA-CLINIC-001` · Save
- [ ] Open each settings pane: `?pane=portal` · `integrations` · `clinic` · `clinical` · `money` · `roles` · `people` · `audit` · `merge`
- [ ] `/clinic/doctors` — link **Dr Anita Shah**
- [ ] Schedules — Mon–Sat 09:00–13:00 · 15 min · OPD-1
- [ ] `/clinic/fee-items` — New consult ₹500 · Follow-up ₹300 · Dressing ₹200 · ECG ₹400
- [ ] `/clinic/templates` — open one domain
- [ ] `/clinic/procedures` · `/clinic/procedures/start` · `/clinic/procedures/book`
- [ ] `/clinic/counsellor` · `/clinic/reports` · `/clinic/doctor-desk` · `/clinic/nursing` · `/clinic/lab`
- [ ] `/clinic/token-display` · `/clinic/tv` · `/clinic/audit` · `/clinic/merge` (do not merge yet)
- [ ] `/clinic/refills` · `/clinic/portal-requests` · `/clinic/billing` *(note if hidden when BILLING on)*
- [ ] `/people` — Add **Test Patient One** (F, 15/03/1990, 9876511111) · Edit · open chart
- [ ] Chart tabs: summary, labs, procedures, billing, documents, details
- [ ] Sign out

---

## Step L — Now log in as **QA Reception**

**User:** `qa.reception@qaYYYYMMDD.test`  
**Role:** `clinic_receptionist`

- [ ] `/people` — find Test Patient One
- [ ] `/clinic/appointments` — book Test Patient One · Dr Anita Shah · today/tomorrow 09:00
- [ ] `/clinic/appointments?view=waitlist` opens
- [ ] Cannot edit fee masters / clinic settings
- [ ] Sign out

---

## Step M — Now log in as **QA Doctor**

**User:** `qa.doctor@qaYYYYMMDD.test`  
**Role:** `clinic_doctor`

- [ ] `/clinic/opd` or `/clinic/doctor-desk` — open Test Patient One visit
- [ ] Note: `URI — symptomatic care` · Rx: paracetamol 500 mg · Save
- [ ] Limited admin (no fee master edit)
- [ ] Sign out

---

## Step N — Now log in as **QA Nurse**

**User:** `qa.nurse@qaYYYYMMDD.test`  
**Role:** `clinic_nurse`

- [ ] `/clinic/nursing` — open same visit
- [ ] Vitals: BP `120/80` · pulse `78` · temp `98.6°F` · Save
- [ ] No fee master edit
- [ ] Sign out

---

## Step O — Now log in as **QA Clinic Cashier**

**User:** `qa.cashier@qaYYYYMMDD.test`  
**Role:** `clinic_cashier`

- [ ] `/clinic/billing` (or billing desk if Care billing hidden) — charge New consultation ₹500 (+ Dressing ₹200 if done)
- [ ] Mark paid **Cash**
- [ ] Cannot edit doctor schedules
- [ ] Sign out

---

## Step P — Now log in as **QA Medical Director**

**User:** `qa.meddir@qaYYYYMMDD.test`  
**Role:** `medical_director`

- [ ] `/dashboard` · `/dashboard/qc` · `/dashboard/compliance` open
- [ ] Open each dashboard variant you use: hospital-blood, executive, camps, donors-analytics, lab, blood-inventory, crossmatch, requests
- [ ] `/hospitals` — add **City General Hospital** · Dr Patel · `9876533333`
- [ ] `/partner-blood-banks` opens
- [ ] `/admin/equipment-configuration` — `ELISA Reader 1`
- [ ] `/admin/workflows` — open donor questionnaire · approve if required
- [ ] `/admin/workflows/:key` detail opens
- [ ] `/dashboard/lab/elisa` opens
- [ ] Blood label barcode sample print (tenant barcodes)
- [ ] `/admin/blood-data-reset` — ConfirmDialog · **Cancel**
- [ ] `/camps` — create `QA Weekend Camp` · tomorrow · MAIN lawn · open detail
- [ ] `/support` opens
- [ ] Sign out

---

## Step Q — Now log in as **QA BB Reception**

**User:** `qa.bbreception@qaYYYYMMDD.test`  
**Role:** `receptionist` (blood)

- [ ] `/donors` · `/donors/new` — register **Donor Ramesh Kumar** (O+, 72 kg, 9876544444, DOB 10/05/1988)
- [ ] Open donor detail
- [ ] Sign out

---

## Step R — Now log in as **QA BB Counsellor**

**User:** `qa.bbcounsellor@qaYYYYMMDD.test`  
**Role:** `counsellor`

- [ ] Open Donor Ramesh Kumar · counselling → **fit to donate**
- [ ] Sign out

---

## Step S — Now log in as **QA Phlebotomist**

**User:** `qa.phlebo@qaYYYYMMDD.test`  
**Role:** `phlebotomist`

- [ ] `/collections` or `/workstation/donor` — complete collection for Ramesh
- [ ] Sign out

---

## Step T — Now log in as **QA Testing**

**User:** `qa.testing@qaYYYYMMDD.test`  
**Role:** `testing_specialist`

- [ ] `/testing` → pending · enter/add results · completed · tti-panel paths open
- [ ] `/workstation/lab` opens
- [ ] Complete testing for the unit
- [ ] Sign out

---

## Step U — Now log in as **QA Technician**

**User:** `qa.tech@qaYYYYMMDD.test`  
**Role:** `technician`

- [ ] `/blood-inventory/pending-separation` · `/workstation/separation` · triple-bag workspace
- [ ] Open each blood inventory tab once (pending-separation, components, discarded, autoclave-waste, …)
- [ ] Complete separation / processing for the unit
- [ ] Sign out

---

## Step V — Now log in as **QA Quality Officer**

**User:** `qa.qo@qaYYYYMMDD.test`  
**Role:** `quality_officer`

- [ ] `/blood-inventory/component-qc` — pass QC
- [ ] `/blood-inventory/pending-doctor-components` · `/dashboard/qc` · `/tasks`
- [ ] `/crossmatch` (redirects OK) · `/requests` · `/requests/new` — request from City General · patient `CGH Bed 12`
- [ ] `/workstation/issue` — issue path
- [ ] `/add-bag` form opens
- [ ] Print bag/component label
- [ ] Sign out

---

## Step W — Now log in as **QA Billing Admin**

**User:** `qa.billadmin@qaYYYYMMDD.test`  
**Role:** `billing_admin`  
*(Skip W–Z if BILLING not enabled)*

- [ ] `/billing` · `/billing/masters` · `/billing/packages` — create `OPD day package` ₹800
- [ ] `/billing/settings` · Save
- [ ] `/billing/accounts` · `/billing/reports` open
- [ ] Sign out

---

## Step X — Now log in as **QA Billing Cashier**

**User:** `qa.billcash@qaYYYYMMDD.test`  
**Role:** `billing_cashier`

- [ ] `/billing` — charge Test Patient One · OPD day package ₹800 · collect Cash
- [ ] Open bill composer `/billing/bills/:id` if shown
- [ ] Sign out

---

## Step Y — Now log in as **QA Billing Supervisor**

**User:** `qa.billsup@qaYYYYMMDD.test`  
**Role:** `billing_supervisor`

- [ ] `/billing/approvals` · `/billing/credit-notes` · `/billing/refunds`
- [ ] Optional ₹100 credit-note path
- [ ] `/billing/day-close` — run day close (or open and Cancel if not closing for real)
- [ ] Sign out

---

## Step Z — Now log in as **QA Billing Accountant**

**User:** `qa.billacct@qaYYYYMMDD.test`  
**Role:** `billing_accountant`

- [ ] `/billing/reports` · `/billing/accounts` · open one account
- [ ] Sign out

---

## Step AA — Now use the **Patient app** (not staff portal)

**URL:** `https://qaYYYYMMDD.patient.healthsetu.co.in/`  
**User:** phone `9876511111` (Test Patient One)

- [ ] `/signin` → Home `/`
- [ ] `/visits` · `/book` — book tomorrow · Dr Anita Shah
- [ ] `/records` · `/medicines` · `/bills` · `/profile`
- [ ] `/notifications` · `/messages` · `/more`
- [ ] `/privacy` · `/security` · `/account` · `/abha` · `/services` · `/services/emergency`

### Then log in again as **QA Clinic Admin**

**User:** `qa.clinicadmin@qaYYYYMMDD.test`

- [ ] `/clinic/portal-requests` — see the booking · update status
- [ ] Sign out

---

## Step AB — Optional: Swastha screens

Only if `SWASTHA` is enabled. Log in as org admin (or OHC admin) and open every `/ohc/*` path once:

- [ ] `/ohc` · employees · pre-employment · pre-employment-authorization · opd · periodic-medical · audiometry · health-checkup · vaccination
- [ ] first-aiders · ambulances · ambulance · first-aid-box · canteen-hygiene · plant-inspection
- [ ] collection-agencies · biomedical-waste · monthly-ohc-work · yearly-calendar · daily-report
- [ ] organization · departments · job-titles · medical-tests · test-requirements · documents

---

## Step AC — Help docs (browser, no product login)

Open https://mahavir-b.github.io/healthsetu_docs/ and tick each sidebar page loads:

- [ ] Home · Getting started (overview, login, by-role, before-you-start, all Prep pages, go-live, **this QA page**, FAQ, glossary)
- [ ] Security (all) · Core (all) · RakhtSetu (all) · SupplySetu (all) · HRSetu (all) · CareSetu (all) · SwasthaSetu (all)
- [ ] How to add screenshots & videos

---

## Step AD — Cross-checks after all logins

Log in as **QA Org Admin** again (`qa.admin@…`):

- [ ] Blood centre bundle: Lab Tech exists · gloves in BB fridge · donor Ramesh · label printed
- [ ] Clinic bundle: Dr Anita in picker · appointment · OPD note · ₹500 bill
- [ ] Dates show **DD/MM/YYYY** (patient DOB `15/03/1990`)
- [ ] Lists: title + count · Refresh + Add on header
- [ ] Destructive actions used ConfirmDialog (not `window.confirm`)
- [ ] All staff work stayed on `https://….healthsetu.com` (no localhost)

### Public token pages *(N/A unless you have a live token)*

- [ ] `/vendor/onboarding/:token` · `/employee/onboarding/:token` · `/employee/offer-sign/:token`
- [ ] `/quotation/vendor/:token` · `/purchase-order/vendor/:token` · `/purchase-order/confirmed/:token`
- [ ] `/camp-organizer-approval/:token` · `/camp-feedback/:token` · `/pre-employment/sign/:token` · `/forms/:token`

---

## Sign-off

| Step | Who logged in | Pass? | Notes |
|------|---------------|-------|-------|
| A | Platform admin | [ ] | |
| B | qa.admin (organization_admin) | [ ] | |
| C | qa.hradmin | [ ] | |
| D | qa.hrmgr | [ ] | |
| E | qa.payroll | [ ] | |
| F | qa.employee | [ ] | |
| G | qa.supply | [ ] | |
| H | qa.store | [ ] | |
| I | qa.request | [ ] | |
| J | qa.invmgr | [ ] | |
| K | qa.clinicadmin | [ ] | |
| L | qa.reception | [ ] | |
| M | qa.doctor | [ ] | |
| N | qa.nurse | [ ] | |
| O | qa.cashier | [ ] | |
| P | qa.meddir | [ ] | |
| Q–V | Blood line roles | [ ] | |
| W–Z | Billing roles | [ ] | |
| AA | Patient app + portal requests | [ ] | |
| AB | Swastha | [ ] N/A | |
| AC | Help docs | [ ] | |
| AD | Cross-checks | [ ] | |

**Org code:** `qaYYYYMMDD` = _______________  
**Overall:** Pass / Fail / Pass with issues  

---

## Related help

- <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>
- <a href="#" data-hs-route="getting-started/before-you-start">Before you start (paper & Excel)</a>
- <a href="#" data-hs-route="getting-started/by-role">Guides by role</a>
- <a href="#" data-hs-route="core/users-roles">Users & roles</a>
