# Full manual QA checklist

Use this as a **single pass** from new organisation → setup → every role → day-to-day flows → **every screen/link/button** (Phase 9). For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>. Print this page or tick boxes in a copy while you test.

<div class="callout callout--tip">
  <strong>Staff entry (always):</strong> use the tenant portal — locally
  <code>http://{orgCode}.localhost:5174/...</code>.
  Platform admin: <code>http://localhost:5174/</code>.
  Patient app (if PatientSetu): <code>http://{orgCode}.localhost:5181/</code>.
  Do <strong>not</strong> log into standalone module ports (5173 Rakht · 5175 Supply · 5176 HR · 5177 Swastha · 5179 Care) for staff testing.
</div>

**Marking:** `[ ]` pending · `[x]` pass · `[!]` fail (note bug / screenshot / role / URL)

**Pass rule:** action completes, success banner or expected list refresh, no unexplained error banner, correct nav for that role.

Also see <a href="#" data-hs-route="getting-started/before-you-start">Before you start (paper & Excel)</a>.

---

## QA seed pack (use these exact values)

Replace `YYYYMMDD` with today’s date (e.g. `20261122`). Everything below is designed to fit together.

### Organisation (Core)

| Field | Exact value |
|-------|-------------|
| Organisation name | `QA HealthSetu Campus YYYYMMDD` |
| Code (slug) | `qaYYYYMMDD` → portal `http://qaYYYYMMDD.localhost:5174/` |
| Address line 1 | `12 SG Highway` |
| City | `Ahmedabad` |
| State | `Gujarat` |
| PIN | `380054` |
| Phone | `9876500001` |
| Email | `admin@qaYYYYMMDD.test` |
| Contact person | `QA Org Admin` |
| Modules to enable | CARE + SUPPLY + BLOOD_BANK + HR + BILLING + PATIENT |

### Branding / payment / SMTP (post-READY)

| Field | Exact value |
|-------|-------------|
| App / brand name | `QA Campus` |
| Primary colour | keep default or `#2563eb` |
| Support email | `support@qaYYYYMMDD.test` |
| SMTP from address | your lab SMTP “from” (or mark N/A) |
| Payment UPI ID | `qacampus@upi` *(or real test UPI)* |
| Payee name | `QA HealthSetu Campus` |
| Sample fee amount | `500` |

### Shared password for all QA users

| Field | Value |
|-------|-------|
| Password | `QaTest@2026` *(change if your password policy differs)* |

### Workplace & HR structure

| Field | Exact value |
|-------|-------------|
| Workplace code | `MAIN` |
| Workplace name | `Main Campus` |
| PT state | `Gujarat` |
| Working week | Mon–Sat |
| Address | `12 SG Highway, Ahmedabad 380054` |
| Shift 1 | Name `Morning` · key `morning` · `08:00`–`16:00` |
| Shift 2 | Name `Evening` · key `evening` · `16:00`–`22:00` |
| Holiday sample | `26/01/YYYY` — `Republic Day` |

| Department | Roles to attach |
|------------|-----------------|
| `Administration` | organization_admin, clinic_admin, hr_admin, supply_admin |
| `Front Desk` | clinic_receptionist, receptionist, clinic_cashier, billing_cashier |
| `Clinical` | clinic_doctor, clinic_nurse, clinic_pa, clinic_counsellor, clinic_procedure_tech |
| `Laboratory` | phlebotomist, testing_specialist, technician, technician_supervisor, quality_officer |
| `Counseling` | counsellor *(blood)* |
| `Stores` | store_keeper, inventory_manager, request, supplies |
| `Medical Office` | medical_director, doctor *(blood)* |

### Employees to hire (HR) — then link login users

| Employee name | Dept | Org role | Extra fields |
|---------------|------|----------|--------------|
| `Dr Anita Shah` | Clinical | clinic_doctor | Council `GMC` · Reg `G-12345` · DOJ today · **Active** |
| `Nurse Priya Mehta` | Clinical | clinic_nurse | DOJ today · **Active** |
| `Ravi Patel` | Front Desk | clinic_receptionist | DOJ today · **Active** |
| `Sneha Desai` | Front Desk | clinic_cashier | DOJ today · **Active** |
| `Amit Joshi` | Stores | store_keeper | DOJ today · **Active** |
| `Lab Tech Kiran Shah` | Laboratory | technician | DOJ today · **Active** |
| `Counsellor Meera Shah` | Counseling | counsellor | DOJ today · **Active** |
| `Phlebotomist Neha Rana` | Laboratory | phlebotomist | DOJ today · **Active** |
| `MO Dr Vikram Patel` | Medical Office | medical_director | Council `GMC` · Reg `G-67890` · **Active** |

### Login users (tenant Settings → Users)

Pattern: `qa.{role}@qaYYYYMMDD.test` · password `QaTest@2026` · display name = role label.

| Login email | Role slug | Display name |
|-------------|-----------|--------------|
| `qa.admin@qaYYYYMMDD.test` | organization_admin | QA Org Admin |
| `qa.clinicadmin@qaYYYYMMDD.test` | clinic_admin | QA Clinic Admin |
| `qa.reception@qaYYYYMMDD.test` | clinic_receptionist | QA Reception |
| `qa.doctor@qaYYYYMMDD.test` | clinic_doctor | QA Doctor (link to Dr Anita Shah if prompted) |
| `qa.nurse@qaYYYYMMDD.test` | clinic_nurse | QA Nurse |
| `qa.cashier@qaYYYYMMDD.test` | clinic_cashier | QA Clinic Cashier |
| `qa.supply@qaYYYYMMDD.test` | supply_admin | QA Supply Admin |
| `qa.store@qaYYYYMMDD.test` | store_keeper | QA Store Keeper |
| `qa.invmgr@qaYYYYMMDD.test` | inventory_manager | QA Inventory Manager |
| `qa.request@qaYYYYMMDD.test` | request | QA Requester |
| `qa.meddir@qaYYYYMMDD.test` | medical_director | QA Medical Director |
| `qa.bbcounsellor@qaYYYYMMDD.test` | counsellor | QA BB Counsellor |
| `qa.phlebo@qaYYYYMMDD.test` | phlebotomist | QA Phlebotomist |
| `qa.testing@qaYYYYMMDD.test` | testing_specialist | QA Testing |
| `qa.tech@qaYYYYMMDD.test` | technician | QA Technician |
| `qa.qo@qaYYYYMMDD.test` | quality_officer | QA Quality Officer |
| `qa.bbreception@qaYYYYMMDD.test` | receptionist | QA BB Reception |
| `qa.hradmin@qaYYYYMMDD.test` | hr_admin | QA HR Admin |
| `qa.hrmgr@qaYYYYMMDD.test` | hr_manager | QA HR Manager |
| `qa.payroll@qaYYYYMMDD.test` | hr_payroll | QA Payroll |
| `qa.employee@qaYYYYMMDD.test` | hr_employee | QA Employee Self-Service |
| `qa.billadmin@qaYYYYMMDD.test` | billing_admin | QA Billing Admin |
| `qa.billcash@qaYYYYMMDD.test` | billing_cashier | QA Billing Cashier |
| `qa.billsup@qaYYYYMMDD.test` | billing_supervisor | QA Billing Supervisor |
| `qa.billacct@qaYYYYMMDD.test` | billing_accountant | QA Billing Accountant |

