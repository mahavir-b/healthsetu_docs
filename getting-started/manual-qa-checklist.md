# Full manual QA checklist

Use this as a **single pass** from new organisation → setup → every role → day-to-day flows. For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>.

<div class="callout callout--tip">
  <strong>Staff entry (always):</strong> tenant portal
  <code>http://{orgCode}.localhost:5174/...</code>.
  Platform admin: <code>http://localhost:5174/</code>.
  Patient app: <code>http://{orgCode}.localhost:5181/</code>.
  Do <strong>not</strong> use standalone module ports (5173 / 5175 / 5176 / 5177 / 5179) for staff login.
</div>

**Marking:** `[ ]` pending · `[x]` pass · `[!]` fail (bug / screenshot / role / URL)  
**Pass rule:** action completes, expected banner or list refresh, correct nav for that role.

---

## Fixed QA seed (use these exact values)

Use **one** test organisation. Copy the tables below into the UI — do not invent alternate names mid-run (breaks cross-module pickers).

### Organisation (platform create)

| Field | Value |
|-------|--------|
| Legal / display name | `QA Demo Multispecialty Hospital` |
| Code (slug) | `qa20261122` *(or `qa` + today’s YYYYMMDD)* |
| Portal URL | `http://qa20261122.localhost:5174/` |
| Address line 1 | `12 Ring Road, Near Metro Station` |
| City | `Mumbai` |
| State | `Maharashtra` |
| PIN | `400069` |
| Phone | `9876500001` |
| Email | `admin@qa20261122.test` |
| Contact person | `Priya Shah` |
| Modules to enable | CARE · SUPPLY · BLOOD_BANK · HR · BILLING · PATIENT |

### Branding / payments / email (examples)

| Setting | Example value |
|---------|----------------|
| App name | `QA Demo Hospital` |
| Primary colour | `#1d9e75` (or product default) |
| Support email | `support@qa20261122.test` |
| SMTP from | `noreply@qa20261122.test` |
| Test email To | your real inbox |
| UPI ID | `qademo@upi` |
| Payee name | `QA Demo Multispecialty Hospital` |
| Bag reserve fee (if shown) | `500` |
| WhatsApp display number | your sandbox / test number |

### Shared password for all QA users

| Field | Value |
|-------|--------|
| Password | `QaTest@2026` |
| Email pattern | `qa.{role}@qa20261122.test` |

### Workplace

| Field | Value |
|-------|--------|
| Code | `MAIN` |
| Name | `Main Campus` |
| State (Professional Tax) | `Maharashtra` |
| Working week | Mon–Sat |
| Address | same as org · lat/long optional |
| Geofence | skip for QA unless testing attendance geo |

### Shifts on MAIN

| Name | Key | Start | End | Roles needed (examples) |
|------|-----|-------|-----|-------------------------|
| Morning | `morning` | `08:00` | `16:00` | clinic_receptionist, clinic_doctor, clinic_nurse, store_keeper, phlebotomist, hr_employee |
| Evening | `evening` | `16:00` | `22:00` | clinic_doctor, clinic_nurse, clinic_cashier, technician |

### Departments on MAIN (create all)

| Department | Roles to attach |
|------------|-----------------|
| Administration | organization_admin, clinic_admin, hr_admin, supply_admin, billing_admin |
| Front desk | clinic_receptionist, receptionist |
| OPD | clinic_doctor, clinic_pa, clinic_counsellor |
| Nursing | clinic_nurse, clinic_procedure_tech |
| Laboratory | testing_specialist, technician, technician_supervisor |
| Store | store_keeper, inventory_manager, request, supply_admin |
| Blood bank — Collection | counsellor, phlebotomist, coordinator |
| Blood bank — Issue | doctor, medical_director, quality_officer |
| HR | hr_manager, hr_payroll, hr_employee |
| Billing | billing_cashier, billing_supervisor, billing_accountant |

### Holidays (add at least these)

| Date (DD/MM/YYYY) | Name |
|-------------------|------|
| `26/01/2026` | Republic Day |
| `15/08/2026` | Independence Day |
| `02/10/2026` | Gandhi Jayanti |

### Employees to hire (HR) — then link Care doctors

