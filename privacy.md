# Privacy Policy for The Money App

**Last Updated: 11 October 2026**

> This canonical policy is kept in sync with the in-app Privacy Policy screen
> (`PersonalFinanceApp/Views/More/PrivacyPolicyView.swift`). When you change one,
> change the other — the same disclosures (external services, document vault
> retention, deletion scope) must appear in both.

The Money App ("we", "our", "the App") is committed to protecting your privacy. This policy explains what data the App handles, how it is stored, and your rights.

---

## 1. Privacy-First Architecture

The Money App is designed with a privacy-first, offline-first architecture. Your financial ledger is stored on your device using Apple's SwiftData framework. We do not operate servers, databases, or cloud infrastructure that stores your personal or financial information. If you explicitly enable the optional iCloud Document Vault, vault files are stored in your own Apple iCloud account; ledger records are not synced to iCloud.

- No user accounts or sign-ups are required.
- No financial-ledger cloud sync. Only vault documents you choose can be stored in your own iCloud Drive, and you can turn that off.
- No analytics, tracking pixels, or advertising SDKs are embedded in the App.
- No third-party data brokers receive any information from the App.

## 2. Data We Handle

All of the following data is stored locally on your device and is never transmitted to our servers:

**Financial Records:** Transactions, accounts, budgets, goals, assets, liabilities, insurance policies, credit card details, recurring payments, and investment holdings.

**Personal Identifiers (Optional):** PAN number, Aadhaar number, bank-account identifiers, and mutual-fund folio identifiers you choose to store. These are encrypted at rest using AES-256-GCM encryption with keys stored in the iOS Keychain.

**App Preferences:** Currency preference, notification settings, biometric authentication preference, and search history. Stored via UserDefaults on-device.

**Bank SMS (optional)** -- If you set up the SMS Auto-Track shortcut, bank transaction SMS messages you choose to forward via the iOS Shortcuts app are parsed on your device into transactions. The App never reads your messages directly and no SMS content leaves your device.

**Details read from your financial emails (only if you turn on Gmail Auto-Track)** -- For emails the App recognises, it keeps the transaction it records and, where the email states them: the last digits of the account or card, a stated account balance and its date, a card statement's amount due, minimum due and due date, and auto-pay mandate details (merchant, limit, frequency). It also keeps each email's Gmail message ID so the same email is not processed twice, and, for emails it flags as possibly not being a payment, the email's subject line and sender so you can review the flag. Nothing else from an email is stored. These details stay on your device and are included in your encrypted backups.

**Your corrections** -- Categories you assign to a merchant, and names you give merchants, are stored on your device so later payments to the same merchant can be suggested the same way.

**Home-screen widget** -- The widget displays a monthly spending summary (amounts and your top spending category) stored in an App Group container on your device, protected by iOS file protection.

## 3. Third-Party Services

The App connects to the internet only for the following optional or read-only features. It runs no backend of its own:

**Google Gmail API** -- If you turn on the optional Gmail Auto-Track feature, the App connects to your Gmail account with read-only access (scope: gmail.readonly) through Google OAuth and searches for financial emails: bank and card transaction alerts, card statement summaries, auto-pay mandate notices, dividend notices, insurance premium receipts, mutual-fund and stock purchase and redemption confirmations, and loan and EMI servicing emails. Searches cover known bank, card, insurer and fund senders, plus emails from any sender whose subject reads like a transaction (for example "debited", "credited" or "UPI"), so that a bank changing its email address is not missed. Every email is read and parsed on your device; an email that is not recognised as a financial record is discarded, and only its message ID is kept so it is not read again. Uncertain transactions, and every holding or loan, are added only after you approve them. Password-protected attachments are never opened automatically. The App cannot send, change or delete email. Email content is never sent to us, to any server, to advertising or analytics services, or to any AI service. The App's use of Gmail data complies with the Google API Services User Data Policy, including the Limited Use requirements. You can disconnect Gmail at any time; this revokes the App's access at Google and deletes the stored tokens from your device. Records already added stay in your ledger until you delete them.

**AMFI mutual-fund NAVs** -- If you refresh your portfolio's fund values, the App downloads AMFI's public daily NAV file (amfiindia.com) over the network and matches it on your device. The request carries no fund name or holding, so it reveals nothing about what you own; it is read-only and sends no personal data. This is a public data feed, not an account service — no sign-in or identifier is involved.

**Currency reference rates** -- If you ask for exchange rates on the Currency Rates screen, the App downloads the European Central Bank's public euro reference-rate file (ecb.europa.eu) and works out rupee figures on your device; after that first request it refreshes the file about once a month. The request names no currency and carries no identifier, so it reveals nothing about you or your spending; it is read-only and sends no personal data. If you never ask for rates, the App never contacts this service.