Create remaining Phase 2 roles the same way only if you need full matrix coverage (`clinic_pa`, `billing_*`, etc.).

### Care masters

| Field | Exact value |
|-------|-------------|
| Clinic display name | `QA Campus OPD` |
| Phone / email | `9876500001` / `opd@qaYYYYMMDD.test` |
| Address | `12 SG Highway, Ahmedabad, Gujarat, 380054` |
| Registration no. | `QA-CLINIC-001` |
| Languages | English, Gujarati |
| Specialty seed | General OPD *(plus one specialty you actually seed)* |
| Doctor | `Dr Anita Shah` (HR employee) |
| Schedule | Mon–Sat · `09:00`–`13:00` · slot `15` min · max `16` · room `OPD-1` |
| Fee — New consult | `New consultation` · `₹500` |
| Fee — Follow-up | `Follow-up consultation` · `₹300` |
| Fee — Dressing | `Dressing` · `₹200` |
| Fee — ECG | `ECG` · `₹400` |

### Test individual (patient / person)

| Field | Exact value |
|-------|-------------|
| Full name | `Test Patient One` |
| Sex | Female |
| Date of birth | `15/03/1990` |
| Phone | `9876511111` |
| Address | `41 Satellite Road, Ahmedabad` |
| WhatsApp consent | Yes *(if testing messages)* |

### Supply masters

| Kind | Exact value |
|------|-------------|
| Location 1 | Code `MAIN-STORE` · Name `Main store` |
| Location 2 | Code `OT-STORE` · Name `OT store` |
| Location 3 | Code `BB-FRIDGE` · Name `Blood bank fridge room` |
| Catalog 1 | `Surgical gloves M` · category consumable · unit `box` · reorder `10` · location Main store |
| Catalog 2 | `Disposable syringe 5ml` · consumable · unit `box` · reorder `20` |
| Catalog 3 | `HBsAg ELISA kit 96T` · reagent · unit `kit` · reorder `2` · location BB fridge |
| Opening stock | Gloves: **50** boxes into Main store · lot `LOT-GLOVE-01` · expiry `31/12/2027` |
| Vendor | Name `MedSupply Gujarat Pvt Ltd` · GSTIN `24AAAAA0000A1Z5` · phone `9876522222` · city Ahmedabad |
| Vendor checklist docs | GST certificate, Drug licence *(tick both as required)* |
| Draft PO | Vendor MedSupply · item Surgical gloves M · qty **20** · rate `₹180` |

### Rakht masters

| Field | Exact value |
|-------|-------------|
| Institution | `City General Hospital` · city Ahmedabad · contact `Dr Patel` · phone `9876533333` |
| Institution doctor | `Dr Patel` · dept Medicine |
| Sample donor | Name `Donor Ramesh Kumar` · DOB `10/05/1988` · Male · phone `9876544444` · blood group `O+` · weight `72` kg |
| Camp (optional) | Name `QA Weekend Camp` · date tomorrow · venue `MAIN campus lawn` |
| Equipment sample | `ELISA Reader 1` · location Lab |

### Billing module *(if BILLING)*

| Field | Exact value |
|-------|-------------|
| Charge / package | `OPD day package` · `₹800` |
| Cashier test patient | `Test Patient One` |

### Patient app *(if PATIENT)*

| Field | Exact value |
|-------|-------------|
| Patient login phone | `9876511111` (same as Test Patient One) |
| Book | Tomorrow · Dr Anita Shah · morning slot |

---

## 0. Pre-flight

- [ ] Core UI + Core API running (platform + tenant portal on **5174**)
- [ ] Module UIs running: Care, Supply, Rakht, HR, Billing as needed
- [ ] Module APIs running for subscribed packs
- [ ] Platform admin login works at `http://localhost:5174/`
- [ ] SMTP / WhatsApp / UPI ready *(or mark N/A)*
- [ ] Password sheet: all users use `QaTest@2026`

**Modules for this round:**

- [ ] CARE · [ ] SUPPLY · [ ] BLOOD_BANK · [ ] HR · [ ] BILLING · [ ] PATIENT

Skip Swastha unless an existing org still has it.

---

## Phase 1 — Platform admin: create organization

**As:** Platform admin · `http://localhost:5174/organizations`

### 1.1 Create org

- [ ] Create org with seed pack values: name `QA HealthSetu Campus YYYYMMDD`, code `qaYYYYMMDD`, Ahmedabad address, phone `9876500001`
- [ ] Enable CARE + SUPPLY + BLOOD_BANK + HR + BILLING + PATIENT
- [ ] Lands on `/organizations/:id` with success banner
- [ ] Note org id: _______________ · code: `qaYYYYMMDD`

### 1.2 Provision until READY

- [ ] Provisioning → wait until **READY**
- [ ] Apply DB / schema updates if pending → READY again
- [ ] **Seed configuration** — General OPD (Care) selected
- [ ] COMMS / platform pieces present for new tenant

### 1.3 Import roles

- [ ] Roles → **Import recommended roles**
- [ ] Confirm Care / Supply / HR / Rakht / Billing roles from Phase 2 exist
- [ ] Optional: disable unused roles

### 1.4 First org admin user

- [ ] Create `qa.admin@qaYYYYMMDD.test` · role **organization_admin** · password `QaTest@2026`
- [ ] Invite path works *(or set password manually)*

### 1.5 Org configuration tabs (post-READY)

| Tab | Exact values to save |
|-----|----------------------|
| Branding | [ ] App name `QA Campus` · support `support@qaYYYYMMDD.test` |
| Email server | [ ] Lab SMTP · test to your inbox · *(or N/A)* |
| Payment QR | [ ] UPI `qacampus@upi` · payee `QA HealthSetu Campus` · fee `500` · *(or N/A)* |
| Communications | [ ] WhatsApp test to `9876500001` · *(or N/A)* |
| Barcodes | [ ] At least one blood-bag / stock label template (or finish in tenant) |
| ID cards | [ ] One employee badge version (or finish in tenant) |
| Customize functionality | [ ] Flags match QA intent (all subscribed modules on) |
| Configuration | [ ] Review defaults |

### 1.6 Platform handoff gate

- [ ] Sign in as `qa.admin@…` at `http://qaYYYYMMDD.localhost:5174/`
- [ ] Sidebar shows Care, Supply, Rakht, HR, Billing (as enabled)
- [ ] `/settings/overview` loads

