# Full manual QA checklist

Walk this **in order**. Each section starts with **who to log in as**, then the exact steps for that user. Sign out before the next login.

**Learning one role only?** Open <a href="#" data-hs-route="getting-started/by-role">Hands-on by role</a> and click your job (e.g. Doctor) for a practise path. Use this full checklist when you are validating a whole new organisation.

For a shorter go-live list, see <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>.

<div class="callout callout--tip">
  <strong>Where to log in (Azure)</strong><br/>
  Platform admin: <code>https://admin.healthsetu.com/</code><br/>
  Staff (every role below): <code>https://qacampus.healthsetu.com/</code><br/>
  Patient app: <code>https://qacampus.patient.healthsetu.co.in/</code><br/>
  Use only the Azure hosts above for this QA round.<br/><strong>How to navigate:</strong> use the <em>left menu</em> and on-screen buttons (Add, Edit, Save, Refresh, Approve). Do not type web paths.
</div>

Tenant portal: `https://qacampus.healthsetu.com/` (or your training org host).  
**Password for every QA staff user:** `QaTest@2026`  
**Marking:** `[ ]` pending · `[x]` pass · `[!]` fail  

---

## Seed values (copy from here while typing)

| What | Value |
|------|-------|
| Org name / code | `QA HealthSetu Campus` / `qacampus` |
| Address | `12 SG Highway`, Ahmedabad, Gujarat, `380054` |
| Org phone / email | `9876500001` / `admin@qacampus.test` |
| Modules | CARE + SUPPLY + BLOOD_BANK + HR + BILLING + PATIENT |
| Brand | App `QA Campus` · support `support@qacampus.test` |
| UPI *(optional)* | `qacampus@upi` · payee `QA HealthSetu Campus` · fee `500` |
| Workplace | Code `MAIN` · name `Main Campus` · PT Gujarat · Mon–Sat |
| Shifts | `Morning` 08:00–16:00 · `Evening` 16:00–22:00 |
| Holiday | `26/01/2026` Republic Day |
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
| `qa.admin@qacampus.test` | organization_admin |
| `qa.hradmin@qacampus.test` | hr_admin |
| `qa.hrmgr@qacampus.test` | hr_manager |
| `qa.payroll@qacampus.test` | hr_payroll |
| `qa.employee@qacampus.test` | hr_employee |
| `qa.clinicadmin@qacampus.test` | clinic_admin |
| `qa.reception@qacampus.test` | clinic_receptionist |
| `qa.doctor@qacampus.test` | clinic_doctor |
| `qa.nurse@qacampus.test` | clinic_nurse |
| `qa.cashier@qacampus.test` | clinic_cashier |
| `qa.supply@qacampus.test` | supply_admin |
| `qa.store@qacampus.test` | store_keeper |
| `qa.invmgr@qacampus.test` | inventory_manager |
| `qa.request@qacampus.test` | request |
| `qa.meddir@qacampus.test` | medical_director |
| `qa.bbreception@qacampus.test` | receptionist |
| `qa.bbcounsellor@qacampus.test` | counsellor |
| `qa.phlebo@qacampus.test` | phlebotomist |
| `qa.testing@qacampus.test` | testing_specialist |
| `qa.tech@qacampus.test` | technician |
| `qa.qo@qacampus.test` | quality_officer |
| `qa.billadmin@qacampus.test` | billing_admin |
| `qa.billcash@qacampus.test` | billing_cashier |
| `qa.billsup@qacampus.test` | billing_supervisor |
| `qa.billacct@qacampus.test` | billing_accountant |

---

## Step 0 — Pre-flight (no login)

- [ ] Azure reachable: `https://admin.healthsetu.com/` sign-in works; tenant DNS for new org will be `https://qacampus.healthsetu.com/`
- [ ] Open help site home: https://mahavir-b.github.io/healthsetu_docs/ — sidebar loads
- [ ] Password ready: `QaTest@2026`

---

## Step A — Now log in as **Platform admin**

**URL:** `https://admin.healthsetu.com/`  
**User:** your platform admin account  

