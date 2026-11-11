# Campus Lost & Found Management System

Students report lost and found items, search and auto-match them, submit claims with a secret detail, and an admin verifies ownership before an in-person handover.

Live site: https://campuslostandfound12.netlify.app/

## How it works

1. **Report** — a student reports a lost or a found item (name, photo, category, location, date, description, contact).
2. **Search & auto-match** — anyone can browse/search without signing in. The system suggests possible matches by category, location, date and keywords. A match is only a suggestion, never proof.
3. **Claim** — to claim an item, sign in and give a secret identifying detail only the real owner would know (for example a scratch, a sticker, the contents of a wallet, a name inside a notebook). You cannot claim your own report.
4. **Admin verification** — an admin sees the secret proof and both private contacts (never shown publicly), compares the proof with the item, and approves (Verified) or rejects the claim.
5. **Handover** — after approval, My Desk shows a handover box with the verified owner's contact and the instruction to collect in person and show a college ID. The admin contacts both sides privately to arrange the meeting point. There is no automatic SMS/email alert.
6. **Returned / Closed** — only after the in-person ID check and handover does the admin mark the case Returned. Admins can delete Returned/Closed cases; students never see a Delete button.

## Statuses

Open → Claimed → Verified → Returned / Closed

## Tech

- Single-file static web app: `index.html` (open it directly, or deploy it to Netlify / GitHub Pages)
- Firebase Authentication (Email/Password, verification link) and Firestore for live sync
- Demo Student and Demo Admin accounts work without Firebase, for a quick demo
- Firebase Project ID and Web API key are embedded in `index.html` because a web client needs them to connect. They are not a password. Do not add service-account keys or other secrets to this file.

## Project mapping (for ADSA, OOP and DBMS demos)

- **ADSA:** HashMap index for lookup by ID/category, ArrayList-style lists, searching and sorting.
- **OOP:** User, Item, LostItem, FoundItem, Admin.
- **DBMS:** Users, Items, Claims and Locations tables (Firestore collections in this build).

The full ADSA/OOP/DBMS explanation, ER diagram and class diagram are in the admin-only Project guide inside the app, not on the public pages.