---

## Phase 2 — Roles catalog (verify after import)

Confirm each role exists for enabled modules.

### Cross-product

- [ ] `admin` · [ ] `organization_admin`

### Care

- [ ] `clinic_admin` · [ ] `clinic_receptionist` · [ ] `clinic_doctor` · [ ] `clinic_nurse` · [ ] `clinic_pa` · [ ] `clinic_procedure_tech` · [ ] `clinic_counsellor` · [ ] `clinic_cashier`

### Supply

- [ ] `supply_admin` · [ ] `collection` · [ ] `store_keeper` · [ ] `request` · [ ] `supplies` · [ ] `inventory_supervisor` · [ ] `inventory_manager` · [ ] `supplies_manager`

### Rakht

- [ ] `medical_director` · [ ] `staff` · [ ] `coordinator` · [ ] `receptionist` · [ ] `phlebotomist` · [ ] `counsellor` · [ ] `doctor` · [ ] `testing_specialist` · [ ] `technician_supervisor` · [ ] `joint_secretary` · [ ] `trustee` · [ ] `technician` · [ ] `quality_officer`

### HR

- [ ] `hr_admin` · [ ] `hr_manager` · [ ] `hr_payroll` · [ ] `hr_employee`

### Billing

- [ ] `billing_cashier` · [ ] `billing_supervisor` · [ ] `billing_accountant` · [ ] `billing_admin`

### Optional custom role

- [ ] Create role `qa_readonly` with only view/list capabilities
- [ ] Assign to throwaway `qa.readonly@qaYYYYMMDD.test`
- [ ] Confirm Settings / masters are hidden or blocked

---

## Phase 3 — Create test users

**As:** Org admin · `/system/organization?admin=users`

- [ ] Create every login from the **Login users** table in the seed pack
- [ ] Password `QaTest@2026` for each
- [ ] Spot-check: sign in as `qa.reception@…` and `qa.store@…` — Home loads, sidebar matches role, sign out works

| # | Email | Created | Can sign in |
|---|-------|---------|-------------|
| 1 | `qa.admin@…` | [ ] | [ ] |
| 2 | `qa.clinicadmin@…` | [ ] | [ ] |
| 3 | `qa.reception@…` | [ ] | [ ] |
| 4 | `qa.doctor@…` | [ ] | [ ] |
| 5 | `qa.nurse@…` | [ ] | [ ] |
| 6 | `qa.cashier@…` | [ ] | [ ] |
| 7 | `qa.supply@…` | [ ] | [ ] |
| 8 | `qa.store@…` | [ ] | [ ] |
| 9 | `qa.invmgr@…` | [ ] | [ ] |
| 10 | `qa.request@…` | [ ] | [ ] |
| 11 | `qa.meddir@…` | [ ] | [ ] |
| 12 | `qa.bbcounsellor@…` | [ ] | [ ] |
| 13 | `qa.phlebo@…` | [ ] | [ ] |
| 14 | `qa.testing@…` | [ ] | [ ] |
| 15 | `qa.tech@…` | [ ] | [ ] |
| 16 | `qa.qo@…` | [ ] | [ ] |
| 17 | `qa.bbreception@…` | [ ] | [ ] |
| 18 | `qa.hradmin@…` | [ ] | [ ] |
| 19 | `qa.hrmgr@…` | [ ] | [ ] |
| 20 | `qa.payroll@…` | [ ] | [ ] |
| 21 | `qa.employee@…` | [ ] | [ ] |
| 22 | `qa.billadmin@…` | [ ] | [ ] |
| 23 | `qa.billcash@…` | [ ] | [ ] |
| 24 | `qa.billsup@…` | [ ] | [ ] |
| 25 | `qa.billacct@…` | [ ] | [ ] |

---

## Phase 4 — Tenant Settings / get ready

**As:** `qa.admin@…` · `/settings/overview`

### 4.1 Getting started

- [ ] Overview shows task list + readiness cards
- [ ] Recommended setup: accept defaults for MAIN campus
- [ ] Guided path if shown: Organization → Recommended → Workplaces → People → Get ready
- [ ] `/settings/get-ready` — activate ready services

### 4.2 Organization

- [ ] Org details match seed pack (Ahmedabad / Gujarat / 380054)
- [ ] Workplace **MAIN** / Main Campus created with Morning + Evening shifts
- [ ] Departments created: Administration, Front Desk, Clinical, Laboratory, Counseling, Stores, Medical Office
- [ ] People & access: invite/link core staff from seed pack
- [ ] Barcodes: one blood bag + one stock label — mapping → sample print
- [ ] ID cards: one version — print for `Dr Anita Shah`

### 4.3 Service readiness

| Service | Ready / Active |
|---------|----------------|
| Patient care / Care | [ ] |
| Billing | [ ] |
| Inventory / Supply | [ ] |
| Blood bank | [ ] |
| HR | [ ] |
| Communications | [ ] *(or N/A)* |

- [ ] Activating Care does not wait on unrelated Supply tasks if Care tasks are done

---

## Phase 5 — Module masters

Order: **HR → Supply → Care → Rakht → Billing → Patient**.

### 5.1 HRSetu — as `qa.hradmin@…`

- [ ] MAIN workplace + Morning/Evening shifts + Republic Day holiday
- [ ] Departments + roles as in seed pack
- [ ] Hire all employees in seed pack (especially **Dr Anita Shah** with GMC `G-12345`)
- [ ] Status **Active** for every hire above
- [ ] `/employees` shows `Dr Anita Shah`, `Nurse Priya Mehta`, `Lab Tech Kiran Shah`

### 5.2 SupplySetu — as `qa.supply@…`

- [ ] Locations: `Main store`, `OT store`, `Blood bank fridge room`
- [ ] Catalog: Surgical gloves M, Disposable syringe 5ml, HBsAg ELISA kit 96T
- [ ] Vendor checklist: GST + Drug licence required
- [ ] Vendor: `MedSupply Gujarat Pvt Ltd` / GSTIN `24AAAAA0000A1Z5`
- [ ] Opening stock: **50** boxes gloves · lot `LOT-GLOVE-01` · expiry `31/12/2027` → Main store
- [ ] Optional: barcode print for gloves

### 5.3 CareSetu — as `qa.clinicadmin@…`

- [ ] Clinic settings: `QA Campus OPD`, reg `QA-CLINIC-001`, Ahmedabad address
- [ ] Doctors: link **Dr Anita Shah**
- [ ] Schedule: Mon–Sat 09:00–13:00, 15 min, OPD-1
- [ ] Fees: New consult ₹500, Follow-up ₹300, Dressing ₹200, ECG ₹400
- [ ] `/people` → add **Test Patient One** (DOB 15/03/1990, phone 9876511111)
- [ ] Open chart `/clinic/patients/person/:id` for that person

