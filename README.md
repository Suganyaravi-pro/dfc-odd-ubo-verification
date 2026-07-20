# 🕵️ UBO Verification Automation (Kofax RPA)

## Overview
A Kofax RPA solution automating the Ultimate Beneficial Owner (UBO) verification process for customer due diligence, updating internal records with UBO details as provided by clients to the client outreach team.

## Challenge
UBO verification for customer due diligence involved manually cross-referencing UBO details across multiple systems (BCDB, KVK, Concord), creating and linking records, checking for discrepancies, and uploading compliance documents. It was a time-consuming, manual, and error-prone process.

## My Solution
I designed, built, and maintained a Kofax RPA solution that automates UBO data extraction, validation, record linking, and document handling for customer due diligence, working across BCDB, the KVK registry, and Concord.

## Process Flow
1. **Input** — the robot receives an input file and extracts all relevant UBO and customer details
2. **Login & UBO search** — the robot logs into BCDB (the internal customer/beneficial-owner database) using UBO details and searches for the UBO record
3. **Address comparison** — the robot compares the UBO's address details for validation
4. **Customer record login** — the robot logs into BCDB using customer details
5. **UBO record management:**
   - If the UBO is **not present** in BCDB, a new BC (Business Contact) record is created and linked to the company
   - If the UBO is **already present** in BCDB, the existing record is linked to the company
   - Existing outdated UBO links are removed as part of this update
6. **Validation check** — if all UBOs are successfully linked and the IPD code is `IPD0000`, the robot creates a JSON file containing the Customer BC number and KVK number
7. **Session handoff** — a Desktop Automation robot is called to close prior sessions and log into the KVK (Dutch Chamber of Commerce) registry site
8. **Company lookup** — the robot searches the KVK number on the site
   - If the company is **found**, the process continues
   - If the company is **not found**, a fallout occurs and the Business Process Run (BPR) is marked as failed
9. **UBO data extraction & reporting** — for each UBO, data is extracted from a CSV file, and the Desktop Automation robot answers the required reporting questions
10. **Discrepancy handling** — if a UBO exists in both KVK and BCDB but with differing details, the updated information is reflected in the KVK UBO application
11. **Output file update** — an entry is added to the output import file
12. **Document handling in Concord** (the document management system):
    - Searches for the relevant dossier
    - Uploads the standard UBO register document
    - Closes the dossier

## Impact
- Automated a previously manual, multi-system UBO verification process across BCDB, KVK, and Concord
- Reduced manual effort in matching, linking, and validating UBO records for customer due diligence
- Improved consistency by automatically reconciling UBO detail mismatches between systems
- Streamlined document handling and reporting through end-to-end automation

## Tools
`Kofax RPA` `Desktop Automation` `JSON` `CSV`

---
*Note: This repository is a write-up of a project built during my professional role. Actual source code and company data are confidential and not included here.*