| Employee name | Dept | Org role (login later) | Joining | Council / reg (doctors) | Status |
|---------------|------|------------------------|---------|-------------------------|--------|
| Dr Anita Mehta | OPD | clinic_doctor | `01/11/2026` | MMC · `2020/12345` | **Active** |
| Dr Rohan Kulkarni | Blood bank — Issue | doctor | `01/11/2026` | MMC · `2018/67890` | **Active** |
| Nurse Kavita Patil | Nursing | clinic_nurse | `01/11/2026` | — | Active |
| Front desk Sneha Joshi | Front desk | clinic_receptionist | `01/11/2026` | — | Active |
| Store Ramesh Yadav | Store | store_keeper | `01/11/2026` | — | Active |
| Lab Tech Imran Sheikh | Laboratory | testing_specialist | `01/11/2026` | — | Active |
| Phlebo Deepa Nair | Blood bank — Collection | phlebotomist | `01/11/2026` | — | Active |
| Counsellor Meera Iyer | Blood bank — Collection | counsellor | `01/11/2026` | — | Active |
| Cashier Amit Desai | Billing | clinic_cashier | `01/11/2026` | — | Active |
| HR Exec Neha Gupta | HR | hr_manager | `01/11/2026` | — | Active |

Salary for QA: basic `25000`, HRA `5000` (or leave components blank if payroll not in scope).

### Care clinic masters

| Field | Value |
|-------|--------|
| Clinic display name | `QA Demo Multispecialty Hospital` |
| Phone / email / address | same as org |
| Registration / licence | `MH/CLINIC/QA/2026/001` |
| Languages | English, Hindi, Marathi |
| Specialties / seed | **General OPD** (+ Dermatology if you want a second) |
| Doctor 1 | Dr Anita Mehta → link HR employee · New consult **₹500** · Follow-up **₹300** |
| Doctor 2 (optional) | Dr Rohan Kulkarni · New **₹600** · Follow-up **₹350** |
| Schedule (Anita) | Mon–Sat · `09:00`–`13:00` · slot **15** min · max **16** · Room `OPD-1` |
| Fee items | `New consultation` ₹500 · `Follow-up` ₹300 · `Dressing` ₹200 · `Injection` ₹150 |

### Individuals / patients (create in `/people`)

| Name | Sex | DOB (DD/MM/YYYY) | Phone | Blood group | Notes |
|------|-----|------------------|-------|-------------|-------|
| Sunita Rao | Female | `15/03/1988` | `9876511001` | B+ | OPD + billing path |
| Vikram Shah | Male | `22/07/1995` | `9876511002` | O+ | Second appointment |
| Patient app user | — | — | `9876511003` | A+ | PatientSetu book path |

### Supply masters

**Locations**

| Name | Parent | Purpose |
|------|--------|---------|
| Main store | — | Primary stock |
| OT store | Main store | Theatre consumables |
| Nursing station | Main store | Ward issues |
| Blood bank fridge room | Main store | BB consumables / cold |

**Catalog (week-one items)**

| Name | Category | Unit | Location | Min / reorder |
|------|----------|------|----------|---------------|
| Sterile gloves M | Consumable | box | Main store | 5 / 10 |
| Disposable syringe 5ml | Consumable | pcs | Main store | 50 / 100 |
| IV set | Consumable | pcs | Nursing station | 20 / 40 |
| Blood bag CPD 350ml | Consumable | pcs | Blood bank fridge room | 10 / 25 |
| HBsAg ELISA kit | Reagent | kit | Blood bank fridge room | 1 / 2 |
| Paracetamol 500mg | Medicine | strip | Main store | 20 / 40 |

**Opening stock (add after catalog)**

| Item | Qty | Location | Batch | Expiry (DD/MM/YYYY) |
|------|-----|----------|-------|---------------------|
| Sterile gloves M | 20 boxes | Main store | `GLV-QA-01` | `31/12/2027` |
| Disposable syringe 5ml | 200 | Main store | `SYR-QA-01` | `30/06/2027` |
| Blood bag CPD 350ml | 50 | Blood bank fridge room | `BAG-QA-01` | `31/03/2027` |

**Vendor document checklist**

