PROJECT SCAN v1 — PROTOTYPE STARTER
===================================

WHAT THIS IS
A prototype of an offline-first student tardiness registry. It supports a local encrypted vault, fictional demo students, CSV masterlist import, search, one-tap registration, duplicate checks for the same local date, recent records, and CSV export.

IMPORTANT SECURITY LIMITS
- This is a prototype, not a security-audited or school-approved production system.
- Use fictional demo data only until the school authorizes the app and its data-handling plan.
- The app encrypts its saved local vault with AES-GCM (256-bit) and derives a key from the passphrase using PBKDF2/SHA-256 (310,000 iterations). The passphrase is not stored.
- A forgotten passphrase means the encrypted vault cannot be recovered.
- CSV exports are plaintext and are NOT encrypted. Store them only in a school-approved secure location; delete them securely when no longer needed.
- Anyone who knows the passphrase and can access the app can unlock the vault. Protect and lock the device too.
- This is local-only: no syncing between phones, no user accounts, no central audit log, no server-side controls, and no guaranteed protection against a compromised phone/browser.
- The browser's local storage can be deleted by the user, browser cleanup, or device management. Maintain a tested backup plan.
- Timestamps use the device's local clock; incorrect device time can make records inaccurate.
- Do not store actual student data in a public code repository or share a real masterlist through unapproved services.

HOW TO TEST ON A COMPUTER
1. Extract the ZIP to a folder.
2. Install Python 3 if not already installed.
3. Open Terminal/Command Prompt in the extracted folder.
4. Run: python -m http.server 8000
5. Open http://localhost:8000 in a modern browser.
6. Create a strong, unique passphrase of 12+ characters and confirm it.
7. Click “Load fictional demo students”, search a demo name, and register it.
8. Refresh the page, unlock the vault, and verify the records remain.
9. Test duplicate prevention and CSV export.

HOW TO TEST ON A PHONE
The service worker and Web Crypto encryption require a secure context: HTTPS or localhost. To use the app on a phone, publish the app files to an HTTPS host approved by the school, open that HTTPS URL on the phone, and load the app once while online. Then use the browser's “Add to Home Screen” option if available. Test airplane mode before relying on it. Do not put student data in the hosting repository; the code files should contain no real records.

CSV FORMAT
Use a UTF-8 CSV with these exact headers:
student_id,name,grade,section
2026-001,Sample Student,11,STEM A

Importing a new roster REPLACES the previous roster but keeps existing tardiness entries. Test imports with fictional data first and verify the result.

NEXT BEFORE REAL DEPLOYMENT
1. Obtain school administration approval and involve the school's ICT/data-protection contact.
2. Review compliance with the Data Privacy Act of 2012 and applicable school policies.
3. Agree who may use the device, access the masterlist, export reports, correct records, and retain/delete backups.
4. Test recovery, offline operation, duplicate handling, wrong-time behavior, and CSV correctness.
5. Arrange an independent code/security review before using real student data.