### 5.4 RakhtSetu — as `qa.meddir@…`

- [ ] Institution: `City General Hospital` + Dr Patel
- [ ] Equipment: `ELISA Reader 1`
- [ ] Donor questionnaire / workflows reviewed (approve if required)
- [ ] Blood label barcode sample print
- [ ] Confirm Supply BB fridge + HBsAg kit exist *(do not create catalog inside Rakht)*

### 5.5 Billing — as `qa.billadmin@…` *(if BILLING)*

- [ ] Master charge / package `OPD day package` ₹800
- [ ] Cashier desk opens for `qa.billcash@…`

### 5.6 PatientSetu — as `qa.clinicadmin@…` *(if PATIENT)*

- [ ] Portal settings pane saved
- [ ] `/clinic/portal-requests` opens
- [ ] Patient app: `http://qaYYYYMMDD.localhost:5181/` loads

---

## Phase 6 — Happy paths (use seed people & items)

### 6.1 Care — reception → doctor → nurse → cashier

- [ ] As `qa.reception@…`: `/people` shows Test Patient One (or add if missing)
- [ ] Book appointment: **Test Patient One** · **Dr Anita Shah** · today or tomorrow · 09:00 slot
- [ ] As `qa.doctor@…`: OPD → open visit → note “URI — symptomatic care” · Rx paracetamol 500 mg · save
- [ ] As `qa.nurse@…`: vitals for same visit (e.g. BP `120/80`, pulse `78`, temp `98.6°F`)
- [ ] As `qa.cashier@…`: bill **New consultation ₹500** (+ Dressing ₹200 if done) · mark paid Cash
- [ ] Optional WhatsApp to `9876511111` with consent
- [ ] Spot-check reports / audit

### 6.2 Supply — store → request → approve → PO

- [ ] As `qa.store@…`: confirm gloves stock ≥ 50 in Main store
- [ ] As `qa.request@…`: request **5** boxes Surgical gloves M for OT store
- [ ] As `qa.invmgr@…` or supply admin: **Approve** request
- [ ] Movement / issue 5 boxes Main store → OT store
- [ ] Draft PO: MedSupply · gloves × 20 @ ₹180 · save draft
- [ ] Receive path (or simulate) against that PO
- [ ] Add asset e.g. `BP Monitor QA-01` in Main store / Clinical
- [ ] Daily QC / staff task: complete one checklist item if templates exist

### 6.3 Rakht — counsellor → phlebo → testing → issue

- [ ] As `qa.bbcounsellor@…` / reception: register **Donor Ramesh Kumar** (O+, 72 kg, phone 9876544444)
- [ ] Counselling: fit to donate
- [ ] As `qa.phlebo@…`: collection complete
- [ ] As `qa.testing@…`: TTI / blood group path for the unit
- [ ] As `qa.tech@…`: separation / processing
- [ ] As `qa.qo@…`: component QC pass
- [ ] Crossmatch / issue: request from **City General Hospital** · component for patient name `CGH Bed 12`
- [ ] Optional camp: `QA Weekend Camp` + one registration
- [ ] Print bag / component label

### 6.4 HR — hire → attendance → leave → self-service

- [ ] As `qa.hradmin@…`: hire extra employee `Temp Staff One` · Front Desk · clinic_receptionist · Active
- [ ] Assign Morning shift on MAIN for today
- [ ] Mark attendance present for Temp Staff One
- [ ] Leave: apply 1 day casual leave next week → as `qa.hrmgr@…` approve
- [ ] As `qa.employee@…`: My day / check-in / leave view loads
- [ ] As `qa.payroll@…`: open salary / statutory / reports (smoke)

### 6.5 Billing module *(if BILLING)*

- [ ] As `qa.billcash@…`: charge Test Patient One · `OPD day package` ₹800 · collect Cash
- [ ] As `qa.billsup@…`: approval / credit-note path if required (₹100 adjustment)
- [ ] Day close for today
- [ ] As `qa.billacct@…`: open reports

### 6.6 Patient portal *(if PATIENT)*

- [ ] On `:5181` use phone `9876511111` / Test Patient One
- [ ] Book tomorrow with Dr Anita Shah
- [ ] Staff: request appears in `/clinic/portal-requests`
- [ ] Staff action updates patient-visible status

### 6.7 Cross-module bundles

- [ ] **Blood centre:** Lab Tech Kiran Shah active → gloves in BB fridge room → donor Ramesh → label print
- [ ] **Clinic:** Dr Anita Shah in doctor picker → book Test Patient One → OPD → ₹500 bill
- [ ] **Campus:** one smoke path per live module without opening :5173/:5175/:5176/:5179

---

## Phase 7 — Role-by-role capability smoke

Sign in as each user · confirm **can** / **must not**.

### 7.1 Admins

| Login | Must can | Must not |
|-------|----------|----------|
| `qa.admin@…` | [ ] Settings, Users, all modules | — |
| `qa.clinicadmin@…` | [ ] Clinic settings, doctors, fees | [ ] Supply vendor create if not granted |
| `qa.hradmin@…` | [ ] Workplaces, hire | [ ] Blood policy approve if not granted |
| `qa.supply@…` | [ ] Catalog, vendors, PO | [ ] Care Rx write if not granted |
| `qa.meddir@…` | [ ] BB clinical config | [ ] Payroll edit if not granted |
| `qa.billadmin@…` | [ ] Billing masters | [ ] HR hire if not granted |

### 7.2 Care line

| Login | Smoke |
|-------|-------|
| `qa.reception@…` | [ ] Book Test Patient One · cannot edit fee masters |
| `qa.doctor@…` | [ ] OPD / Rx · limited admin |
| `qa.nurse@…` | [ ] Vitals · no fee master edit |
| `qa.cashier@…` | [ ] Collect ₹500 · no doctor schedule edit |

### 7.3 Supply line

| Login | Smoke |
|-------|-------|
| `qa.store@…` | [ ] Stock in/out gloves |
| `qa.invmgr@…` | [ ] Approve request |
| `qa.request@…` | [ ] Raise request · cannot approve if policy forbids |

### 7.4 Rakht line

| Login | Smoke |
|-------|-------|
| `qa.bbreception@…` | [ ] Donor intake |
| `qa.bbcounsellor@…` | [ ] Counselling |
| `qa.phlebo@…` | [ ] Collection |
| `qa.testing@…` | [ ] Testing |
| `qa.tech@…` | [ ] Processing |
| `qa.qo@…` | [ ] QC |

### 7.5 HR / Billing line

| Login | Smoke |
|-------|-------|
| `qa.hrmgr@…` | [ ] Approve leave |
| `qa.payroll@…` | [ ] Salary / statutory views |
| `qa.employee@…` | [ ] Self-service only |
| `qa.billcash@…` | [ ] Desk charge |
| `qa.billsup@…` | [ ] Approvals / day close assist |
| `qa.billacct@…` | [ ] Reports |