**Apple iCloud Drive (optional)** -- If you enable iCloud storage for the Document Vault, the App stores those vault files in the private iCloud container associated with your Apple account. Apple provides and governs that storage. The option is off by default, does not sync your financial ledger, and can be disabled in the App.

Aside from the services above, no other third-party services, SDKs, or APIs are used by the App. We do not use Firebase, Google Analytics, Facebook SDK, Crashlytics, or any similar service, and the App embeds no third-party analytics, tracking, or advertising code.

## 4. Data Security

We implement multiple layers of security to protect your data:

- **Encryption at Rest:** Sensitive identifiers (PAN, Aadhaar, bank details, and mutual-fund folio identifiers) are encrypted using AES-256-GCM. Encryption keys are stored in the iOS Keychain with kSecAttrAccessibleWhenUnlockedThisDeviceOnly protection.
- **File Protection:** The App's data files are protected with NSFileProtectionComplete, meaning they are inaccessible when the device is locked.
- **Biometric Authentication:** Optional Face ID or Touch ID can be enabled to restrict access to the App.
- **No Developer-Operated Storage:** We run no backend that stores your data. Optional providers you choose to use, including Google and Apple iCloud, apply their own security and privacy terms.

## 5. Bank Statement Import & Document Vault

The App supports importing bank statements in CSV, PDF, and XLSX formats from HDFC, ICICI, SBI, Axis, and Kotak banks. This processing happens entirely on your device:

- Files are parsed locally using deterministic parsers; image-only PDFs use Apple's on-device Vision OCR.
- No bank credentials, net banking passwords, or account login details are ever requested or stored by the App.

**Document Vault:** Statements you import, and documents you add directly (policies, receipts, invoices, portfolio files), are filed and KEPT in the App's on-device document vault so you can find them later -- they are **not** discarded after parsing. These files are stored on your device, protected with NSFileProtectionComplete, and are included in your encrypted backups. You may opt into storing them in your own iCloud Drive instead (off by default). You can view and permanently delete any stored document from the Documents screen at any time, and Clear All Data removes every one of them.

## 6. Data Export & Deletion

You have full control over your data:

**Export:** You can create CSV or JSON extracts at any time via Profile > Export Data. These are one-way extracts, not restorable backups. Use Profile > Backup & Restore to create a versioned encrypted `.moneybackup` file that the App can restore. All files are generated on-device and shared only to a location you choose.

**Deletion:** You can permanently delete all data via Settings > Clear All Data. This is irreversible and removes all transactions, accounts, budgets, goals, assets, liabilities, insurance policies, achievements, and profile data. It also erases every file in your document vault (in both on-device and iCloud Drive locations), your saved app preferences, your Gmail access tokens, and the on-device encryption key used for your identifiers.

Since we do not store your data on any server, deletion from your device is complete and final. There are no backups on our end to restore from.

## 7. Push Notifications

The App uses local push notifications (not remote/server-based) for:

- Spending-limit warnings at the threshold you choose in Notification Settings
- EMI and bill payment reminders
- Goal milestone celebrations
- Weekly financial digest summaries

These notifications are scheduled entirely on-device. No notification tokens are sent to any server. You can enable or disable notifications in the App's settings or through iOS Settings at any time.

## 8. Children's Privacy

The App is not directed at children under the age of 18. We do not knowingly collect or store personal information from children. If you are under 18, please use the App only under parental or guardian supervision.

## 9. Compliance with Indian Law

The App is designed for users in India and we are committed to complying with applicable Indian data protection laws, including the Digital Personal Data Protection Act, 2023 (DPDP Act), to the extent applicable.

Given our privacy-first architecture (no data collection, no servers, no accounts), our data handling obligations are minimal. Nonetheless:

- You have the right to access, correct, and delete your data at any time (all available through the App's interface).
- Optional services you choose — Google OAuth/Gmail and Apple iCloud Drive — may process data outside India under their own terms. The disclosures above explain what each service receives. You can use the core ledger without enabling either. The AMFI and European Central Bank downloads receive no personal data.
- We do not sell, rent, or trade any personal data.

## 10. Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be reflected in the App with an updated "Last updated" date. Since we do not collect email addresses or contact information, we cannot notify you directly -- please review this policy periodically.

## 11. Contact

If you have questions or concerns about this Privacy Policy, please contact:

**Developer:** Ateeshay Jain
**Email:** ateeshayjain@gmail.com
**GitHub:** github.com/ateeshayjain/TheMoneyApp

---

The Money App v1.0.2
(c) 2026 Ateeshay Jain. All rights reserved.
