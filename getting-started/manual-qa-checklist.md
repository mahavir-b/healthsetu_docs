# Full manual QA checklist

Use this as a **single pass** from new organisation → setup → every role → day-to-day flows. For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>. Print this page or tick boxes in a copy while you test.

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

## Phase 9 — Sign-off

| Area | Tester | Date | Pass? | Notes |
|------|--------|------|-------|-------|
| Phase 1 READY | | | [ ] | |
| Phase 2 Roles | | | [ ] | |
| Phase 3 Users | | | [ ] | |
| Phase 4 Settings | | | [ ] | |
| Phase 5 Masters | | | [ ] | |
| Phase 6 Care | | | [ ] | |
| Phase 6 Supply | | | [ ] | |
| Phase 6 Rakht | | | [ ] | |
| Phase 6 HR | | | [ ] | |
| Phase 6 Billing | | | [ ] | |
| Phase 6 Patient | | | [ ] | |
| Phase 7 Roles | | | [ ] | |
| Phase 8 Safety | | | [ ] | |

**Org code:** `qaYYYYMMDD` = _______________  
**Build / env:** _______________  
**Overall:** Pass / Fail / Pass with issues  

---

## Quick URL cheat sheet

| What | URL |
|------|-----|
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
