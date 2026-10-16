# CareerPilot — LinkedIn Career OS (PWA prototype)

## What's included
- Dark, responsive dashboard designed for phone and desktop
- Job opportunity form, role-search shortcuts and status tracking
- Resume summary draft helper
- LinkedIn headline/About drafts and profile checklist
- Post draft generator and saved drafts
- Routine settings and native LinkedIn job-alert setup guide
- Interview practice questions
- CSV export for application tracking
- PWA manifest and service worker for install/offline shell caching

## Run locally
For best PWA behavior, serve these files over localhost/HTTPS:
```bash
python -m http.server 8000
```
Then open `http://localhost:8000`. Service workers generally do not work when opening `index.html` directly as a file.

## Important integration status
This is a front-end prototype. It does **not** currently connect to LinkedIn, an AI API, email, or a database. Drafts and tracker records use browser `localStorage`, which is not secure multi-user storage. Do not store passwords, session cookies, OAuth tokens, or sensitive data here.

### To implement production integrations
1. Deploy the PWA over HTTPS.
2. Build a server-side API (e.g. Next.js route handlers) and managed authentication/database (e.g. Supabase Auth + Postgres with row-level security).
3. Keep all secrets and access tokens server-side; use OAuth with least-privilege scopes, CSRF/state checks, secure sessions and explicit revocation.
4. Register an app in LinkedIn Developer Portal and request only products/permissions actually available and approved for that app. Publicly available permissions may allow member sign-in and certain social sharing; broader job, recruiter or member-data APIs may require separate approval. Do not assume job-search or account-management access.
5. Add AI drafting behind a server-side endpoint and ask the user to review outputs before any external action.
6. Add scheduled notifications only after the user explicitly configures a delivery provider and permissions.

The app deliberately does not automate scraping, mass connection requests, mass messages, or unapproved LinkedIn actions.