- [ ] GST certificate  
- [ ] Drug licence  
- [ ] PAN  
- [ ] Cancelled cheque  

**Vendors**

| Name | Supplies | GSTIN (fake OK for QA) | Phone | Contact |
|------|----------|------------------------|-------|---------|
| MedSupply India Pvt Ltd | Consumables, syringes, gloves | `27AABCU9603R1ZM` | `9876522001` | Sales desk |
| BioKit Diagnostics | ELISA / reagents | `27AABCU9603R1ZN` | `9876522002` | Mr Patel |
| PharmaCare Distributors | Medicines | `27AABCU9603R1ZO` | `9876522003` | Ms Khan |

**First PO**

| Field | Value |
|-------|--------|
| Vendor | MedSupply India Pvt Ltd |
| Lines | Sterile gloves M × 10 boxes · Syringe 5ml × 100 |
| Deliver to | Main store |
| Status to reach | Draft → Submit/Approve → Receive *(as far as roles allow)* |

**Asset (optional)**

| Name | Location | Notes |
|------|----------|-------|
| Centrifuge Lab-1 | Laboratory / BB fridge room | Needs daily QC if templates exist |

### Rakht masters

**Institutions**

| Name | City | Contact | Phone | Own doctors? |
|------|------|---------|-------|--------------|
| City Care Nursing Home | Mumbai | Dr Joshi | `9876533001` | Yes |
| Horizon Surgical Hospital | Thane | Ms Banerjee | `9876533002` | No |

**Equipment**

| Name | Where | Use | Daily QC? |
|------|-------|-----|-----------|
| Tube sealer TS-1 | Collection | Sealing | No |
| Blood bank fridge BF-1 | Fridge room | Storage 2–6°C | Yes |
| ELISA reader ER-1 | Lab | TTI | Yes |
| Centrifuge CF-1 | Lab | Separation | Yes |

**Donor (happy path)**

| Field | Value |
|-------|--------|
| Name | `Arjun Verma` |
| Sex | Male |
| DOB | `10/05/1992` |
| Phone | `9876544001` |
| Blood group | `O+` |
| Weight | `72` kg |
| Address | `Andheri East, Mumbai` |
| Donation type | Whole blood |
| Camp (optional) | `QA Walk-in Drive 2026` · date today · venue `Main Campus lobby` |

### Billing / Patient

| Item | Example |
|------|---------|
| Clinic charge | New consultation ₹500 for Sunita Rao |
| Billing package (if used) | `OPD Basic` = consult + dressing |
| Patient app login phone | `9876511003` |

---

## 0. Pre-flight

- [ ] Core UI + Core API on **5174**
- [ ] Module UIs running for embed (Care, Supply, Rakht, HR, Billing)
- [ ] Module APIs up for enabled packs
- [ ] Platform admin can sign in at `http://localhost:5174/`
- [ ] SMTP / WhatsApp / UPI ready **or** mark N/A in Phase 1.5
- [ ] Password sheet: all users `QaTest@2026`

**Enable on create:** CARE · SUPPLY · BLOOD_BANK · HR · BILLING · PATIENT

---

## Phase 1 — Platform admin: create organisation

**As:** Platform admin · `http://localhost:5174/organizations`

### 1.1 Create org

- [ ] Create org with **Fixed QA seed → Organisation** table (name, code, address, modules)
- [ ] Lands on `/organizations/:id` with success banner
- [ ] Record org id: _______________ · code: `qa20261122` (or yours)

### 1.2 Provision until READY

- [ ] Provisioning → wait for **READY**
- [ ] Apply DB / schema updates if pending → still READY
- [ ] Seed configuration → select **General OPD** (and Dermatology if testing second specialty)
- [ ] COMMS present for tenant

### 1.3 Import roles

- [ ] Roles → **Import recommended roles**
- [ ] Confirm Care / Supply / Rakht / HR / Billing roles from Phase 2 appear
- [ ] Optional: disable `trustee`, `joint_secretary`, Swastha roles if unused

### 1.4 First org admin

| Field | Value |
|-------|--------|
| Name | `Priya Shah` |
| Email | `qa.organization_admin@qa20261122.test` |
| Role | `organization_admin` |
| Password | `QaTest@2026` |

