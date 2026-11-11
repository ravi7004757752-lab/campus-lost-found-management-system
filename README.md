# 🎒 Campus Lost & Found Management System

> **Find what you lost. Return what you found.**
>
> A complete web app for a college campus: students report lost and found items, the system auto-matches them, owners claim items with a secret detail only they would know, and an admin verifies ownership before an in-person handover — with a college ID check.

[![Live Site](https://img.shields.io/badge/Live%20Site-Netlify-00C7B7?style=for-the-badge)](https://campuslostandfound12.netlify.app/)
[![GitHub Pages Ready](https://img.shields.io/badge/Deploy-GitHub%20Pages-181717?style=for-the-badge&logo=github)](https://github.com/ravi7004757752-lab/campus-lost-found-management-system)
[![Firebase](https://img.shields.io/badge/Backend-Firebase-FFCA28?style=for-the-badge&logo=firebase)](https://firebase.google.com/)
[![Made for College](https://img.shields.io/badge/Built%20for-ADSA%20%E2%80%A2%20OOP%20%E2%80%A2%20DBMS-blue?style=for-the-badge)](https://campuslostandfound12.netlify.app/)

**🔗 Live demo:** https://campuslostandfound12.netlify.app/
**📦 This repo:** `index.html` is the whole app — open it, or deploy it anywhere.

---

## ✨ What it does

| Feature | How it works |
|---|---|
| 📝 **Report lost / found** | Name, photo, category, location, date, description and contact — in one form. |
| 🔍 **Search & browse** | Search by name, filter by type / category / location, sort newest first. No sign-in needed to browse. |
| 🤖 **Auto-match** | After every report, the system suggests possible matches by category, location, keywords and close dates, with a match %. A match is only a suggestion — never proof. |
| 🔐 **Claim with secret proof** | To claim an item, sign in and give a secret identifying detail only the real owner would know — a scratch, a sticker, the contents of a wallet, a name inside a notebook, a lock-screen photo. You cannot claim your own report. |
| 🛡️ **Admin verification** | An admin sees the secret proof and both private contacts, compares the proof with the actual item and description, then approves (**Verified**) or rejects the claim. |
| 🤝 **In-person handover** | After approval, My Desk shows a handover box with the verified owner's contact and the instruction to collect in person and show a college ID. The admin contacts both sides privately to arrange the meeting point. Only after the ID check and handover does the admin mark the case **Returned**. |
| 🗑️ **Admin delete** | Admins can delete **Returned / Closed** cases only (with a confirmation warning that the item and all its claims are deleted permanently). Students never see a Delete button. |
| 🙈 **Privacy by design** | Reporter and claimant phone/email and secret details are **never shown publicly** — only to the owner, the claimant and the admin. Signed-out visitors see only: *"Reporter's contact is kept private — after your claim is verified, the admin connects you both."* |

> ⚠️ **No automatic SMS / email alert exists yet.** The admin contacts the owner directly from the private claim contact.

---

## 🔄 The full journey — from lost to returned

```
Lost item reported          Found item reported
        \                          /
         └─ Auto-match suggests ──┘
                    ↓
         Owner claims it
     (secret detail, privately)
                    ↓
        Admin verifies proof
   secret → photo → date/location
                    ↓
              ✅ Verified
                    ↓
   Admin contacts both sides privately
   My Desk shows the handover box:
   "Collect it in person, show your
    college ID"
                    ↓
      🤝 In-person handover
      + college ID check
                    ↓
            ✅ Returned
```

### Statuses

| Status | Meaning |
|---|---|
| **Open** | Reported, waiting for a match / claim. |
| **Claimed** | Someone has claimed it, waiting for admin verification. |
| **Verified** | Admin confirmed the secret proof — the claimant is the owner. |
| **Returned** | Handed over in person after the ID check. |
| **Closed** | Case finished / no further action. |

> **Approved ≠ Returned.** A claim can be Verified and still not handed over yet.

---

## 🧪 Try it in 2 minutes (demo accounts)

No real account needed — use the demo buttons on the sign-in page:

| Account | What you can do |
|---|---|
| **Demo Student** (`student@campus.edu`) | Report items, search, claim items, track your reports & claims in My Desk. |
| **Demo Admin** (`admin@campus.edu`) | Everything a student can do, **plus** the Admin dashboard: verify claims, mark returned, close cases, delete Returned/Closed cases, and read the admin-only Project guide. |

**A 2-minute demo to run live:**
1. Sign in as **Demo Student** → Report a **Found** item (e.g. "Blue water bottle", Main Library, today).
2. Search for it by name → open Details → note that no contact is shown publicly.
3. Sign out, sign in as **Demo Admin** → claim it with a secret detail (e.g. "black cap and a small dent on its base").
4. Open **Admin** → Pending claims → see the secret proof (admin only) → **Approve**.
5. Sign in as **Demo Student** again → **My Desk** → read the green handover box.
6. Sign in as **Demo Admin** → **Mark returned** → then in **All cases**, the Returned item shows a red **Delete** button.

Demo data is session-only — a reload resets the demo items.

---

## 🧑‍💻 For students & teachers — ADSA • OOP • DBMS

This is **one project shown in three subjects**. The full explanation, ER diagram, class diagram and viva Q&A are in the **admin-only Project guide inside the app** — they are deliberately hidden from the public pages.

### ADSA — Data Structures & Algorithms
- **HashMap** index for O(1) lookup by item ID / category.
- **ArrayList**-style lists for items and claims, with searching and sorting (newest first, by name, category, location).
- **Auto-match** scoring: category + location + keywords + close dates.

### OOP — Object-Oriented Programming
- Classes: `User`, `Item`, `LostItem`, `FoundItem`, `Admin`.
- Inheritance: `LostItem` / `FoundItem` extend `Item`.
- Encapsulation: secret proof, contact and email live in a locked private store, readable only by the claimant or an admin.

### DBMS — Database Management System
- Tables / collections: `Users`, `Items`, `Claims`, `Locations`.
- Claim lifecycle as a state machine: Reported → Claimed → Verified → Returned / Closed.
- Normalisation in practice: one item, many claims; private claim details stored separately from the public item record.

---

## 🚀 Run it yourself

### Option 1 — Just open it
Download `index.html` and open it in a browser. Demo Student / Demo Admin work immediately, no setup needed.

### Option 2 — Deploy it (free)
- **Netlify Drop:** drag `index.html` onto [app.netlify.com/drop](https://app.netlify.com/drop) — done in a minute.
- **GitHub Pages:** repo Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save. Your site will be at `https://ravi7004757752-lab.github.io/campus-lost-found-management-system/`.

### Option 3 — Connect your own Firebase (live sync)
The Firebase config in `index.html` is a placeholder. To enable live sync, fill it in with **your own** Firebase project:
1. Create a project at [console.firebase.google.com](https://console.firebase.google.com/) → enable **Authentication → Email/Password**.
2. Create a **Firestore Database** (test mode to start).
3. Register a Web App, copy its config, and replace the `firebaseConfig` in `index.html`.
4. If the connection test shows *permission-denied*, paste the Firestore rules shown in the app's Firebase box (admin-only) into Firebase Console → Firestore Database → Rules → Publish.

> Firebase sends a verification **link** by email, not a 6-digit code. Real SMS OTP would need a paid SMS provider.

---

## 🔒 Security notes

- **No real Firebase key is in this repo.** The Firebase config in `index.html` is a placeholder (`YOUR_FIREBASE_API_KEY`, `YOUR_PROJECT_ID`, …). Fill in your own Firebase config there to enable live sync, or leave it as-is — Demo Student / Demo Admin still work without it. Never commit a real API key, service-account key, or any other secret to a public repo.
- Passwords are stored by Firebase as one-way hashes — nobody, including an admin, can read a user's password back. Use **Forgot password** in the app instead.
- False claims are rejected and stay on record. One approved claim wins — an admin cannot approve a second claim on an item that already has a verified owner.

---

## 📁 What's in this repo

```
campus-lost-found-management-system/
├── index.html    # The whole app — UI, logic, Firebase, demo data
└── README.md     # This file
```

---

## 🙏 Credits

Built by **Ravi Kumar** (Chandigarh University) as a single project for **ADSA, OOP and DBMS** — with Muse.

Live site: https://campuslostandfound12.netlify.app/
