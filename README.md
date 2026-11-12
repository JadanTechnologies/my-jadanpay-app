# JadanPay: VTU & Data Reselling

A mobile-first web app for airtime, data, bill payments, wallet-to-wallet transfers, earnings, referrals, and a receptionist (front-desk) view.

Developed by **Jadan Tech Solutions Nig Ltd**.

Status: **front-end prototype.** All money, accounts and verification are simulated in the browser. See [Before going live](#before-going-live).

---

## Run locally

No build step and no dependencies.

```bash
npm start        # serves the folder at http://localhost:3000
```

Or open `index.html` directly in a browser.

## Project structure

```
jadanpay/
├── index.html        All screens, sheets, modals and popups
├── css/
│   └── styles.css    Cartoon theme, animations, splash, responsive layout
├── js/
│   └── app.js        All logic: accounts, payments, PIN, receipts, chat, etc.
├── package.json      `npm start` dev server (no runtime dependencies)
├── .gitignore
└── README.md
```

---

## Demo accounts

Shown on the login screen while `SHOW_DEMO = true` (near the bottom of `js/app.js`).

| Role         | Email                  | Password |
|--------------|------------------------|----------|
| Customer     | demo@kwiktop.app       | demo1234 |
| Receptionist | reception@jadanpay.app | front123 |

Set `SHOW_DEMO = false` before showing the app to anyone else.

---

## Features

### 1. Splash screen
- Letters **J-A-D-A-N-P-A-Y** appear in one straight row with a bouncy scale-in, then a confetti burst.
- The sticker **THE** pops in above the logo.
- Six service chips (Airtime, Data, Bills, Cable TV, Electricity, Send money) fly in from random directions.
- A yellow box flips through the service names.
- A shine sweeps across the logo.
- Tap a letter to wiggle it. Tap the mascot to spin it with confetti and a chime.
- "Developed by Jadan Tech Solutions Nig Ltd" stays at the bottom.
- Skip button, or it ends automatically after about 6.4 seconds.

### 2. Sign-up and log-in
- **Log in** with email and password. The form shows clear messages for each error: wrong password (with attempts left), unknown email, invalid email, missing password, no internet connection, and too many attempts.
- **Sign up** asks for full name, email, phone number (11 digits starting with 0), password, and an optional referral code. The phone and referral fields appear only on sign-up.
- **Strong passwords only.** A password needs 8+ characters, an uppercase letter, a lowercase letter, a number, and a symbol. A checklist ticks off each rule as you type, and sign-up is refused until all are met.
- **Password buddy:** a cartoon face closes its eyes while you type, then opens them. It frowns with a warning when the password is weak and smiles when it is strong.
- **Show / hide password** button on every password field.
- **Passwords are hashed** (salted SHA-256). They are never stored as readable text.
- **Forgot password:** enter your email, get a 6-digit code (shown on screen in demo mode), then set a strong new password.
- **Success messages:** account created, login successful, password reset successful.
- **Fingerprint login** (simulated) once turned on in Settings.
- **Enter key** submits the form.
- **Demo buttons:** fill the customer or receptionist demo details in one tap.
- The screen scrolls on small phones, and the demo box is compact.

### 3. Home (customer)
- **Wallet balance** card with an **Add money** button. It shows the personal virtual account number, with copy and share.
- **Services tiles** (Airtime, Data, Cable TV, Electricity, Bills, More) bounce gently and open each service's page.
- **Wallet tools:** Send money, Referrals, Saved numbers, Alerts, Verify, Help (support chat), and Network health.
- **Earnings card:** profit from sales and referral rewards. Withdraw any amount to your wallet, with no minimum.
- **Today's profit, transaction count, and revenue chart.**
- **Recent transactions:** tap any row for details.
- **Scrolling service banner.**

### 4. Airtime
- Choose MTN, Airtel, Glo or 9mobile. The network is detected automatically from the phone number's prefix.
- Preset amounts (₦100 to ₦5,000) or a custom amount (₦50 to ₦50,000).
- **Recent number suggestions** appear as you type or tap the field.
- **Pick from phone book** imports a contact on Android Chrome, or shows sample contacts elsewhere.
- Margin: 3% (5% for Resellers).

### 5. Data
- Four network tiles. Tap a network and its bundles **drop down** below it. Tap the header to collapse or open the list.
- Each bundle shows your cost and your profit.
- Same number entry, suggestions and phone-book import as airtime.

### 6. Bills and services
Each service has its own page, listing what's available and how it works, with fees.
- **Cable TV:** DSTV, GOTV and Startimes. Each provider drops down its plans.
- **Electricity:** Ikeja Electric, Eko DisCo and Abuja DisCo, with prepaid token amounts.
- **Internet & bills:** Spectranet, Smile and Startimes, with data plans.
- **More:** WAEC and NECO PINs, and betting wallet top-ups.
- Tapping a plan opens the purchase with that provider and option already selected.

### 7. Send money (wallet to wallet)
- The recipient must be a registered JadanPay user. Enter a number and the name appears with a green tick. An unregistered number is refused, and you can't send to yourself.
- The sender's wallet is debited and the recipient's wallet is credited. The recipient gets a "Money received" alert and a history entry.
- Minimum ₦100. No fee.

### 8. Confirmations, PIN and fingerprint
Every money movement (airtime, data, bills, transfers, withdrawals) goes through three checks:
1. **Confirm popup** listing the details, with **Yes, confirm** or **No, go back**. It can't be dismissed by tapping outside.
2. **Transaction PIN:** on first use, the app asks you to create a 4-digit PIN and confirm it. After that, every transaction asks for it.
   - 3 wrong PINs trigger a **10-minute block** with a countdown popup.
   - **Forgot PIN?** opens support chat with a message about the PIN.
   - **Contact support** on the block popup opens the chat.
   - Change your PIN from **Profile → Transaction PIN**. You must enter the current PIN first.
3. **Fingerprint for payments** (optional, from Settings). Simulated in this version.

### 9. Transactions, receipts and sharing
- Every transaction has a **date and time**.
- **Transaction details** sheet: share, repeat (airtime, data or transfer), report a problem (opens support chat), or cancel.
- **Receipt** on each successful payment: a paper-style card with a PAID stamp, an animated amount, a JadanPay watermark, and date and time.
- **Save image:** creates a PNG receipt with the watermark. On phones that support it, the image goes straight to the share menu.
- **Share:** WhatsApp, Email, SMS, Telegram, Copy, or More (the phone's share menu).
- **Preview and edit** the message before sending.

### 10. Wallet tools
- **Send money:** see section 7.
- **Referrals:** your invite code (for example `JP-ADA`). Friends who sign up with it give you ₦100 in earnings and get a ₦100 bonus. A simulate button stands in for a real sign-up.
- **Promo posts:** five ready-made styles (Savings, Hype, Family, Earn money, Urgent). Each includes your code. Share to WhatsApp, Facebook, X, Telegram, Instagram, TikTok, Email, SMS, Copy, or More.
- **Saved numbers:** save frequently used numbers and tap **Use**.
- **Alerts:** a bell in the header with an unread count. Covers payments, deposits, referral rewards, PIN blocks, and wallet verification.
- **Verify wallet:** BVN or NIN (11 digits), then a personal 10-digit virtual account number for bank transfers. Use "Simulate incoming transfer" to test a deposit.
- **Network health:** an overall success donut, the best network right now, and a 7-day success bar chart for each network. Refresh readings to simulate new results.
- **Help:** support chat.

### 11. Profile and settings
- Tap your initials in the header to open your profile.
- **Profile picture:** upload any image (cropped square), pick a cartoon avatar, or go back to initials.
- **Personal details:** change your name and phone number.
- **Change password** (current password required, strong password enforced).
- **Transaction PIN:** set up or change.
- **Account tier:** upgrade to Reseller (₦2,000) for a higher airtime margin (5%).
- **Settings:** fingerprint login, fingerprint for payments, sound effects, and vibration.
- **Log out.**

### 12. Earnings
- Profit from every sale and referral reward goes to earnings, separate from your wallet.
- **Withdraw to wallet** with any amount. **All** and **Half** buttons fill in the amount.
- Each withdrawal shows in history.

### 13. Support chat
- Floating 💬 button above the navigation bar, and a **Help** tile.
- Quick questions: failed payment, data not received, fund wallet, talk to an agent.
- Scripted replies with a typing indicator. Mentions of PIN, failed payments, verification, balance and funding get specific answers.

### 14. Announcements
- Shown once per session after log-in: welcome, network health, wallet verification, and maintenance.
- **Next** steps through them. **Cancel** closes them at any time.

### 15. Receptionist desk
A separate role (set in the code, see the demo account) for front-desk staff:
- Replaces Home with **Desk**.
- **Today's sales:** total and count.
- **Find customer:** enter a number to see its network, with quick Airtime, Data and Bills buttons pre-filled.
- **Queue:** walk-in customers. **Serve** opens airtime for that customer.

### 16. Offline and feedback
- A red bar appears at the top when there is no internet connection. A toast confirms when the connection returns.
- Messages show a green tick for success or a red warning for errors. The warnings include a short shake.

### 17. Sound and feel
- Synthesised success chime and tick sounds (no audio files).
- Vibration on success where the device supports it.
- Confetti on success, cursor glow, tilting cards, and magnetic buttons on desktop.
- Cartoon theme throughout: thick outlines, hard shadows, rounded fonts (Fredoka), and bright colours.

---

## Code map (js/app.js)

Sections appear in this order:

1. **Splash:** letter build-up and the splash surprises (chips, flip word, tap effects).
2. **Data model:** `NETS`, `PLANS`, `BILLS`, `SVC`, `USERS`, `DEMO_CONTACTS`, `ANN`, `PRESETS`, `PW_RULES`.
3. **Helpers:** `$`, `money`, `detect`, `setPhone`, `normPhone`, `toast`, `copyText`, `fmtWhen`.
4. **Navigation:** `go(view)` switches screens and refreshes the one you open.
5. **Auth:** `setMode`, `signIn`, `signOut`, hashing (`hashPw`, `setPw`, `checkPw`), password buddy, show/hide, sign-up and log-in handlers, forgot password.
6. **Checkout:** `showSummary`, `payNow`, `showReceipt`, `receiptCanvas`, `saveReceiptImage`, `receiptText`.
7. **Confirm and PIN:** `guardTx` (confirm popup), `gateTx`, `openPinSetup`, `openPinVerify`, `pinVerifyStep`, `showLock`, buttons.
8. **Wallet:** earnings (`addEarn`, `doWd`), send money (`findUserByPhone`, `creditUser`), virtual account (`renderKyc`), referrals and promo posts (`openPromo`, `promoShare`), saved numbers, alerts (`addNote`, `renderAlerts`).
9. **Services:** `showService` (drop-down options), `openBill`, `renderBill`, `renderPlans` (drop-down bundles).
10. **Support and announcements:** `sendChat`, `botReply`, `maybeAnn`.
11. **Settings:** sound, vibration, fingerprint (`bioScan`, simulated).
12. **Network health:** `renderNet`, `NETSTAT`.
13. **Receptionist:** `updateDesk`, `renderQueue`.
14. **Init:** first render.

---

## Before going live

This prototype runs entirely in the browser. Before real customers use it, these need a server and real providers.

| Area | Now (prototype) | Needed for launch |
|------|-----------------|-------------------|
| Accounts | Stored in memory, reset on reload | Database with sessions |
| Passwords | Salted SHA-256 in the browser | Server-side bcrypt or argon2 |
| Transaction PIN | Hashed in memory, 10-minute block | Server-side attempts and lock |
| Airtime, data and bills | Simulated, no provider call | VTU provider API (e.g. VTpass, Monnify, Flutterwave), keys kept on the server |
| Wallets and transfers | Between accounts in one browser session | Server ledger with transactions |
| Virtual accounts | Random 10-digit numbers | Licensed partner bank |
| BVN / NIN | Simulated 11-digit check | Approved KYC provider |
| Withdrawals to bank | Not built (moves earnings to wallet only) | Bank transfer API |
| Receptionist role | Hard-coded demo account | Admin tool creating staff accounts on the server |
| PIN reset | Support message only | Support tool that verifies identity |
| Fingerprint | Simulated scanner | WebAuthn with stored credentials |
| Support chat | Scripted replies | Live agent system |
| Network health and contacts | Sample data | Live metrics and real phone book access |
| Referral and promo | Simulated rewards | Server-side reward rules |
| Receipts | Generated in the browser | Server-generated, signed receipts |

**Security checklist before launch:**
- Set `SHOW_DEMO = false`, and remove the demo accounts.
- Move all secrets (provider keys, bank keys) to the server. Never put them in this file.
- Enforce the PIN, lock and confirmation rules on the server too, not only in the browser.
- Use HTTPS, rate limiting on log-in and PIN checks, and audit logs for money movements.
- Test on real Android and iOS devices, and on slow mobile networks.

## Suggested next steps

1. Split `js/app.js` into modules (`auth.js`, `wallet.js`, `payments.js`, `receipts.js`, `ui.js`) as the code grows.
2. Build a backend (Node/Express, Supabase or Firebase) for accounts, the transaction ledger, PIN checks and webhooks.
3. Add automated tests for `PW_RULES`, `detect`, `normPhone`, `fmtWhen` and the PIN lock logic.
4. Add real VTU provider and bank integrations in a server-side service.
5. Review all copy and demo text before launch.

---

© Jadan Tech Solutions Nig Ltd. All rights reserved.
