# Prep pack — Excel / CSV templates

Use these **after** you fill the printable worksheets under **Getting started → Before you start**.

## How to open in Excel

1. Download the CSV for your module.
2. Excel → **Data → From Text/CSV** (or double-click; set encoding UTF-8 if Indian names look wrong).
3. Optional: copy each sheet into one workbook named `HealthSetu-prep-<org>.xlsx`.
4. Type into HealthSetu from the workbook — do not redesign ops in the browser.

## Files

| Module | File | Columns |
|--------|------|---------|
| HR | `hr-places.csv` | site, city, open_days, approx_staff, notes, pt_state |
| HR | `hr-org-chart.csv` | site, department, job_title, typical_count, reports_to |
| HR | `hr-shifts.csv` | site, shift_name, start, end, used_by |
| HR | `hr-join-checklist.csv` | document_or_step, required_yn, kept_by_today |
| RakhtSetu | `rakht-hospitals.csv` | hospital_name, city, contact, phone, doctors_from_hospital_yn |
| RakhtSetu | `rakht-equipment.csv` | equipment_name, location, used_for, temp_range, daily_qc_yn |
| RakhtSetu | `rakht-tests.csv` | area, test_or_marker, method, kit_brand, notes |
| RakhtSetu | `rakht-qc.csv` | area, daily, weekly, monthly, quarterly, owner_role |
| CareSetu | `care-doctors.csv` | doctor_name, specialty, council_reg, new_fee, followup_fee, in_hr_yn |
| CareSetu | `care-schedules.csv` | doctor_name, weekdays, start, end, slot_minutes, max_patients, room |
| CareSetu | `care-fees.csv` | service_name, price, notes |
| SupplySetu | `supply-locations.csv` | location_name, parent, kept_here, issued_by |
| SupplySetu | `supply-catalog.csv` | item_name, category, unit, location, min_reorder |
| SupplySetu | `supply-vendors.csv` | vendor_name, supplies, gstin, contact, required_docs |
| SwasthaSetu | `swastha-employers.csv` | employer_name, contact, phone_email, exam_types |
| SwasthaSetu | `swastha-panels.csv` | panel_name, tests_included, price |
| SwasthaSetu | `swastha-test-requirements.csv` | applies_to, department_or_job, required_tests, frequency |

Sample rows are included as examples — replace with your data.