### Create the org

- [ ] Go to **Organizations** → Create
- [ ] Name `QA HealthSetu Campus` · code `qacampus` · address from seed pack
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

- [ ] Add user `qa.admin@qacampus.test` · role **organization_admin** · password `QaTest@2026`

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

**URL:** `https://qacampus.healthsetu.com/`  
**User:** `qa.admin@qacampus.test`  
**Role:** `organization_admin`  
**Password:** `QaTest@2026`

### Portal chrome

- [ ] **Home** loads · branding shows `QA Campus`
- [ ] **Home** opens · left-menu sections include **My Work**, **People**, **Appointments & Visits**, **Clinical Services**, **Billing**, **Resources & Inventory**, **Insights**, **Administration** (which ones appear depends on modules and your role)
- [ ] Left menu → **My Work** → **Inbox** — page opens with **Open** / **Done** tabs
- [ ] Left menu → **My Work** → **Preferences** → change one setting → **Save**
- [ ] Left menu → **Insights** → open **Reports library** and **Click analysis**

### Setup (under Administration)

Left menu → **Administration** → **Setup**. Then use the **settings left rail** (not the main portal menu).

#### Getting started
- [ ] **Setup overview**
- [ ] **Recommended setup**
- [ ] **Smart setup** (if shown)
- [ ] From Setup overview, open **Get ready** and **All settings** if those buttons are shown

#### Organization
- [ ] **Organization details** — confirm Ahmedabad / Gujarat / 380054 → **Save** if you change anything
- [ ] **Workplaces** — click **Add** → code **MAIN** / Main Campus · Morning + Evening shifts → **Save**
- [ ] **Departments & job titles** — add Administration, Front Desk, Clinical, Laboratory, Counseling, Stores, Medical Office → **Save**
- [ ] **People & access** — open once; use **Invite** / **Add people** if shown
- [ ] **Documents & branding** — open tabs **Letterhead & prints**, **Labels & barcodes**, **ID cards**

#### Services
- [ ] **Patient care** — Overview · **Doctors & specialties** · **Appointments & hours** · **Clinical templates** · **Patient portal**
- [ ] **Billing & payments** — Overview · **Charges & pricing** · **Invoices & taxes** · **Online payments**
- [ ] **Inventory & procurement** — Overview · **Catalog & stock locations** · **Vendors & approvals** · **Assets, QC & maintenance**
- [ ] **Blood bank** — Overview · **Facility & licence** · **Policies** · **Components** · **Storage equipment**
- [ ] **Human resources** — Overview · **Employment & leave** · **Time & attendance** · **Payroll** · **Training & credentials**
- [ ] **Communications** — Overview · **Automated messages** · **Channels** · **Message templates** · **Preferences**
- [ ] **Laboratory & diagnostics** — Overview (if shown)

#### Administration (inside Setup rail)
- [ ] **Access profiles** · **Approvals** · **Integrations** · **Data import** · **Audit history** · **Template updates**

### Create every QA login user

Left menu → **Administration** → **Users** → click **Add** for each login on the sheet (password `QaTest@2026`).

- [ ] All users from the login sheet created
- [ ] Left menu → **Administration** → **Setup** → **Documents & branding** → **Labels & barcodes** → open a template → **Mapping** → tick fields → **Save** → open **Designer**
- [ ] Same page → **ID cards** tab → open a version → designer · print a sample for a later employee

### Redirect sanity (stay logged in as admin)

- [ ] Opening **Administration** → **Setup** lands on **Setup overview**
- [ ] Left menu → **People** → **Individuals** opens the people list
- [ ] Left menu → **My Work** → **Preferences** opens preferences

### Sign out

- [ ] Sign out of `qa.admin@…`

---

## Step C — Now log in as **QA HR Admin**

**User:** `qa.hradmin@qacampus.test`  
**Role:** `hr_admin`

