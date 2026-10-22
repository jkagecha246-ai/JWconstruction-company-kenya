# John Construction Network — Launch checklist

## Recommended first production setup
This package is configured for a single Render web service with a 1 GB persistent disk for the SQLite database. Render's normal filesystem is ephemeral, so persistent storage is required for this SQLite setup.

### 1. Put the project in GitHub
Create a new GitHub repository named `john-construction-network` and upload the contents of this folder.

### 2. Create the Render service
In Render: **New → Blueprint** and select the GitHub repository. Render will read `render.yaml`.

The service is configured with:
- Node.js 20+
- `npm install`
- `npm start`
- `/api/health` health check
- persistent disk mounted at `/var/data`
- generated JWT secret

### 3. Add M-Pesa production credentials
In Render → Environment, enter the values supplied by Safaricom/Daraja:
- `MPESA_CONSUMER_KEY`
- `MPESA_CONSUMER_SECRET`
- `MPESA_SHORTCODE`
- `MPESA_PASSKEY`
- `MPESA_CALLBACK_URL`

The callback must be the public HTTPS URL of this app followed by:
`/api/payments/mpesa/callback`

Never put these secrets in GitHub or send them in ChatGPT.

### 4. Test before taking customer money
First use Daraja sandbox credentials. Verify:
1. registration/login
2. job creation
3. STK Push
4. callback receipt/status update
5. duplicate/failed payment handling
6. job status changes

Only after successful sandbox testing should production credentials be enabled.

## Important production work still required
This is a working MVP backend, not a guarantee of production readiness. Before public launch, add:
- admin dashboard and role controls
- professional identity/credential verification
- payment ledger and reconciliation
- commission rules and professional payouts
- refunds/disputes
- stronger rate limiting and abuse protection
- audit logs and monitoring
- backups and recovery testing
- privacy notice, terms, refund/dispute policy and data-protection compliance
- proper production database migration if the network grows beyond a single service instance