---

## Phase 8 — UI / safety gates

- [ ] Lists: title + count left; Refresh (+ Add) same header row
- [ ] Destructive actions use ConfirmDialog (delete user, discard unit, day close, data reset)
- [ ] No `window.confirm` for those paths
- [ ] Errors in-page banner
- [ ] Dates **DD/MM/YYYY** (e.g. patient DOB shows `15/03/1990`)
- [ ] Empty states short
- [ ] Individuals only via `/people`
- [ ] Portal embeds stay on **5174**

### Dangerous paths

- [ ] Disable `qa.readonly@…` (if created) → cannot sign in
- [ ] Day close → cannot freely post without reopen policy
- [ ] Merge duplicates / data reset only with ConfirmDialog + authorized role

---

## Phase 9 — Every screen, link & primary button

**Pass rule for each row:** open URL on `http://qaYYYYMMDD.localhost:5174{path}` (or platform host) → page loads → run **Primary check** → no unexplained error banner. Skip rows for modules you did not enable. Mark redirects as **Redirect OK** if they land on the target.

**As:** `qa.admin@…` unless a row says another role.

### 9.0 Help docs site (this document app)

Open `https://mahavir-b.github.io/healthsetu_docs/` and tick every sidebar page loads:

| Doc page | Pass |
|----------|------|
| Home | [ ] |
| Getting started — overview, login, by-role, before-you-start | [ ] |
| Prep — HR / Rakht / Care / Supply / Swastha | [ ] |
| Go-live checklist · **This QA checklist** · FAQ · Glossary | [ ] |
| Security — overview, tenant isolation, Azure, access | [ ] |
| Core — overview, inbox, users-roles, barcodes, settings, communications | [ ] |
| RakhtSetu — overview, donors, camps, collections, processing, testing, patients-requests, qc | [ ] |
| SupplySetu — overview, catalog-stock, assets, vendors-po, checklists | [ ] |
| HRSetu — overview, employees, attendance-leave, payroll, my-hr, reports | [ ] |
| CareSetu — overview, patients, appointments, opd, procedures, counsellor, billing, setup | [ ] |
| SwasthaSetu — overview, exams, site-checks | [ ] |
| How to add screenshots & videos | [ ] |

### 9.1 Platform admin (`http://localhost:5174`)

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Login | `/login` | Sign in | [ ] |
| Organizations list | `/organizations` | Search + open QA org | [ ] |
| Create organization | `/organizations/new` | Form fields load (do not create second org unless needed) | [ ] |
| Org Profile | `/organizations/:id` | Save / view profile | [ ] |
| Provisioning | `?admin=provisioning` | Status READY visible | [ ] |
| Users | `?admin=users` | Refresh · Add user button | [ ] |
| Add org user | `/organizations/:id/users/new` | Form loads | [ ] |
| Edit org user | `/organizations/:id/users/:userId` | Open `qa.admin` | [ ] |
| Roles | `?admin=roles` | Import / list | [ ] |
| New role | `/organizations/:id/roles/new` | Form loads | [ ] |
| Edit role | `/organizations/:id/roles/:roleId` | Open organization_admin | [ ] |
| Configuration | `?admin=configuration` | Values load | [ ] |
| Branding | `?admin=branding` | Save | [ ] |
| Email server | `?admin=email` | Save · Send test *(or N/A)* | [ ] |
| Payment QR | `?admin=payments` | Save *(or N/A)* | [ ] |
| Communications | `?admin=communications` | Save · test *(or N/A)* | [ ] |
| ABDM | `?admin=abdm` | Page loads *(or N/A)* | [ ] |
| Barcodes list | `?admin=barcodes` | Refresh · open template | [ ] |
| Barcode mapping | `.../barcodes/:templateId/mapping` | Toggle one field · Save | [ ] |
| Barcode designer | `.../barcodes/:templateId/designer` | Canvas loads | [ ] |
| ID cards | `?admin=id-cards` | Open version | [ ] |
| ID card designer | `.../id-cards/:versionId/designer` | Canvas loads | [ ] |
| Customize functionality | `?admin=customize` | Flags visible | [ ] |
| Platform users | `/users` | List · Refresh | [ ] |
| New platform user | `/users/new` | Form loads | [ ] |
| Platform user detail | `/users/:userId` | Open one user | [ ] |
| Communications (platform) | `/communications` | Page loads | [ ] |
| Index redirect | `/` | Lands on `/organizations` | [ ] |

### 9.2 Tenant portal chrome

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Home | `/` or `/home` | Cards / My Day load | [ ] |
| Inbox | `/inbox` | List · Refresh | [ ] |
| Preferences | `/user-preference` | Save a preference | [ ] |
| Account redirect | `/account` | → `/user-preference` | [ ] |
| Reports library | `/insight/reports` | List opens | [ ] |
| Click analysis | `/insight/clicks` | Page opens *(admin)* | [ ] |
| Individuals | `/people` | Search · Add · open Test Patient One | [ ] |
| Add individual | `/people/new` | Form · Cancel | [ ] |
| Edit individual | `/people/:id/edit` | Save Test Patient One | [ ] |
| Person → Care chart | `/people/:id` | Redirects to chart when CARE on | [ ] |
| Patients redirect | `/patients` | → `/people` | [ ] |
| Clinic patients redirect | `/clinic/patients` | → `/people` | [ ] |
| Setup / Settings | `/settings/overview` | Tasks + readiness | [ ] |
| Legacy `/setup` | `/setup` | → settings overview | [ ] |
| Tenant Users | `/system/organization?admin=users` | Refresh · Add | [ ] |
| Add tenant user | `/system/organization/users/new` | Form | [ ] |
| Tenant Barcodes | `?admin=barcodes` | Open template | [ ] |
| Tenant barcode mapping | `/system/organization/barcodes/:id/mapping` | Save | [ ] |
| Tenant barcode designer | `.../barcodes/:id/designer` | Canvas | [ ] |
| Tenant ID cards | `?admin=id-cards` | Open version | [ ] |
| ID card designer | `.../id-cards/:id/designer` | Canvas | [ ] |
| No access | `/no-access` | Empty state (or skip) | [ ] |

### 9.3 Settings hub — every page

Open from Settings sidebar (or paste path). Primary = page loads + Save / Continue / Approve if present.