- [ ] Home loads · HR items visible · Care clinical write not available (or read-only)
- [ ] Left menu → **HR dashboard** · **HR reports** — both open
- [ ] Left menu → **Administration** → **Setup** → **Workplaces** → open MAIN · holidays `26/01` Republic Day → **Save**
- [ ] **Setup** → **Departments & job titles** (or workplace depts) → roles attached per seed pack
- [ ] Left menu → **People** → **Shift roster** → Morning + Evening
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

**User:** `qa.hrmgr@qacampus.test`  
**Role:** `hr_manager`

- [ ] Left menu → **Employees** — list loads
- [ ] Left menu → **Leave** — open a leave for Temp Staff One (create one if needed: 1 day next week) → click **Approve**
- [ ] Cannot open org Customize / platform tabs
- [ ] Sign out

---

## Step E — Now log in as **QA Payroll**

**User:** `qa.payroll@qacampus.test`  
**Role:** `hr_payroll`

- [ ] Left menu → **Salary** · **Statutory** · **HR reports** — each opens
- [ ] Open a salary run if one exists (click the run name)
- [ ] Confirm **Hire** is not available
- [ ] Sign out

---

## Step F — Now log in as **QA Employee (self-service)**

**User:** `qa.employee@qacampus.test`  
**Role:** `hr_employee`

- [ ] Left menu → **My day** — loads
- [ ] Open **Check in**, **Leave**, **Salary slips**, **Documents**
- [ ] Open **Attendance**, **My shifts**, **Holidays**, **Work clearances**
- [ ] Left menu → **My Work** → **Preferences** (no separate Profile menu)
- [ ] No admin Setup / hire screens
- [ ] Sign out

---

## Step G — Now log in as **QA Supply Admin**

**User:** `qa.supply@qacampus.test`  
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

**User:** `qa.store@qacampus.test`  
**Role:** `store_keeper`

- [ ] Left menu → **Stock** — gloves visible · click **Refresh**
- [ ] Stock in/out or **Inventory movement** for gloves → **Save**
- [ ] Limited or no vendor master edit (per capabilities)
- [ ] Sign out

---

## Step I — Now log in as **QA Requester**

**User:** `qa.request@qacampus.test`  
**Role:** `request`

- [ ] Left menu → **Request inventory** → **Add** — request **5** boxes Surgical gloves M for OT store → **Submit**
- [ ] Cannot click **Approve** on your own request (if policy forbids)
- [ ] Sign out

---

## Step J — Now log in as **QA Inventory Manager**

**User:** `qa.invmgr@qacampus.test`  
**Role:** `inventory_manager`

- [ ] Left menu → **Approvals** — select the gloves request → **Approve**
- [ ] Confirm movement / issue path Main store → OT store
- [ ] Sign out

---

## Step K — Now log in as **QA Clinic Admin**

**User:** `qa.clinicadmin@qacampus.test`  
**Role:** `clinic_admin`

- [ ] Left menu → **Insights** → **Clinic dashboard**
- [ ] Left menu → **Administration** → **Clinic settings** — name `QA Campus OPD` · reg `QA-CLINIC-001` → **Save**
- [ ] In Clinic settings, open each rail item: **Identity & letterhead**, **Locations & departments**, **Doctors & fees**, **Rooms, devices & staff**, **Schedules & leave**, **Department templates**, **Fee master (GST, SAC)**, **Billing & tax rules**, **Roles & permissions**, **Reminders & outbox**, **Patient portal**, **Integrations (SupplySetu, video)**, **Desktop sync inbox**, **Audit log**, **Data export & merge**
- [ ] Left menu → **People** → **Doctors** (or **Administration** → **Doctor schedules**) — link **Dr Anita Shah** → **Save**
- [ ] Set schedules — Mon–Sat 09:00–13:00 · 15 min · OPD-1 → **Save**
- [ ] Left menu → **Administration** → **Fee items** — New consult ₹500 · Follow-up ₹300 · Dressing ₹200 · ECG ₹400 → **Save**
- [ ] Left menu → **Administration** → **Department templates** — open one pack
- [ ] Left menu → **Clinical Services** → **Procedures** → try **Start** / **Book** (cancel if not running a real sitting)
- [ ] Open **Recommendations**, **Reports**, **Doctor desk**, **Nursing station**, **Lab & results**
- [ ] Open **Token display**, **Audit log**, **Merge duplicates** (do not merge yet)
- [ ] Open **Refills**, **Portal requests**, **Cashier desk** / Care **Billing** *(note if hidden when BILLING module is on)*
- [ ] Left menu → **People** → **Individuals** → **Add** **Test Patient One** (F, 15/03/1990, 9876511111) → **Save** · pencil **Edit** · **Open chart**
- [ ] Chart tabs: Summary, Labs, Procedures, Billing, Documents, Details
- [ ] Sign out

