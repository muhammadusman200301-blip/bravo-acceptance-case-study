# Bravo Acceptance · Case Study

> **Source code is private under client NDA.** This repo documents the product, the architecture and my role. Happy to walk through it on a call: [book 30 min](https://calendly.com/muhammadusman200301/30min).

**Bravo Acceptance** is a mobile app for auto-loan customers in the US. Customers make payments, check their balance and payment history, set up payment schedules and get reminders before due dates.

| | |
|---|---|
| **My role** | Full-stack: mobile app and backend |
| **Platforms** | iOS, Android |
| **Live** | [App Store](https://apps.apple.com/us/app/bravo-acceptance/id6821011117) · [Google Play](https://play.google.com/store/apps/details?id=com.innovateauto) |

## Tech stack
React Native · TypeScript · Node.js · Firebase Cloud Functions · Firestore · LoanPro API · PayNearMe · Twilio

## What I built
- Mobile screens for payments, balance, payment history and payment schedules
- Integration with **LoanPro** for loan data and **PayNearMe** for payments
- **Webhook-driven payment events** handled in Firebase Cloud Functions, with notifications to the customer as each payment lands
- **Twilio SMS OTP** sign-in
- Debugging of external API failures and payment confirmation issues in production

## Payment flow (simplified)

```
Customer app ──► Cloud Function ──► PayNearMe (payment)
                                       │
PayNearMe webhook ──► Cloud Function ──► LoanPro (post payment)
                            │
                            └──► Push / SMS notification to customer
```

## Challenges and how I handled them
- **Payment events arriving late or more than once** – made webhook handling retry-safe so a repeated event doesn't post a payment twice.
- **Failures in outside providers** – logged every external call, traced failures through webhook logs and provider responses, and fixed them at the root cause.
- **Secure sign-in for financial data** – SMS OTP via Twilio and strict access to loan records.

---
More of my work: [Portfolio](https://muhammadusman-portfolio10.netlify.app) · [LinkedIn](https://www.linkedin.com/in/muhammad-usman-987852388/)
