# dt-clinic-operations-assignment
DT Business Analyst Assignment – Clinic Inventory Micro-Audits and Patient Care Communication System
DT Business Analyst Assignment – Rahul Dounde





Task 1: Daily Clinic Inventory Micro-Audit
Objective
In a small clinic pharmacy, inventory errors usually occur due to manual entry, time pressure, and name variations — not because of intent.
 The objective of this system is early detection of small errors, better billing discipline, and prevention of month-end inventory shocks, without increasing doctor involvement.
This system is designed to run daily in 20–30 minutes and fit into real clinic workflows.

STEP 1 — Identify High-Risk Medicines (One-time setup | ~30 minutes)
A High-Risk Medicine List is created to focus daily checks only where errors are most likely.
Criteria used:
High daily sales volume


Similar or confusing medicine names


Frequently prescribed by the doctor


Higher value per unit


High-Risk Medicine List (Example):
Medicine (Master Name)
Reason for High Risk
Dolo 650
High volume and multiple name variations
Azithromycin 500
Frequently entered using abbreviations
Pantoprazole 40
Prescribed frequently

This list is reviewed monthly and updated if required.

STEP 2 — Daily Name-Variation Check (10 minutes/day)
Daily action:
Filter the Sales Register to show only High-Risk Medicines


Group similar or incorrect name entries manually


Example mapping:
Entered Name Variants
Mapped To
Dolo / Dolo 650 / Dolo kind
Dolo 650
Azithro 500 / Azithromycin
Azithromycin 500

What is flagged:
New or unusual name variants


Misspellings not seen earlier


Action taken:
Add the variant to the mapping list


Inform billing staff to use the standard master name


This step prevents silent revenue leakage caused by name mismatches.

STEP 3 — Daily Usage Reasonableness Check (5–10 minutes/day)
For each high-risk medicine:
Expected Closing Stock
 = Opening Stock + Purchases − Total Sales (after name grouping)
Comparison example:
Medicine
Expecte d
Actual
Difference
Action
Dolo 650
1,460
1,440
−20
Review sales entries

Tolerance rule:
 Differences greater than ±2% are flagged for review.
This check highlights quantity errors or missed entries without full reconciliation.

STEP 4 — Random Bill Spot Check (5–10 minutes/day)
Daily action:
Randomly select 3–5 bills involving high-risk medicines


Verify:


Medicine name matches the master list


Quantity looks reasonable against the prescription


Why random:
 Staff cannot predict which bill will be checked, encouraging consistent billing discipline.
Output:
 Errors are logged and corrected. No punitive action is taken.

STEP 5 — Weekly Pattern Tracking (15 minutes/week)
A simple error log is maintained:
Date
Medicine
Error Type
Repeated
Aug 1
Dolo 650
Name variant
Yes
Aug 3
Dolo 650
Quantity error
No

Weekly decision rules:
Same error ≥ 3 times → staff retraining


Errors across multiple medicines → SOP update


This improves systems, not blame.

STEP 6 — Doctor Escalation Rules
Doctor involvement is required only if:
Financial impact is material


The same issue persists despite correction


Inventory mismatch affects patient treatment availability


All routine issues are handled without disturbing the doctor.

Daily Checklist
Name-variation check


Usage reasonableness check


Random bill spot check


Weekly Checklist
Error pattern review


SOP updates or retraining decisions



Task 1 Summary
This micro-audit system detects errors early, improves billing discipline, and prevents inventory shocks while respecting staff workload and protecting doctor time.














Task 2: Patient Care & Communication System Design
Objective
Doctors often lose time responding to routine patient messages on WhatsApp.
 The objective is to structure patient communication, automate routine messages, and ensure the doctor is involved only where medical judgment is required.

STEP 1 — Message Type Classification (One-time | ~20 minutes)
Message Type
Example
Doctor Input Needed
Follow-up Reminder
“Please visit on Aug 5”
No
Post-Procedure Care
“Mild swelling is normal”
No
Side-Effect Advisory
“Nausea may occur”
No
Custom Instruction
“Avoid sun exposure for 7 days”
Yes
Patient Question
“Regarding itching…”
Yes











STEP 2 — Care Control Sheet (Daily Working Sheet)
A single Google Sheet named Care_Control is maintained.
Patient
Phone
Visit Type
Message Type
Message Text
Doctor Approval
Status
Ramesh K
9XXXX
OPD
Follow-up
Auto-filled
Not Required
Pending
Sita P
9XXXX
Procedure
Post-Procedure
Auto-filled
Not Required
Pending
Arjun M
9XXXX
OPD
Custom
Blank
Required
Waiting

This sheet acts as the single source of truth.

STEP 3 — Doctor Review Window (Every 3–4 hours)
Process:
Filter rows where:


Doctor Approval = Required


Status = Waiting


Sit with the doctor for a 10-minute review window


Doctor dictates or approves responses


Responses are entered once by staff


The doctor does not type messages or open WhatsApp.




STEP 4 — Patient Question Handling (Google Form Flow)
Patients submit questions via a Google Form.
Form fields:
Name


Phone


Question


Urgency (Routine / Urgent)


Responses populate a Patient_Questions sheet:
Patient
Phone
Question
Answer
Status
Lakshmi
9XXXX
Is itching normal?
—
Pending

Questions are batched and reviewed with the doctor periodically.

STEP 5 — Message Dispatch Logic
Messages are sent only when:
Message text is filled


Status = Pending


Doctor approval is not required or already approved


Status flow:
 Pending → Sent → Closed



STEP 6 — Daily Closing Check (5 minutes/day)
Before clinic closing:
Filter Status = Pending


Ensure no critical communication is missed


Reschedule follow-ups if required



Optional Step — Automation (Later Phase)
Once workflows stabilize:
Google Apps Script reads pending rows


Messages are sent via WhatsApp API


Status updates automatically to “Sent”


Focus remains on logic, not complex automation.

Task 2 Summary
This system reduces WhatsApp chaos, protects doctor time, and ensures consistent patient communication using simple, runnable tools.