| Screen | Path | Pass |
|--------|------|------|
| Setup overview | `/settings/overview` | [ ] |
| Get ready | `/settings/get-ready` | [ ] |
| Recommended setup | `/settings/recommended` | [ ] |
| Smart setup | `/settings/smart-setup` | [ ] |
| All settings | `/settings/all-settings` | [ ] |
| Organization details | `/settings/organization` | [ ] |
| Workplaces | `/settings/workplaces` | [ ] |
| Inheritance | `/settings/inheritance` | [ ] |
| Departments & job titles | `/settings/departments` | [ ] |
| Job title | `/settings/job-title` | [ ] |
| People & access | `/settings/people` | [ ] |
| Invite | `/settings/invite` | [ ] |
| Documents & branding | `/settings/documents` | [ ] |
| Access profiles | `/settings/access-profiles` | [ ] |
| Approvals | `/settings/approvals` | [ ] |
| Integrations | `/settings/integrations` | [ ] |
| Data import | `/settings/data-import` | [ ] |
| Audit history | `/settings/audit` | [ ] |
| Template updates | `/settings/template-updates` | [ ] |
| Impact | `/settings/impact` | [ ] |
| Platform template manager | `/settings/platform` | [ ] *(HS staff)* |
| **Patient care** overview | `/settings/pc` | [ ] |
| Doctors & specialties | `/settings/pc-doctors` | [ ] |
| Appointments & hours | `/settings/pc-appointments` | [ ] |
| Clinical templates | `/settings/pc-clinical` | [ ] |
| Patient portal | `/settings/pc-portal` | [ ] |
| **Billing** overview | `/settings/bl` | [ ] |
| Charges & pricing | `/settings/bl-charges` | [ ] |
| Invoices & taxes | `/settings/bl-invoices` | [ ] |
| Online payments | `/settings/bl-payments` | [ ] |
| **Inventory** overview | `/settings/inv` | [ ] |
| Catalog & locations | `/settings/inv-catalog` | [ ] |
| Vendors & approvals | `/settings/inv-vendors` | [ ] |
| Assets / QC | `/settings/inv-assets` | [ ] |
| **Blood bank** overview | `/settings/bb` | [ ] |
| Facility & licence | `/settings/bb-facility` | [ ] |
| Policies | `/settings/bb-policies` | [ ] |
| Policy detail | `/settings/bb-policy` | [ ] |
| Components | `/settings/bb-components` | [ ] |
| Storage equipment | `/settings/bb-storage` | [ ] |
| **HR** overview | `/settings/hr` | [ ] |
| Employment & leave | `/settings/hr-employment` | [ ] |
| Leave plan | `/settings/hr-leave` | [ ] |
| Required documents | `/settings/hr-docs` | [ ] |
| Time & attendance | `/settings/hr-time` | [ ] |
| Shifts | `/settings/hr-shifts` | [ ] |
| Shift eligibility | `/settings/hr-eligibility` | [ ] |
| Holidays | `/settings/hr-holidays` | [ ] |
| Check-in | `/settings/hr-checkin` | [ ] |
| Payroll | `/settings/hr-payroll` | [ ] |
| Training & credentials | `/settings/hr-training` | [ ] |
| **Comms** overview | `/settings/cm` | [ ] |
| Automated messages | `/settings/cm-auto` | [ ] |
| Channels | `/settings/cm-channels` | [ ] |
| WhatsApp | `/settings/cm-wa` | [ ] |
| Message templates | `/settings/cm-templates` | [ ] |
| Template detail | `/settings/cm-template` | [ ] |
| Preferences | `/settings/cm-prefs` | [ ] |
| Lab / DX overview | `/settings/dx` | [ ] |

### 9.4 CareSetu screens

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Clinic dashboard | `/clinic` | Loads | [ ] |
| Appointments | `/clinic/appointments` | Refresh · book | [ ] |
| Waitlist | `/clinic/appointments?view=waitlist` | Tab/view | [ ] |
| OPD | `/clinic/opd` | Open visit | [ ] |
| Refills | `/clinic/refills` | List | [ ] |
| Portal requests | `/clinic/portal-requests` | List *(PATIENT)* | [ ] |
| Clinic billing | `/clinic/billing` | Desk *(hidden if BILLING on — note)* | [ ] |
| Doctors | `/clinic/doctors` | Open Dr Anita Shah | [ ] |
| Fee items | `/clinic/fee-items` | Edit New consultation ₹500 | [ ] |
| Clinic settings | `/clinic/settings` | Save letterhead | [ ] |
| Portal pane | `/clinic/settings?pane=portal` | Save | [ ] |
| Integrations pane | `/clinic/settings?pane=integrations` | Opens | [ ] |
| Clinical / money / roles / people / audit / merge panes | `/clinic/settings?pane=…` | Each pane opens | [ ] |
| Templates | `/clinic/templates` | Open one domain | [ ] |
| Template domain | `/clinic/templates/:code` | List | [ ] |
| Procedures | `/clinic/procedures` | Board | [ ] |
| Start procedure | `/clinic/procedures/start` | Wizard opens | [ ] |
| Book sitting | `/clinic/procedures/book` | Form | [ ] |
| Counsellor | `/clinic/counsellor` | List | [ ] |
| Reports | `/clinic/reports` | Open one report | [ ] |
| Doctor desk | `/clinic/doctor-desk` | Queue | [ ] |
| Nursing | `/clinic/nursing` | Queue | [ ] |
| Lab | `/clinic/lab` | Worklist | [ ] |
| Token display | `/clinic/token-display` | Display | [ ] |
| Audit | `/clinic/audit` | List | [ ] |
| Merge duplicates | `/clinic/merge` | Tool (do not merge unless test) | [ ] |
| Person chart | `/clinic/patients/person/:personId` | Tabs: summary, labs, procedures, billing, documents, details | [ ] |
| Token TV | `/clinic/tv` | Public display | [ ] |