- [ ] User created / invited
- [ ] Can sign in at `http://qa20261122.localhost:5174/`

### 1.5 Configuration tabs

| Tab | Enter |
|-----|--------|
| Branding | App name `QA Demo Hospital`, support `support@qa20261122.test`, logo optional |
| Email | SMTP → test to your inbox |
| Payment QR | UPI `qademo@upi`, payee `QA Demo Multispecialty Hospital`, fee `500` |
| Communications | WhatsApp sandbox → send test *(or N/A)* |
| Barcodes | defer to tenant Settings if empty |
| ID cards | defer to tenant Settings if empty |
| Customize | leave defaults unless contract differs |

### 1.6 Handoff gate

- [ ] Org admin sees subscribed modules only
- [ ] `/settings/overview` loads

---

## Phase 2 — Roles catalog

Confirm these slugs exist after import (enabled modules only).

### Cross-product

- [ ] `admin` · [ ] `organization_admin`

### Care

- [ ] `clinic_admin` · [ ] `clinic_receptionist` · [ ] `clinic_doctor` · [ ] `clinic_nurse`  
- [ ] `clinic_pa` · [ ] `clinic_procedure_tech` · [ ] `clinic_counsellor` · [ ] `clinic_cashier`

### Supply

- [ ] `supply_admin` · [ ] `store_keeper` · [ ] `inventory_manager` · [ ] `request`  
- [ ] `collection` · [ ] `supplies` · [ ] `inventory_supervisor` · [ ] `supplies_manager`

### Rakht

- [ ] `medical_director` · [ ] `counsellor` · [ ] `phlebotomist` · [ ] `testing_specialist`  
- [ ] `technician` · [ ] `technician_supervisor` · [ ] `quality_officer` · [ ] `doctor`  
- [ ] `receptionist` · [ ] `coordinator` · [ ] `staff` · [ ] `trustee` · [ ] `joint_secretary`

### HR / Billing

- [ ] `hr_admin` · [ ] `hr_manager` · [ ] `hr_payroll` · [ ] `hr_employee`  
- [ ] `billing_admin` · [ ] `billing_cashier` · [ ] `billing_supervisor` · [ ] `billing_accountant`

### Custom role (optional)

- [ ] Create role `qa_readonly_store` with **view inventory only**
- [ ] Assign `qa.readonly@qa20261122.test` → confirm cannot create PO

---

## Phase 3 — Create every persona login

**As:** org admin · `/system/organization?admin=users`  
Password for all: `QaTest@2026`

