# Hands-on: Doctor

**Role:** `clinic_doctor`  
**Practise on:** `https://{your-org}.healthsetu.com/`  
**Login:** your doctor login (e.g. `qa.doctor@…` in a training org)  
**Time:** about 20–30 minutes

<div class="callout callout--tip">
  Sign out of any other account first. Open only the staff portal above — not a module Static Web App URL.
</div>

## You will learn

- Open your doctor desk / OPD queue
- Complete one patient visit (note + Rx)
- See procedures and reports you are allowed to use
- Confirm you cannot change clinic fee masters

## Step by step

1. [ ] Sign in at `https://{your-org}.healthsetu.com/`
2. [ ] Open **Doctor desk** (`/clinic/doctor-desk`) or **OPD** (`/clinic/opd`)
3. [ ] Pick a booked patient for today (ask reception to book **Test Patient One** if the queue is empty)
4. [ ] Open the visit
5. [ ] Enter a short note, e.g. `URI — symptomatic care`
6. [ ] Add a medicine (e.g. paracetamol 500 mg) and save
7. [ ] Finish / sign the visit if your clinic uses sign-off
8. [ ] Open **Procedures** (`/clinic/procedures`) — browse the board (start a sitting only if trainers say so)
9. [ ] Open **Reports** (`/clinic/reports`) — open one report you are allowed to see
10. [ ] Try **Fee items** (`/clinic/fee-items`) — you should **not** be able to edit masters (or the menu is hidden)
11. [ ] Sign out

## Screens this role uses

- `/clinic/doctor-desk`
- `/clinic/opd`
- `/clinic/procedures`
- `/clinic/reports`
- `/clinic/patients/person/:id (chart)`

## Done when

- [ ] You finished every step without an unexplained error banner
- [ ] You know which sidebar items are yours (and which are not)

## Next

Reception books the patient → you see them in OPD. After you finish, cashier collects the fee — see <a href="#" data-hs-route="getting-started/practice/clinic-cashier">Clinic cashier</a>.

<a href="#" data-hs-route="getting-started/by-role">← All roles</a>
