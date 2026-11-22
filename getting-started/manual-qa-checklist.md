# Full manual QA checklist

Walk this **in order**. Each section starts with **who to log in as**, then the exact steps for that user. Sign out before the next login.

**Learning one role only?** Open <a href="#" data-hs-route="getting-started/by-role">Hands-on by role</a> and click your job (e.g. Doctor) for a practise path. Use this full checklist when you are validating a whole new organisation.

For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>.

<div class="callout callout--tip">
  <strong>Where to log in (Azure)</strong><br/>
  Platform admin: <code>https://admin.healthsetu.com/</code><br/>
  Staff (every role below): <code>https://qaYYYYMMDD.healthsetu.com/</code><br/>
  Patient app: <code>https://qaYYYYMMDD.patient.healthsetu.co.in/</code><br/>
  Use only the Azure hosts above for this QA round.<br/><strong>How to navigate:</strong> use the <em>left menu</em> and on-screen buttons (Add, Edit, Save, Refresh, Approve). Do not type web paths.
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
- [ ] Platform left menu → **Users** — list opens · click **Add** / **New** — form loads

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
- [ ] Left menu shows Care, Supply, Rakht, HR, Billing sections
- [ ] Left menu → **Inbox** → click **Refresh**
- [ ] Profile / account menu → **Preferences** → change one setting → **Save**
- [ ] Left menu → **Insight** → open **Reports** and **Clicks**

### Setup / Settings — open every page and Save/Continue where shown

Left menu → **Setup** (or **Settings**). Work through the left settings rail:

- [ ] **Setup overview** · **Get ready** · **Recommended setup** · **Smart setup** · **All settings**
- [ ] **Organization details** — confirm Ahmedabad / Gujarat / 380054 → **Save** if you change anything
- [ ] **Workplaces** — click **Add** → code **MAIN** / Main Campus · Morning + Evening shifts → **Save**
- [ ] **Departments & job titles** — add Administration, Front Desk, Clinical, Laboratory, Counseling, Stores, Medical Office → **Save**
- [ ] **People & access** · **Invite** — open each once
- [ ] **Documents & branding** · **Access profiles** · **Approvals**
- [ ] **Integrations** · **Data import** · **Audit history** · **Template updates** · impact / diagnostics if shown
- [ ] Under services → **Patient care** and its sub-pages (doctors, appointments, clinical, portal)
- [ ] **Billing** service settings (charges, invoices, payments)
- [ ] **Inventory** service settings (catalog, vendors, assets)
- [ ] **Blood bank** service settings (facility, policies, components, storage)
- [ ] **HR** service settings (employment, leave, docs, time, shifts, holidays, check-in, payroll, training)
- [ ] **Communications** service settings (auto, channels, WhatsApp, templates, prefs)
- [ ] Open **Diagnostics** if shown

### Create every QA login user

Left menu → **Administration** (or **Organization**) → **Users** → click **Add** for each login on the sheet (password `QaTest@2026`).

- [ ] All users from the login sheet created
- [ ] Same area → **Barcodes** → open a template → **Mapping** → tick fields → **Save** → open **Designer**
- [ ] **ID cards** → open a version → designer · print a sample for a later employee

### Redirect sanity (stay logged in as admin)

- [ ] Opening **Setup** lands on **Setup overview**
- [ ] Opening **Patients** (if still labelled that way) lands on **Individuals**
- [ ] Opening **Account** lands on preferences

### Sign out

- [ ] Sign out of `qa.admin@…`

---

## Step C — Now log in as **QA HR Admin**

**User:** `qa.hradmin@qaYYYYMMDD.test`  
**Role:** `hr_admin`

- [ ] Home loads · HR items visible · Care clinical write not available (or read-only)
- [ ] Left menu → **HR dashboard** · **HR reports** — both open
- [ ] Left menu → **Workplaces** → open MAIN · holidays `26/01` Republic Day → **Save**
- [ ] **Departments** (or workplace depts) → roles attached per seed pack
- [ ] **Shifts** → Morning + Evening
- [ ] Left menu → **Employees** → click **Hire** for each:
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
- [ ] Click **Dr Anita Shah** name (or pencil **Edit**) to open detail
- [ ] Open **Onboarding**, **Training**, **BGV**, **Salary**, **Statutory**, **Full and Final** once each
- [ ] Left menu → **Attendance** — mark Temp Staff One present today → **Save**
- [ ] Left menu → **Leave** — list opens
- [ ] Open **Employee setup**, **Document library**, **Employee files**, **Work clearances**, **Holidays**
- [ ] Assign Morning shift to Temp Staff One → **Save**
- [ ] Sign out

---