| # | Role | Name | Email | Created | Sign-in OK |
|---|------|------|-------|---------|------------|
| 1 | organization_admin | Priya Shah | `qa.organization_admin@qa20261122.test` | [ ] | [ ] |
| 2 | clinic_admin | Clinic Admin | `qa.clinic_admin@qa20261122.test` | [ ] | [ ] |
| 3 | clinic_receptionist | Sneha Joshi | `qa.clinic_receptionist@qa20261122.test` | [ ] | [ ] |
| 4 | clinic_doctor | Dr Anita Mehta | `qa.clinic_doctor@qa20261122.test` | [ ] | [ ] |
| 5 | clinic_nurse | Kavita Patil | `qa.clinic_nurse@qa20261122.test` | [ ] | [ ] |
| 6 | clinic_pa | PA User | `qa.clinic_pa@qa20261122.test` | [ ] | [ ] |
| 7 | clinic_procedure_tech | Proc Tech | `qa.clinic_procedure_tech@qa20261122.test` | [ ] | [ ] |
| 8 | clinic_counsellor | Clinic Counsellor | `qa.clinic_counsellor@qa20261122.test` | [ ] | [ ] |
| 9 | clinic_cashier | Amit Desai | `qa.clinic_cashier@qa20261122.test` | [ ] | [ ] |
| 10 | supply_admin | Supply Admin | `qa.supply_admin@qa20261122.test` | [ ] | [ ] |
| 11 | store_keeper | Ramesh Yadav | `qa.store_keeper@qa20261122.test` | [ ] | [ ] |
| 12 | inventory_manager | Inv Manager | `qa.inventory_manager@qa20261122.test` | [ ] | [ ] |
| 13 | request | Request User | `qa.request@qa20261122.test` | [ ] | [ ] |
| 14 | medical_director | Med Director | `qa.medical_director@qa20261122.test` | [ ] | [ ] |
| 15 | counsellor | Meera Iyer | `qa.counsellor@qa20261122.test` | [ ] | [ ] |
| 16 | phlebotomist | Deepa Nair | `qa.phlebotomist@qa20261122.test` | [ ] | [ ] |
| 17 | testing_specialist | Imran Sheikh | `qa.testing_specialist@qa20261122.test` | [ ] | [ ] |
| 18 | technician | Lab Tech | `qa.technician@qa20261122.test` | [ ] | [ ] |
| 19 | quality_officer | QC Officer | `qa.quality_officer@qa20261122.test` | [ ] | [ ] |
| 20 | receptionist | BB Reception | `qa.bb_receptionist@qa20261122.test` | [ ] | [ ] |
| 21 | hr_admin | HR Admin | `qa.hr_admin@qa20261122.test` | [ ] | [ ] |
| 22 | hr_manager | Neha Gupta | `qa.hr_manager@qa20261122.test` | [ ] | [ ] |
| 23 | hr_payroll | Payroll User | `qa.hr_payroll@qa20261122.test` | [ ] | [ ] |
| 24 | hr_employee | Self Service | `qa.hr_employee@qa20261122.test` | [ ] | [ ] |
| 25 | billing_admin | Billing Admin | `qa.billing_admin@qa20261122.test` | [ ] | [ ] |
| 26 | billing_cashier | Bill Cashier | `qa.billing_cashier@qa20261122.test` | [ ] | [ ] |
| 27 | billing_supervisor | Bill Supervisor | `qa.billing_supervisor@qa20261122.test` | [ ] | [ ] |
| 28 | billing_accountant | Accountant | `qa.billing_accountant@qa20261122.test` | [ ] | [ ] |

Per user: Home loads · sidebar matches role · sign out OK.

---

## Phase 4 — Tenant Settings / get ready

**As:** `qa.organization_admin@…` · `/settings/overview`

- [ ] Overview shows tasks + readiness cards
- [ ] Recommended setup: accept defaults for MAIN campus
- [ ] Workplaces: create **MAIN** from seed table
- [ ] Departments: create all 10 departments with roles attached
- [ ] People & access: invite / link the Phase 3 users as needed
- [ ] Barcodes: create template `QA Blood Bag Label` → map collection/unit fields → sample print
- [ ] ID cards: version `QA Staff Badge 2026`
- [ ] Activate Care / Supply / Blood / HR / Billing / Comms when cards say ready

---

## Phase 5 — Module masters (enter seed data)

Order: **HR → Supply → Care → Rakht → Billing → Patient**.

### 5.1 HR (`hr_admin`)

- [ ] MAIN + Morning/Evening shifts
- [ ] All departments from seed
- [ ] Holidays 26/01, 15/08, 02/10/2026
- [ ] Hire all employees in seed table → status **Active**
- [ ] Dr Anita Mehta has MMC `2020/12345`
- [ ] `/employees` shows at least 10 active staff

### 5.2 Supply (`supply_admin`)

- [ ] Locations: Main store, OT store, Nursing station, Blood bank fridge room
- [ ] Catalog: all 6 seed items
- [ ] Opening stock rows (gloves 20, syringes 200, bags 50)
- [ ] Vendor checklist: GST, drug licence, PAN, cancelled cheque
- [ ] Vendors: MedSupply, BioKit, PharmaCare
- [ ] Draft PO to MedSupply (gloves 10 + syringes 100)

### 5.3 Care (`clinic_admin`)

- [ ] Clinic settings = seed letterhead + licence `MH/CLINIC/QA/2026/001`
- [ ] Doctors: Anita Mehta linked to HR · schedule Mon–Sat 09:00–13:00
- [ ] Fee items: New ₹500, Follow-up ₹300, Dressing ₹200, Injection ₹150
- [ ] `/people`: create **Sunita Rao** and **Vikram Shah**
- [ ] Open chart `/clinic/patients/person/:id` for Sunita

### 5.4 Rakht (`medical_director`)

