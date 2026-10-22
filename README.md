# John Construction Network Kenya — Real MVP

A mobile-first construction marketplace with user accounts, professional profiles, jobs, SQLite persistence, and a Safaricom Daraja M-Pesa STK Push integration point.

## Run locally
1. Install Node.js 20+.
2. Copy `.env.example` to `.env`.
3. Set a strong `JWT_SECRET`.
4. Run `npm install`.
5. Run `npm start`.
6. Open `http://localhost:3000`.

## M-Pesa production setup
Create a Daraja app and use production credentials in `.env`. Set `MPESA_CALLBACK_URL` to a public HTTPS endpoint. The server never sends credentials to the browser.

Required:
- MPESA_CONSUMER_KEY
- MPESA_CONSUMER_SECRET
- MPESA_SHORTCODE
- MPESA_PASSKEY
- MPESA_CALLBACK_URL
- MPESA_ENV=production

The callback marks the payment as paid only after Daraja reports ResultCode 0. For go-live, also add server-side reconciliation, rate limiting, HTTPS, backups, audit logs, fraud controls, and a proper admin/operations workflow.

## Important business/legal work before launch
- Register the business and payment merchant account appropriately.
- Use a clear service/commission agreement.
- Verify construction professionals and represent qualifications accurately.
- Publish privacy, terms, refund/dispute and professional-verification policies.
- Assess ODPC registration/compliance for the personal data the platform processes.
