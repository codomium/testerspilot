# Firestore compliance config

## Current document

- **Collection:** `config`
- **Document ID:** `compliance_settings`
- **Fields:**
  - `supportEmail` (string) — shown in admin; optional user-facing support contact
  - `complianceNote` (string) — internal note for policy-safe wording
  - `updatedAt` (timestamp)

Saving from the app **Admin → Settings** tab writes only this document. No payment or crypto fields are written.

## Legacy document (read-only fallback)

Older installs may still have `config/payment_settings` with `paypalEmail`. The app **reads** that document only to pre-fill `supportEmail` in the admin UI if `compliance_settings` has no support email yet. It does **not** write back to `payment_settings`.

### Optional manual cleanup

After you have saved settings once from the app (so `compliance_settings` exists), you may delete `config/payment_settings` in the Firebase console if you no longer need the legacy copy.
