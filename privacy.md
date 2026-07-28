# Privacy Policy for The Money App

**Last Updated: 20 July 2026**

The Money App ("we", "our", "the App") is committed to protecting your privacy. This policy explains what data the App handles, how it is stored, and your rights.

---

## 1. Privacy-First Architecture

The Money App is designed with a privacy-first, offline-first architecture. Your financial data is stored exclusively on your device using Apple's SwiftData framework. We do not operate servers, databases, or cloud infrastructure that stores your personal or financial information.

- No user accounts or sign-ups are required.
- No cloud sync -- your data never leaves your device unless you explicitly export it.
- No analytics, tracking pixels, or advertising SDKs are embedded in the App.
- No third-party data brokers receive any information from the App.

## 2. Data We Handle

All of the following data is stored locally on your device and is never transmitted to our servers:

**Financial Records:** Transactions, accounts, budgets, goals, assets, liabilities, insurance policies, credit card details, recurring payments, and investment holdings.

**Personal Identifiers (Optional):** PAN number, Aadhaar number, and bank account details you choose to store in your Financial Profile. These are encrypted at rest using AES-256-GCM encryption with keys stored in the iOS Keychain.

**App Preferences:** Currency preference, notification settings, biometric authentication preference, and search history. Stored via UserDefaults on-device.

**AI Conversation History:** Messages exchanged with the in-app financial assistant are stored locally in SwiftData for conversation continuity.

**Bank SMS (optional)** -- If you set up the SMS Auto-Track shortcut, bank transaction SMS messages you choose to forward via the iOS Shortcuts app are parsed on your device into transactions. The App never reads your messages directly and no SMS content leaves your device.

**Home-screen widget** -- The widget displays a monthly spending summary (amounts and your top spending category) stored in an App Group container on your device, protected by iOS file protection.

## 3. Third-Party Services

The App integrates with one external service:

**Anthropic Claude API** -- When you use the AI Financial Assistant feature, your conversation messages and a summary of your financial context are sent to Anthropic's API (api.anthropic.com) to generate responses. This context includes account names and balances, aggregated category totals, and your recent transactions at merchant level -- account numbers, UPI handles, and reference numbers are removed before anything is sent. If you use the AI-assisted PDF statement import, statement page images (which may contain your account number and address) are sent for parsing. Documents and photos you attach in the AI CFO chat are likewise sent in full for reading — attach only what you're comfortable sharing with Anthropic under your own key. Both features are optional, off until you provide your own API key, and clearly marked in the App.

**Google Gmail API** -- If you enable the optional Gmail Auto-Track feature, the App connects to your Gmail account with read-only access (scope: gmail.readonly) via Google OAuth, fetches bank transaction alert emails from known bank sender addresses, and parses them on your device. Email content is processed entirely on-device and is never sent to us or any other third party. The App's use of Gmail data complies with the Google API Services User Data Policy, including the Limited Use requirements. You can disconnect Gmail at any time, which deletes the stored tokens from your device.

Anthropic's data handling is governed by their own privacy policy (https://www.anthropic.com/privacy). We recommend reviewing it. Notably, Anthropic states that API inputs are not used to train their models.

No other third-party services, SDKs, or APIs are used by the App. We do not use Firebase, Google Analytics, Facebook SDK, Crashlytics, or any similar service. The App contains zero third-party code dependencies.

## 4. Data Security

We implement multiple layers of security to protect your data:

- **Encryption at Rest:** Sensitive identifiers (PAN, Aadhaar, bank details) are encrypted using AES-256-GCM. Encryption keys are stored in the iOS Keychain with kSecAttrAccessibleWhenUnlockedThisDeviceOnly protection.
- **File Protection:** The App's data files are protected with NSFileProtectionComplete, meaning they are inaccessible when the device is locked.
- **Biometric Authentication:** Optional Face ID or Touch ID can be enabled to restrict access to the App.
- **API Key Security:** Your Claude API key is stored in the iOS Keychain, not in plain text or UserDefaults.
- **No Network Storage:** Since data is never sent to our servers, there is no risk of server-side data breaches affecting your financial information.

## 5. Bank Statement Import

The App supports importing bank statements in CSV and PDF formats from HDFC, ICICI, SBI, Axis, and Kotak banks. This processing happens entirely on your device:

- Files are parsed locally using on-device processing.
- Imported files are not stored after parsing -- only the extracted transactions are saved to your local database.
- No bank credentials, net banking passwords, or account login details are ever requested or stored by the App.

## 6. Data Export & Deletion

You have full control over your data:

**Export:** You can export your data at any time via Settings > Export. Exported files are generated on-device and saved to a location you choose.

**Deletion:** You can permanently delete all data via Settings > Clear All Data. This is irreversible and removes all transactions, accounts, budgets, goals, assets, liabilities, insurance policies, chat history, achievements, and profile data.

Since we do not store your data on any server, deletion from your device is complete and final. There are no backups on our end to restore from.

## 7. Push Notifications

The App uses local push notifications (not remote/server-based) for:

- Budget threshold alerts (when spending reaches 80% of a budget)
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
- No personal data is transferred outside India by the App itself. However, when you use the AI Assistant, conversation data is sent to Anthropic's API servers which may be located outside India. Use of this feature is optional and at your discretion.
- We do not sell, rent, or trade any personal data.

## 10. Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be reflected in the App with an updated "Last updated" date. Since we do not collect email addresses or contact information, we cannot notify you directly -- please review this policy periodically.

## 11. Contact

If you have questions or concerns about this Privacy Policy, please contact:

**Developer:** Ateeshay Jain
**Email:** ateeshayjain@gmail.com
**GitHub:** github.com/ateeshayjain/TheMoneyApp

---

The Money App v1.0.0
(c) 2026 Ateeshay Jain. All rights reserved.
