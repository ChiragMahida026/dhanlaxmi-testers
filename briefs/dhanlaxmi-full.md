# Mission: cover every screen of YOUR area of Dhanlaxmi, signed in to the demo account

Dhanlaxmi is a GST billing, inventory and accounting app for Indian shops. Several testers run at
the same time, each on their own phone, each owning ONE area of the app (table below). Read the
general rules, tools and report format in AGENT_BRIEF.md and follow them, with the changes here.

## 1. Sign in (all testers)
- The login is in the file `login.txt` (read it with `cat login.txt`). It holds an e-mail and a
  one-time code. Never copy them into your report, findings or screenshot names.
- Sign in with the e-mail (not a phone number). When the app asks for the code, type the code from
  the file. It is a demo account: the code is always the same.
- Typing: tap the field, take a screenshot and check the field shows a cursor or the keyboard is
  up BEFORE you type. If it is not focused, tap it again (or on its label), then type with
  `python3 scripts/android/type.py "..."`. If the text still does not appear, try
  `adb shell input text ...` once. A field that will not take text is a finding: note the screen.
- If sign-in fails after 4 different attempts, report it as a blocker with screenshots and stop.

## 2. Your area (PERSONA decides it)
| PERSONA | Area to cover completely |
|---|---|
| malik | Billing / POS: new bill (+ Bill), customer pick, items, quantity, discounts, charges, payment modes (cash, UPI, card, later, partial), save, the invoice view, PDF preview, edit bill, the Bills tab list, filters and search |
| ravi | Khata and parties: customer and supplier lists, add/edit party, party statement, receive payment, who owes (receivables), reminders screen (do not send) |
| grace | Items and stock: Items tab, add/edit product and service, units, GST rates, HSN, batches and expiry, stock adjustment, low and negative stock filters, barcode/scan screens (cancel the camera) |
| lucia | Purchases: purchase bills, purchase orders, expenses, supplier payments, debit notes, what I owe, purchase bill scan/import screens (cancel pickers) |
| anna | Sales documents and books: quotations, sales orders, delivery challans, credit notes, Accounts/reports, GST (GSTR-1, GSTR-3B, ITC), cash and bank book, day book, profit and loss, balance sheet |
| felipe | The More tab and everything not above: settings, business profile, invoice settings, printers, team/staff, notifications, data import and export screens, subscription/plans (look only), help/support, account, language switch (English and Hindi), app lock |

Go through EVERY screen, tab, sheet, filter and menu of your area: open it, scroll it to the end,
open each item's detail and its "more" menu, and go back. Then do the main task of the area once
end to end. Note screens you could not reach and why.

## 3. Hard limits (this is a shared production demo account)
- NEVER: delete the account, reset or delete the company, delete data in bulk, sign out other
  devices, change the login e-mail or phone, turn on/off security settings, buy or change a plan,
  invite or remove a real team member, or send anything (WhatsApp, SMS, e-mail, share sheets: open
  them to check they appear, then cancel).
- You MAY create test records, at most 2 of each kind (bill, party, item, purchase...). Name them
  or put in their notes `AGENT TEST <PERSONA>` so they can be found. Use small amounts (under 500).
  Saved invoices cannot be deleted in this app (they are reversed instead): keep them few.
- Do not change existing records that are not yours.

## 4. Budget and report
- Budget: about 90 actions (not 30). Take a screenshot after every action as AGENT_BRIEF.md says.
- Report as in AGENT_BRIEF.md, plus a section "Screens covered" listing every screen you opened,
  and "Not reached" with the reason. Severity: blocker / major / minor / cosmetic.
- Watch especially: wrong totals or tax, dates that differ between screens, untranslated text in
  Hindi, content hidden behind the bottom bar, crashes, endless spinners, error messages.