### 9.5 SupplySetu screens

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Supply reports | `/reports` | Open one report | [ ] |
| Inventory health | `/dashboard/inventory` | Dashboard | [ ] |
| Staff tasks | `/staff-tasks` | List · Refresh | [ ] |
| Daily QC | `/daily-qc` | Open checklist | [ ] |
| Catalog | `/inventory/catalog` | Refresh · Add | [ ] |
| Catalog new | `/inventory/catalog/new` | Form | [ ] |
| Catalog edit | `/inventory/catalog/:typeId/edit` | Edit gloves | [ ] |
| Stock | `/inventory` | Tabs stock | [ ] |
| Add stock | `/inventory/stock/new` | Form | [ ] |
| Edit stock | `/inventory/stock/:id/edit` | Open gloves lot | [ ] |
| Reorder | `/inventory/reorder` | Form | [ ] |
| Receive | `/inventory/receive` | Form | [ ] |
| Stock intake | `/inventory/stock-intake` | Form | [ ] |
| Assets | `/inventory/assets` | List · Add | [ ] |
| Asset detail | `/inventory/assets/:assetId` | Open one | [ ] |
| Asset import | `/inventory/assets/import` | Wizard | [ ] |
| Service contracts | `/inventory/service-contracts` | List | [ ] |
| Request | `/inventory/request` | Raise 5 gloves | [ ] |
| Approvals | `/inventory/approvals` | Approve | [ ] |
| Movement | `/inventory/movement` | Move stock | [ ] |
| Setup redirect | `/inventory/setup` | → settings / setup | [ ] |
| Vendors | `/inventory/vendors` | Open MedSupply | [ ] |
| Vendor new | `/inventory/vendors/new` | Form | [ ] |
| Purchase orders | `/inventory/purchase-orders` | List · New | [ ] |
| PO new | `/inventory/purchase-orders/new` | Draft gloves ×20 | [ ] |
| PO detail/edit | `/inventory/purchase-orders/:id` | Open draft | [ ] |
| Quotations | `/inventory/quotations` | List · New | [ ] |
| Quotation new | `/inventory/quotations/new` | Form | [ ] |
| Locations | `/inventory/locations` | Main / OT / BB | [ ] |
| Custom fields | `/inventory/custom-fields` | Page | [ ] |
| Parameters | `/inventory/parameters` | Save | [ ] |
| Vendor checklist | `/inventory/vendor-checklist` | GST + Drug licence | [ ] |
| Asset workflow mapping | `/inventory/asset-workflow-mapping` | Page | [ ] |
| Checklists / QC templates | `/admin/qc-checklist-templates` | List | [ ] |
| Checklist new | `/inventory/checklists/new` | Form | [ ] |
| Vendor return | `/inventory/vendor-returns/new` | Form | [ ] |
| Supply data reset | `/admin/supply-data-reset` | ConfirmDialog only — **do not reset** unless intended | [ ] |
| Hub tabs | `/inventory?tab=stock\|checklists\|qc\|quotations\|invoices\|purchase-orders` | Each tab | [ ] |

### 9.6 RakhtSetu screens

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Dashboard | `/dashboard` | Loads | [ ] |
| Dashboard hospital / executive / camps / donors / lab / blood-inv / crossmatch / requests / compliance | `/dashboard/…` | Each opens | [ ] |
| QC dashboard | `/dashboard/qc` | Loads | [ ] |
| Compliance | `/dashboard/compliance` | Loads | [ ] |
| Camps | `/camps` | List · Add / open QA Weekend Camp | [ ] |
| Camp detail | `/camps/:campId` | Opens | [ ] |
| Donors | `/donors` | Search Ramesh · Add | [ ] |
| Donor new | `/donors/new` | Form | [ ] |
| Donor detail/edit/evaluation | `/donors/…` | Open Ramesh | [ ] |
| Collections | `/collections` | List | [ ] |
| Processing | `/blood-inventory/pending-separation` | List | [ ] |
| Blood inventory tabs | pending-separation, bulk-separation, pending-supervisor, pending-doctor, pending-testing, components, transfers, research, donated-nhp, donated-components, discarded, autoclave-waste | Each tab opens | [ ] |
| Component QC | `/blood-inventory/component-qc` | List | [ ] |
| Approvals (doctor components) | `/blood-inventory/pending-doctor-components` | List | [ ] |
| Separation / triple-bag | `/workstation/separation`, `/blood-inventory/triple-bag-workspace` | Opens | [ ] |
| Testing | `/testing` → pending | List | [ ] |
| Testing enter / add / completed / tti-panel | `/testing/…` | Each | [ ] |
| Workstation | `/workstation` | Hub | [ ] |
| Donor station | `/workstation/donor` | Workflow | [ ] |
| Lab batch | `/workstation/lab` | Batch | [ ] |
| Issue request | `/workstation/issue` | Form City General | [ ] |
| Crossmatch | `/crossmatch` | → requests in progress | [ ] |
| Requests | `/requests` | List · New | [ ] |
| Request new | `/requests/new` | Form | [ ] |
| Institutions | `/hospitals` | City General | [ ] |
| Partner blood banks | `/partner-blood-banks` | List | [ ] |
| Add bag | `/add-bag` | Form | [ ] |
| Tasks | `/tasks` | List | [ ] |
| Support | `/support` | Page | [ ] |
| Workflows | `/admin/workflows` | Open questionnaire | [ ] |
| Workflow detail | `/admin/workflows/:key` | Opens | [ ] |
| Equipment configuration | `/admin/equipment-configuration` | ELISA Reader 1 | [ ] |
| Blood data reset | `/admin/blood-data-reset` | ConfirmDialog only — do not wipe | [ ] |
| ELISA run | `/dashboard/lab/elisa` | Opens | [ ] |

### 9.7 HRSetu screens

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| HR dashboard | `/hr/dashboard` | Loads | [ ] |
| HR reports | `/hr/reports` | Open one | [ ] |
| Employees | `/employees` | Search Dr Anita · Hire | [ ] |
| Hire | `/employees/hire` | Wizard | [ ] |
| Employee detail | `/employees/:id` | Open Dr Anita | [ ] |
| Onboarding | `/onboarding` | List | [ ] |
| Training | `/training` | List | [ ] |
| BGV | `/bgv` | List | [ ] |
| Salary | `/salary` | List | [ ] |
| Salary run | `/salary/runs/:runId` | Open if any | [ ] |
| Statutory | `/statutory` | List | [ ] |
| FnF | `/fnf` | List | [ ] |
| Workplaces | `/workplaces` | MAIN | [ ] |
| Workplace detail / dept | `/workplaces/:id` | Departments | [ ] |
| Holidays | `/holidays` | Republic Day | [ ] |
| Holiday templates | `/holiday-templates` | Page | [ ] |
| Departments | `/departments` | Page | [ ] |
| Shifts | `/shifts` | Morning / Evening | [ ] |
| Attendance | `/attendance` | Mark / view | [ ] |
| Leave | `/leave` | Apply / approve | [ ] |
| Employee setup | `/employee-setup` | Hub tabs | [ ] |
| Document library | `/document-library` | Upload/view | [ ] |
| Employee files | `/employee-files` | List | [ ] |
| Work clearances | `/work-clearances` | List | [ ] |
| **Self-service** My day | `/employee/me` | As `qa.employee@…` | [ ] |
| Check in | `/employee/checkin` | [ ] |
| Clearances (me) | `/employee/clearances` | [ ] |
| Leave (me) | `/employee/leave` | [ ] |
| Salary slips | `/employee/salary` | [ ] |
| Documents (me) | `/employee/documents` | [ ] |
| Attendance (me) | `/employee/attendance` | [ ] |
| My shifts | `/employee/shifts` | [ ] |
| Holidays (me) | `/employee/holidays` | [ ] |
| Profile (me) | `/employee/profile` | [ ] |

### 9.8 Billing module screens

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Cashier desk | `/billing` | Open desk | [ ] |
| Bill composer | `/billing/bills/:id` | Open / create bill | [ ] |
| Accounts | `/billing/accounts` | List | [ ] |
| Account detail | `/billing/accounts/:id` | Open one | [ ] |
| Packages | `/billing/packages` | OPD day package | [ ] |
| Approvals | `/billing/approvals` | Queue | [ ] |
| Credit notes | `/billing/credit-notes` | List | [ ] |
| Refunds alias | `/billing/refunds` | Same page | [ ] |
| Day close | `/billing/day-close` | Workflow | [ ] |
| Reports | `/billing/reports` | Open one | [ ] |
| Charge master | `/billing/masters` | List | [ ] |
| Settings | `/billing/settings` | Save | [ ] |