- [ ] Institutions: City Care Nursing Home, Horizon Surgical Hospital
- [ ] Equipment: TS-1, BF-1, ER-1, CF-1
- [ ] Donor questionnaire / workflows approved (default OK)
- [ ] Label template print smoke OK
- [ ] Confirm Supply has blood bags in fridge room (do not create supply catalog in Rakht)

### 5.5 Billing (`billing_admin`) — if BILLING on

- [ ] Charge / package `OPD Basic` = consult + dressing
- [ ] Cashier can open `/billing`

### 5.6 Patient (`clinic_admin`) — if PATIENT on

- [ ] Portal settings pane OK
- [ ] `/clinic/portal-requests` loads
- [ ] Patient app `http://qa20261122.localhost:5181/` loads

---

## Phase 6 — Happy paths (use seed people)

### 6.1 Care — Sunita Rao visit

**As receptionist → doctor → nurse → cashier**

- [ ] `/people` → Sunita Rao exists (or create from seed)
- [ ] Book appointment: **Dr Anita Mehta**, today, next free slot, reason `Fever`
- [ ] Doctor: OPD → note `Viral fever` · Rx `Paracetamol 500mg TDS × 3 days` · save
- [ ] Nurse: vitals Temp `38.2`, BP `120/80`, Pulse `88`
- [ ] Cashier: bill **New consultation ₹500** (+ Dressing ₹200 if charged) · mark paid
- [ ] Optional: WhatsApp with consent on Sunita’s phone
- [ ] Second book: Vikram Shah follow-up path

### 6.2 Supply — gloves / PO

**As store_keeper → request → inventory_manager**

- [ ] Confirm Main store stock: gloves ≥ 20 boxes
- [ ] Request user: request **Sterile gloves M × 2 boxes** to Nursing station
- [ ] Manager: approve
- [ ] Store: issue / move to Nursing station
- [ ] PO: MedSupply gloves 10 + syringes 100 → receive into Main store
- [ ] Asset Centrifuge Lab-1 created *(optional)*
- [ ] Daily QC on BF-1 or centrifuge if template exists

### 6.3 Rakht — Arjun Verma donation → issue

**As counsellor → phlebotomist → testing → technician → issue**

- [ ] Register donor **Arjun Verma** (O+, 72 kg, phone `9876544001`)
- [ ] Counselling: fit to donate
- [ ] Collection: whole blood, bag from stock if linked
- [ ] Testing: ABO/Rh O+ · TTI all non-reactive (HIV, HBsAg, HCV, Syphilis, Malaria)
- [ ] Separation / processing complete
- [ ] Component QC pass
- [ ] Request from **City Care Nursing Home** for O+ PRBC × 1
- [ ] Crossmatch compatible → issue
- [ ] Optional camp `QA Walk-in Drive 2026` + one registration
- [ ] Print bag / component label

### 6.4 HR

**As hr_admin / hr_manager / hr_employee / hr_payroll**

- [ ] Hire one more: `Temp Staff QA` · Front desk · joining today · Active
- [ ] Assign Morning shift to Nurse Kavita for today
- [ ] Mark attendance Present for Kavita
- [ ] Leave: Kavita applies Casual Leave tomorrow → Neha Gupta approves
- [ ] `qa.hr_employee@…` self-service: My day / leave visible
- [ ] Payroll role opens salary / statutory without error

### 6.5 Billing module *(if on)*

- [ ] Cashier posts OPD Basic for Sunita Rao
- [ ] Supervisor approves if required
- [ ] Credit note ₹100 test → day close → reports open

### 6.6 Patient app *(if on)*

- [ ] Patient registers / signs in with phone `9876511003`
- [ ] Books visit with Dr Anita Mehta
- [ ] Staff sees row in `/clinic/portal-requests` and acts
- [ ] Patient sees updated status

### 6.7 Cross-module

- [ ] Blood centre: Imran (lab) login → Arjun donation uses bag from Supply location
- [ ] Clinic: Anita appears in doctor picker because HR Active + MMC number
- [ ] All paths done from portal **5174** only

---

## Phase 7 — Role-by-role smoke

Sign in as each email from Phase 3. Confirm **can** / **must not**.