---

## Step L — Now log in as **QA Reception**

**User:** `qa.reception@qacampus.test`  
**Role:** `clinic_receptionist`

- [ ] Left menu → **People** → **Individuals** — find Test Patient One
- [ ] Left menu → **Appointments & Visits** → **Appointments** → **Add** / **Book** — Test Patient One · Dr Anita Shah · today/tomorrow 09:00 → **Save**
- [ ] Left menu → **Appointments & Visits** → **Waitlist** (or Waitlist view on Appointments)
- [ ] Cannot edit **Fee items** / **Clinic settings**
- [ ] Sign out

---

## Step M — Now log in as **QA Doctor**

**User:** `qa.doctor@qacampus.test`  
**Role:** `clinic_doctor`

- [ ] Left menu → **OPD** or **Doctor desk** — open Test Patient One visit
- [ ] Note: `URI — symptomatic care` · Rx: paracetamol 500 mg → **Save**
- [ ] Limited admin (no fee master edit)
- [ ] Sign out

---

## Step N — Now log in as **QA Nurse**

**User:** `qa.nurse@qacampus.test`  
**Role:** `clinic_nurse`

- [ ] Left menu → **Nursing station** — open same visit
- [ ] Vitals: BP `120/80` · pulse `78` · temp `98.6°F` → **Save**
- [ ] No fee master edit
- [ ] Sign out

---

## Step O — Now log in as **QA Clinic Cashier**

**User:** `qa.cashier@qacampus.test`  
**Role:** `clinic_cashier`

- [ ] Left menu → **Cashier desk** (or Care **Billing** if shown) — charge New consultation ₹500 (+ Dressing ₹200 if done)
- [ ] Click **Mark paid** / **Collect** → **Cash**
- [ ] Cannot edit doctor schedules
- [ ] Sign out

---

## Step P — Now log in as **QA Medical Director**

**User:** `qa.meddir@qacampus.test`  
**Role:** `medical_director`

- [ ] Left menu → **RakhtSetu dashboard** · **QC dashboard** · **Audit and compliance** — each opens
- [ ] Open other dashboard views available (camps, donors, lab, inventory, requests) once each
- [ ] Left menu → **Institutions** → **Add** **City General Hospital** · Dr Patel · `9876533333` → **Save**
- [ ] Open partner blood banks if shown
- [ ] Left menu → **Equipment configuration** — `ELISA Reader 1` → **Save**
- [ ] Left menu → **Workflows** — open donor questionnaire · **Approve** if you are the approver
- [ ] Open a workflow detail by clicking the row
- [ ] Open lab ELISA dashboard if shown
- [ ] **Administration** → **Setup** → **Documents & branding** → **Labels & barcodes** — print a sample blood label
- [ ] Left menu → **Delete data (RakhtSetu)** — confirm dialog → **Cancel**
- [ ] Left menu → **Camps** → **Add** `QA Weekend Camp` · tomorrow · MAIN lawn → **Save** · open detail
- [ ] Open **Support** if shown
- [ ] Sign out

---

## Step Q — Now log in as **QA BB Reception**

**User:** `qa.bbreception@qacampus.test`  
**Role:** `receptionist` (blood)

- [ ] Left menu → **Donors** → **Add** — register **Donor Ramesh Kumar** (O+, 72 kg, 9876544444, DOB 10/05/1988) → **Save**
- [ ] Click the donor name to open detail
- [ ] Sign out

---