### 9.9 SwasthaSetu screens *(only if SWASTHA enabled)*

| Screen | Path | Pass |
|--------|------|------|
| `/ohc` dashboard | [ ] |
| `/ohc/employees` · pre-employment · pre-employment-authorization · opd · periodic-medical · audiometry · health-checkup · vaccination | [ ] |
| `/ohc/first-aiders` · ambulances · ambulance · first-aid-box · canteen-hygiene · plant-inspection | [ ] |
| `/ohc/collection-agencies` · biomedical-waste · monthly-ohc-work · yearly-calendar · daily-report | [ ] |
| `/ohc/organization` · departments · job-titles · medical-tests · test-requirements · documents | [ ] |

### 9.10 Patient app (`http://qaYYYYMMDD.localhost:5181`)

| Screen | Path | Primary check | Pass |
|--------|------|---------------|------|
| Sign in | `/signin` | Login phone `9876511111` | [ ] |
| Home | `/` | Loads | [ ] |
| Visits | `/visits` | List | [ ] |
| Visit today | `/visits/:id/today` | Day view | [ ] |
| Book | `/book` | Book Dr Anita | [ ] |
| Records | `/records` | List | [ ] |
| Medicines | `/medicines` | List | [ ] |
| Bills | `/bills` | List | [ ] |
| Profile | `/profile` | Form | [ ] |
| Notifications | `/notifications` | List | [ ] |
| Messages | `/messages` | List | [ ] |
| More | `/more` | Menu | [ ] |
| Privacy / Security / Account | `/privacy` `/security` `/account` | Each | [ ] |
| ABHA | `/abha` | Flow opens | [ ] |
| Services | `/services` | Hub | [ ] |
| Emergency | `/services/emergency` | Page | [ ] |
| Invite / request-status | `/invite/:token`, `/request-status/:id` | If token available | [ ] |
| Forms | `/forms/:id` | If available | [ ] |

### 9.11 Public token links *(smoke open if you have a live token)*

| Flow | Path pattern | Pass / N/A |
|------|--------------|------------|
| Vendor onboarding | `/vendor/onboarding/:token` | [ ] |
| Employee onboarding | `/employee/onboarding/:token` | [ ] |
| Offer sign | `/employee/offer-sign/:token` | [ ] |
| Vendor quotation | `/quotation/vendor/:token` | [ ] |
| Vendor PO | `/purchase-order/vendor/:token` | [ ] |
| PO confirmed | `/purchase-order/confirmed/:token` | [ ] |
| Camp organizer approval | `/camp-organizer-approval/:token` | [ ] |
| Camp feedback | `/camp-feedback/:token` | [ ] |
| Pre-employment sign | `/pre-employment/sign/:token` | [ ] |
| Care public form | `/forms/:token` | [ ] |

### 9.12 Header / sidebar / chrome buttons (every module)

On Home and one screen per module, verify:

| Control | Pass |
|---------|------|
| Tenant sidebar: each subscribed module group expands | [ ] |
| Click every sidebar leaf once (matches Phase 9.2–9.9) | [ ] |
| Top / page **Refresh** icon where present | [ ] |
| Page **Add** / primary CTA on lists | [ ] |
| Row **Edit** (pencil) on Individuals, Employees, Catalog, Fees | [ ] |
| Row overflow / three-dot menu opens | [ ] |
| **Cancel** on forms returns without error | [ ] |
| **Save** shows success banner | [ ] |
| **Confirm** / **Cancel** on ConfirmDialog | [ ] |
| Sign out · sign back in | [ ] |
| Branding shows `QA Campus` | [ ] |

### 9.13 Redirect sanity

| From | Expect | Pass |
|------|--------|------|
| `/setup` | `/settings/overview` | [ ] |
| `/patients`, `/clinic/patients` | `/people` | [ ] |
| `/account` | `/user-preference` | [ ] |
| `/testing` | `/testing/pending` | [ ] |
| `/crossmatch` | `/requests?tab=inProgress` | [ ] |
| `/blood-inventory` | pending-separation | [ ] |
| `/blood-banks` | partner-blood-banks | [ ] |
| `/inventory/add` | `/inventory/stock/new` | [ ] |
| `/inventory/equipment` | assets | [ ] |
| `/clinic/schedules` | `/clinic` | [ ] |

---

## Phase 10 — Sign-off

| Area | Tester | Date | Pass? | Notes |
|------|--------|------|-------|-------|
| Phase 1 READY | | | [ ] | |
| Phase 2–3 Roles & users | | | [ ] | |
| Phase 4–5 Settings & masters | | | [ ] | |
| Phase 6 Happy paths | | | [ ] | |
| Phase 7 Role matrix | | | [ ] | |
| Phase 8 Safety | | | [ ] | |
| Phase 9.0 Help docs | | | [ ] | |
| Phase 9.1 Platform admin | | | [ ] | |
| Phase 9.2 Portal chrome | | | [ ] | |
| Phase 9.3 Settings hub | | | [ ] | |
| Phase 9.4 Care | | | [ ] | |
| Phase 9.5 Supply | | | [ ] | |
| Phase 9.6 Rakht | | | [ ] | |
| Phase 9.7 HR | | | [ ] | |
| Phase 9.8 Billing | | | [ ] | |
| Phase 9.9 Swastha | | | [ ] N/A | |
| Phase 9.10 Patient app | | | [ ] | |
| Phase 9.11 Public tokens | | | [ ] | |
| Phase 9.12 Chrome buttons | | | [ ] | |
| Phase 9.13 Redirects | | | [ ] | |

**Org code:** `qaYYYYMMDD` = _______________  
**Build / env:** _______________  
**Overall:** Pass / Fail / Pass with issues  

---

## Quick URL cheat sheet

| What | URL |
|------|-----|
| Help docs | `https://mahavir-b.github.io/healthsetu_docs/` |
| This checklist | `https://mahavir-b.github.io/healthsetu_docs/#/getting-started/manual-qa-checklist` |
| Platform orgs | `http://localhost:5174/organizations` |
| Tenant home | `http://qaYYYYMMDD.localhost:5174/` |
| Settings | `.../settings/overview` |
| Users | `.../system/organization?admin=users` |
| Individuals | `.../people` |
| Appointments | `.../clinic/appointments` |
| Inventory | `.../inventory` |
| POs | `.../inventory/purchase-orders` |
| Donors | `.../donors` |
| Employees | `.../employees` |
| Billing | `.../billing` |
| Patient app | `http://qaYYYYMMDD.localhost:5181/` |

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