## Step D — Now log in as **QA HR Manager**

**User:** `qa.hrmgr@qaYYYYMMDD.test`  
**Role:** `hr_manager`

- [ ] Left menu → **Employees** — list loads
- [ ] Left menu → **Leave** — open a leave for Temp Staff One (create one if needed: 1 day next week) → click **Approve**
- [ ] Cannot open org Customize / platform tabs
- [ ] Sign out

---

## Step E — Now log in as **QA Payroll**

**User:** `qa.payroll@qaYYYYMMDD.test`  
**Role:** `hr_payroll`

- [ ] Left menu → **Salary** · **Statutory** · **HR reports** — each opens
- [ ] Open a salary run if one exists (click the run name)
- [ ] Confirm **Hire** is not available
- [ ] Sign out

---

## Step F — Now log in as **QA Employee (self-service)**

**User:** `qa.employee@qaYYYYMMDD.test`  
**Role:** `hr_employee`

- [ ] Left menu → **My day** — loads
- [ ] Open **Check in**, **Leave**, **Salary slips**, **Documents**
- [ ] Open **Attendance**, **My shifts**, **Holidays**, **Clearances**, **Profile**
- [ ] No admin Settings / hire screens
- [ ] Sign out

---

## Step G — Now log in as **QA Supply Admin**

**User:** `qa.supply@qaYYYYMMDD.test`  
**Role:** `supply_admin`

- [ ] Left menu → **Inventory health** · **Supply reports** · **Tasks** · **Daily QC** — each opens
- [ ] **Set up SupplySetu** / locations — ensure Main store, OT store, Blood bank fridge room (click **Add** if missing) → **Save**
- [ ] Left menu → **Catalog** → **Add** Surgical gloves M, Disposable syringe 5ml, HBsAg ELISA kit 96T → **Save**
- [ ] Open gloves row → pencil **Edit** → **Save**
- [ ] Open **Custom fields**, **Parameters**, **Vendor checklist** (GST + Drug licence required)
- [ ] Left menu → **Vendors** → **Add** MedSupply Gujarat · GSTIN `24AAAAA0000A1Z5` → **Save**
- [ ] Left menu → **Stock** → **Add** — gloves **50** · lot `LOT-GLOVE-01` · expiry `31/12/2027` → Main store → **Save**
- [ ] Stock list shows gloves · pencil **Edit** a stock row
- [ ] Left menu → **Assets** → **Add** `BP Monitor QA-01` → **Save** · open detail · try **Import** wizard
- [ ] Open **Service contracts**, asset workflow mapping, reorder, receive, stock intake, **Inventory movement**
- [ ] Left menu → **Purchase orders** → **Add** — MedSupply · gloves ×20 @ ₹180 → **Save** draft · open detail
- [ ] **Quotations** → **Add** — form opens · list loads
- [ ] Vendor returns → **Add** · **Daily QC templates** · checklists → **Add**
- [ ] On Stock hub, click tabs: stock, checklists, QC, quotations, invoices, purchase orders
- [ ] Left menu → **Delete data (Supply)** — confirm dialog appears → **Cancel** (do not wipe)
- [ ] Sign out

---

## Step H — Now log in as **QA Store Keeper**

**User:** `qa.store@qaYYYYMMDD.test`  
**Role:** `store_keeper`

- [ ] Left menu → **Stock** — gloves visible · click **Refresh**
- [ ] Stock in/out or **Inventory movement** for gloves → **Save**
- [ ] Limited or no vendor master edit (per capabilities)
- [ ] Sign out

---

## Step I — Now log in as **QA Requester**

**User:** `qa.request@qaYYYYMMDD.test`  
**Role:** `request`

- [ ] Left menu → **Request inventory** → **Add** — request **5** boxes Surgical gloves M for OT store → **Submit**
- [ ] Cannot click **Approve** on your own request (if policy forbids)
- [ ] Sign out

---

## Step J — Now log in as **QA Inventory Manager**

**User:** `qa.invmgr@qaYYYYMMDD.test`  
**Role:** `inventory_manager`

- [ ] Left menu → **Approvals** — select the gloves request → **Approve**
- [ ] Confirm movement / issue path Main store → OT store
- [ ] Sign out

---

## Step K — Now log in as **QA Clinic Admin**

**User:** `qa.clinicadmin@qaYYYYMMDD.test`  
**Role:** `clinic_admin`

