# LEGACY — Professional Services MVP

## Requirements
- Node.js 18+
- npm

## Run locally (Windows PowerShell)
1. Extract the ZIP and open PowerShell in `LEGACY-Liquid-Glass`.
2. Install dependencies:
   ```powershell
   npm install
   ```
3. Copy `.env.example` to `.env`.
4. Generate a new private JWT secret:
   ```powershell
   node -e "console.log(require('crypto').randomBytes(48).toString('hex'))"
   ```
   Put the result after `JWT_SECRET=` in `.env`.
5. Start:
   ```powershell
   npm start
   ```
6. Open `http://localhost:3000`.

## This update
- Adds persistent light/dark theme selection using local storage.
- Adds a multilingual interface dictionary and translates many fixed UI labels and messages into Russian and English.
- Language selection is remembered after refresh.
- Keeps the existing specialist marketplace, profiles, favorites, filters, order workflow, and verified-order rating features.

## Important limitations
- **The interface is not yet fully 100% localized.** Some dynamically generated labels, the full 120-specialty catalog, category names, server validation errors, and user-entered content still need dedicated translations. This ZIP must not be treated as the completed 100% trilingual release.
- The dark theme has been added, but visual QA on multiple browsers/devices is still required.
- This is a functional MVP, not a production-hardened service. JSON-file storage is intended for local testing and a small single-instance deployment. For production, migrate to PostgreSQL, configure backups, rate limiting, verification, password reset, moderation, and audit logging.
- The ZIP intentionally contains an empty `data/db.json` so it does not redistribute personal account data from the uploaded archive. Existing records remain in the original ZIP you uploaded; back them up privately before replacing your local project.
- The original uploaded archive contained a `.env` file. It has been excluded from this output. If its JWT secret was ever shared or committed, generate a fresh secret and update your private `.env`.
- Use HTTPS in deployment. Keep `.env` private and never commit it. Use persistent storage for the database; ephemeral hosting filesystems can lose data on restart.
- Profile images are stored as data URLs in the JSON database. Production should use object storage and image processing.
- Admin panel, chat, proposal workflow, and team-management features are not fully implemented in this MVP.