| Role | Must can | Must not |
|------|----------|----------|
| organization_admin | Settings, Users, all modules | — |
| clinic_admin | `/clinic/settings`, doctors, fees | Create Supply vendor *(unless granted)* |
| clinic_receptionist | `/people`, book Anita | Edit fee masters |
| clinic_doctor | OPD + Rx for Sunita | Import roles |
| clinic_nurse | Vitals | Delete organisation user |
| clinic_cashier | Collect ₹500 consult | Edit doctor schedule |
| supply_admin | Catalog, vendors, PO | Approve BB medical policy |
| store_keeper | Stock in/out gloves | Org branding |
| request | Raise gloves request | Approve own request if policy forbids |
| inventory_manager | Approve request | Care Rx |
| medical_director | BB config / policies | Payroll edit |
| counsellor | Counselling Arjun | Day close billing |
| phlebotomist | Collection | Fee item edit |
| testing_specialist | Testing TTI | Hire HR employee |
| technician | Separation | Customize functionality |
| quality_officer | QC / compliance | SMTP secrets |
| hr_admin | Workplaces, hire | Issue blood |
| hr_manager | Leave approve | Supply PO |
| hr_payroll | Salary screens | Donor register |
| hr_employee | Self-service only | `/settings` admin |
| billing_* | Matching billing screens | Unrelated module admin |

Tick each role after 2-minute smoke: [ ] all Care · [ ] all Supply · [ ] all Rakht · [ ] all HR · [ ] all Billing

---

## Phase 8 — Safety / UI gates

- [ ] Lists: title + count left; Refresh/Add on same row
- [ ] Delete user / discard unit / day close → ConfirmDialog (not `window.confirm`)
- [ ] Errors in FormBanner
- [ ] Dates **DD/MM/YYYY** (e.g. Sunita DOB `15/03/1988`)
- [ ] Individuals only via `/people`
- [ ] Embed stays on 5174 (no jump to 5179)

Dangerous:

- [ ] Disable `qa.request@…` → cannot sign in
- [ ] Merge duplicate person only with confirm *(if testing)*
- [ ] Day close blocks further posts per policy

---

## Phase 9 — Sign-off

| Area | Tester | Date | Pass? | Notes |
|------|--------|------|-------|-------|
| Seed org `qa20261122` READY | | | [ ] | |
| Roles + 28 users | | | [ ] | |
| Settings MAIN ready | | | [ ] | |
| Masters (HR/Supply/Care/Rakht) | | | [ ] | |
| Care: Sunita ₹500 visit | | | [ ] | |
| Supply: gloves + PO | | | [ ] | |
| Rakht: Arjun → issue City Care | | | [ ] | |
| HR attendance/leave | | | [ ] | |
| Billing / Patient *(if on)* | | | [ ] | |
| Role matrix | | | [ ] | |
| Safety gates | | | [ ] | |

**Org code:** `qa20261122` (or __________)  
**Overall:** Pass / Fail / Pass with issues  

---

## Quick URL cheat sheet

| What | URL |
|------|-----|
| Platform | `http://localhost:5174/organizations` |
| Tenant | `http://qa20261122.localhost:5174/` |
| Settings | `.../settings/overview` |
| Users | `.../system/organization?admin=users` |
| People | `.../people` |
| Appointments | `.../clinic/appointments` |
| Inventory | `.../inventory` |
| POs | `.../inventory/purchase-orders` |
| Donors | `.../donors` |
| Employees | `.../employees` |
| Billing | `.../billing` |
| Patient app | `http://qa20261122.localhost:5181/` |

---

## Related help pages

- <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>
- <a href="#" data-hs-route="getting-started/before-you-start">Before you start (paper & Excel)</a>
- <a href="#" data-hs-route="getting-started/prep/hrsetu">Prep — HRSetu</a>
- <a href="#" data-hs-route="getting-started/prep/caresetu">Prep — CareSetu</a>
- <a href="#" data-hs-route="getting-started/prep/supplysetu">Prep — SupplySetu</a>
- <a href="#" data-hs-route="getting-started/prep/rakhtsetu">Prep — RakhtSetu</a>
- <a href="#" data-hs-route="getting-started/by-role">Guides by role</a>
- <a href="#" data-hs-route="core/users-roles">Users & roles</a>