- [ ] Left menu → Care home / clinic dashboard · **Clinic settings** — name `QA Campus OPD` · reg `QA-CLINIC-001` → **Save**
- [ ] In Clinic settings, open each section/tab: portal, integrations, clinic, clinical, money, roles, people, audit, merge
- [ ] Left menu → **Doctors** — link **Dr Anita Shah** → **Save**
- [ ] Set schedules — Mon–Sat 09:00–13:00 · 15 min · OPD-1 → **Save**
- [ ] Left menu → **Fee items** — New consult ₹500 · Follow-up ₹300 · Dressing ₹200 · ECG ₹400 → **Save**
- [ ] Left menu → **Department templates** — open one pack
- [ ] Open **Procedures** → try **Start** / **Book** buttons (cancel if not running a real sitting)
- [ ] Open **Recommendations**, **Reports**, **Doctor desk**, **Nursing station**, **Lab**
- [ ] Open **Token display**, TV board, **Audit log**, **Merge duplicates** (do not merge yet)
- [ ] Open **Refills**, **Portal requests**, **Billing** *(note if hidden when BILLING module is on)*
- [ ] Left menu → **Individuals** → **Add** **Test Patient One** (F, 15/03/1990, 9876511111) → **Save** · pencil **Edit** · open chart
- [ ] Chart tabs: summary, labs, procedures, billing, documents, details
- [ ] Sign out

---

## Step L — Now log in as **QA Reception**

**User:** `qa.reception@qaYYYYMMDD.test`  
**Role:** `clinic_receptionist`

- [ ] Left menu → **Individuals** — find Test Patient One
- [ ] Left menu → **Appointments** → **Add** / **Book** — Test Patient One · Dr Anita Shah · today/tomorrow 09:00 → **Save**
- [ ] On Appointments, open the **Waitlist** view / tab
- [ ] Cannot edit fee masters / clinic settings
- [ ] Sign out

---

## Step M — Now log in as **QA Doctor**

**User:** `qa.doctor@qaYYYYMMDD.test`  
**Role:** `clinic_doctor`

- [ ] Left menu → **OPD** or **Doctor desk** — open Test Patient One visit
- [ ] Note: `URI — symptomatic care` · Rx: paracetamol 500 mg → **Save**
- [ ] Limited admin (no fee master edit)
- [ ] Sign out

---

## Step N — Now log in as **QA Nurse**

**User:** `qa.nurse@qaYYYYMMDD.test`  
**Role:** `clinic_nurse`

- [ ] Left menu → **Nursing station** — open same visit
- [ ] Vitals: BP `120/80` · pulse `78` · temp `98.6°F` → **Save**
- [ ] No fee master edit
- [ ] Sign out

---

## Step O — Now log in as **QA Clinic Cashier**

**User:** `qa.cashier@qaYYYYMMDD.test`  
**Role:** `clinic_cashier`

- [ ] Left menu → **Billing** (or **Cashier desk**) — charge New consultation ₹500 (+ Dressing ₹200 if done)
- [ ] Click **Mark paid** / **Collect** → **Cash**
- [ ] Cannot edit doctor schedules
- [ ] Sign out

---

## Step P — Now log in as **QA Medical Director**

**User:** `qa.meddir@qaYYYYMMDD.test`  
**Role:** `medical_director`

- [ ] Left menu → **RakhtSetu dashboard** · **QC dashboard** · **Audit and compliance** — each opens
- [ ] Open other dashboard views available (camps, donors, lab, inventory, requests) once each
- [ ] Left menu → **Institutions** → **Add** **City General Hospital** · Dr Patel · `9876533333` → **Save**
- [ ] Open partner blood banks if shown
- [ ] Left menu → **Equipment configuration** — `ELISA Reader 1` → **Save**
- [ ] Left menu → **Workflows** — open donor questionnaire · **Approve** if you are the approver
- [ ] Open a workflow detail by clicking the row
- [ ] Open lab ELISA dashboard if shown
- [ ] Print a sample blood label from **Barcodes** (Settings / Administration)
- [ ] Left menu → **Delete data (RakhtSetu)** — confirm dialog → **Cancel**
- [ ] Left menu → **Camps** → **Add** `QA Weekend Camp` · tomorrow · MAIN lawn → **Save** · open detail
- [ ] Open **Support** if shown
- [ ] Sign out

---

## Step Q — Now log in as **QA BB Reception**

**User:** `qa.bbreception@qaYYYYMMDD.test`  
**Role:** `receptionist` (blood)

- [ ] Left menu → **Donors** → **Add** — register **Donor Ramesh Kumar** (O+, 72 kg, 9876544444, DOB 10/05/1988) → **Save**
- [ ] Click the donor name to open detail
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

- [ ] Left menu → **Collections** or **Donor station** — complete collection for Ramesh → **Save** / **Complete**
- [ ] Sign out

---

## Step T — Now log in as **QA Testing**

**User:** `qa.testing@qaYYYYMMDD.test`  
**Role:** `testing_specialist`