## Step R — Now log in as **QA BB Counsellor**

**User:** `qa.bbcounsellor@qacampus.test`  
**Role:** `counsellor`

- [ ] Open Donor Ramesh Kumar · counselling → **fit to donate**
- [ ] Sign out

---

## Step S — Now log in as **QA Phlebotomist**

**User:** `qa.phlebo@qacampus.test`  
**Role:** `phlebotomist`

- [ ] Left menu → **Collections** or **Donor station** — complete collection for Ramesh → **Save** / **Complete**
- [ ] Sign out

---

## Step T — Now log in as **QA Testing**

**User:** `qa.testing@qacampus.test`  
**Role:** `testing_specialist`

- [ ] Left menu → **Testing** → open **Pending** · click a unit → **Enter results** / **Add results** · check Completed / TTI panel views
- [ ] Left menu → **Lab batch entry** opens
- [ ] Complete testing for the unit → **Save**
- [ ] Sign out

---

## Step U — Now log in as **QA Technician**

**User:** `qa.tech@qacampus.test`  
**Role:** `technician`

- [ ] Left menu → **Processing** · **Separation batch** · triple-bag workspace
- [ ] Open each blood inventory view once (pending separation, components, discarded, autoclave waste, …)
- [ ] Complete separation / processing for the unit → **Save**
- [ ] Sign out

---

## Step V — Now log in as **QA Quality Officer**

**User:** `qa.qo@qacampus.test`  
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

**User:** `qa.billadmin@qacampus.test`  
**Role:** `billing_admin`  
*(Skip W–Z if BILLING not enabled)*

- [ ] Left menu → **Cashier desk** / Billing home · **Charge master** · **Packages** — create `OPD day package` ₹800 → **Save**
- [ ] Left menu → **Billing settings** → **Save**
- [ ] Open **Accounts** · **Billing reports**
- [ ] Sign out

---

## Step X — Now log in as **QA Billing Cashier**

**User:** `qa.billcash@qacampus.test`  
**Role:** `billing_cashier`

- [ ] Left menu → **Cashier desk** — charge Test Patient One · OPD day package ₹800 → **Collect** → Cash
- [ ] Open the bill (row click) if a composer opens
- [ ] Sign out

---

## Step Y — Now log in as **QA Billing Supervisor**

**User:** `qa.billsup@qacampus.test`  
**Role:** `billing_supervisor`

- [ ] Left menu → **Approvals** · **Credit & refunds** (Billing)
- [ ] Optional ₹100 credit-note path
- [ ] Left menu → **Day close** — run day close (or open and **Cancel** if not closing for real)
- [ ] Sign out

---

## Step Z — Now log in as **QA Billing Accountant**

**User:** `qa.billacct@qacampus.test`  
**Role:** `billing_accountant`

- [ ] Left menu → **Billing reports** · **Accounts** — open one account (row click)
- [ ] Sign out

---

## Step AA — Now use the **Patient app** (not staff portal)

**URL:** `https://qacampus.patient.healthsetu.co.in/`  
**User:** phone `9876511111` (Test Patient One)

- [ ] Sign in → Home
- [ ] Open **Visits** · **Book** — book tomorrow · Dr Anita Shah → confirm
- [ ] Open **Records**, **Medicines**, **Bills**, **Profile**
- [ ] Open **Notifications**, **Messages**, **More**
- [ ] Open **Privacy**, **Security**, **Account**, **ABHA**, **Services**, **Emergency**

### Then log in again as **QA Clinic Admin**

**User:** `qa.clinicadmin@qacampus.test`

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

**Org code:** `qacampus` (or your training org code)  
**Overall:** Pass / Fail / Pass with issues  

---

## Related help

- <a href="#" data-hs-route="getting-started/admin-setup">Go-live checklist (admins)</a>
- <a href="#" data-hs-route="getting-started/before-you-start">Before you start (paper & Excel)</a>
- <a href="#" data-hs-route="getting-started/by-role">Guides by role</a>
- <a href="#" data-hs-route="core/users-roles">Users & roles</a>