- [ ] Left menu → **Testing** → open **Pending** · click a unit → **Enter results** / **Add results** · check Completed / TTI panel views
- [ ] Left menu → **Lab batch entry** opens
- [ ] Complete testing for the unit → **Save**
- [ ] Sign out

---

## Step U — Now log in as **QA Technician**

**User:** `qa.tech@qaYYYYMMDD.test`  
**Role:** `technician`

- [ ] Left menu → **Processing** · **Separation batch** · triple-bag workspace
- [ ] Open each blood inventory view once (pending separation, components, discarded, autoclave waste, …)
- [ ] Complete separation / processing for the unit → **Save**
- [ ] Sign out

---

## Step V — Now log in as **QA Quality Officer**

**User:** `qa.qo@qaYYYYMMDD.test`  
**Role:** `quality_officer`

- [ ] Left menu → **Component QC** — pass QC → **Save**
- [ ] Open **Approvals** (doctor components), **QC dashboard**, **Tasks**
- [ ] Open **Crossmatch** (redirects OK) · **Requests** → **Add** — City General · patient `CGH Bed 12` → **Save**
- [ ] Left menu → **New blood request** / issue workstation — complete issue path
- [ ] Open **Add bag** form if shown
- [ ] Print bag/component label
- [ ] Sign out

---

## Step W — Now log in as **QA Billing Admin**

**User:** `qa.billadmin@qaYYYYMMDD.test`  
**Role:** `billing_admin`  
*(Skip W–Z if BILLING not enabled)*

- [ ] Left menu → **Cashier desk** / Billing home · **Charge master** · **Packages** — create `OPD day package` ₹800 → **Save**
- [ ] Left menu → **Billing settings** → **Save**
- [ ] Open **Accounts** · **Billing reports**
- [ ] Sign out

---

## Step X — Now log in as **QA Billing Cashier**

**User:** `qa.billcash@qaYYYYMMDD.test`  
**Role:** `billing_cashier`

- [ ] Left menu → **Cashier desk** — charge Test Patient One · OPD day package ₹800 → **Collect** → Cash
- [ ] Open the bill (row click) if a composer opens
- [ ] Sign out

---

## Step Y — Now log in as **QA Billing Supervisor**

**User:** `qa.billsup@qaYYYYMMDD.test`  
**Role:** `billing_supervisor`

- [ ] Left menu → Billing **Approvals** · **Credit & refunds**
- [ ] Optional ₹100 credit-note path
- [ ] Left menu → **Day close** — run day close (or open and **Cancel** if not closing for real)
- [ ] Sign out

---

## Step Z — Now log in as **QA Billing Accountant**

**User:** `qa.billacct@qaYYYYMMDD.test`  
**Role:** `billing_accountant`

- [ ] Left menu → **Billing reports** · **Accounts** — open one account (row click)
- [ ] Sign out

---

## Step AA — Now use the **Patient app** (not staff portal)

**URL:** `https://qaYYYYMMDD.patient.healthsetu.co.in/`  
**User:** phone `9876511111` (Test Patient One)

- [ ] Sign in → Home
- [ ] Open **Visits** · **Book** — book tomorrow · Dr Anita Shah → confirm
- [ ] Open **Records**, **Medicines**, **Bills**, **Profile**
- [ ] Open **Notifications**, **Messages**, **More**
- [ ] Open **Privacy**, **Security**, **Account**, **ABHA**, **Services**, **Emergency**

### Then log in again as **QA Clinic Admin**

**User:** `qa.clinicadmin@qaYYYYMMDD.test`

- [ ] Left menu → **Portal requests** — see the booking · update status → **Save**
- [ ] Sign out

---

## Step AB — Optional: Swastha screens

Only if `SWASTHA` is enabled. Log in as org admin (or OHC admin) and open every left-menu OHC item once:

- [ ] **OHC dashboard** · **Employees** · **Pre-employment** · **PEM authorization** · **OPD register** · **Periodic medical** · **Audiometry** · health checkup · **Vaccination**
- [ ] **First aiders** · **Ambulances** · ambulance detail · **First aid box** · **Canteen hygiene** · **Plant inspection**
- [ ] **Collection agencies** · **Biomedical waste** · **Monthly OHC work** · yearly calendar · daily report
- [ ] Organization · departments · job titles · **Medical tests** · **Test requirements** · **SOPs & documents**

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

Open the emailed / SMS link (do not type a path):

- [ ] Vendor onboarding · Employee onboarding · Offer sign
- [ ] Vendor quotation · Vendor purchase order · PO confirmed
- [ ] Camp organizer approval · Camp feedback · Pre-employment sign · Public form

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
