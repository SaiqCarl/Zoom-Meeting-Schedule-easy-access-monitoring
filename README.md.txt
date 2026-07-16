# Zoom Meeting Scheduler

A lightweight, self-hosted web app for scheduling and managing Zoom room bookings across multiple accounts/rooms — with a public-facing calendar for requesters and a full admin panel for approvals, room management, and reporting. Built as static HTML/CSS/JS with [Supabase](https://supabase.com/) as the real-time backend.

## ✨ Features

### For requesters (public view)
- **Live availability calendar** — color-coded by day: available, partially booked, fully booked, or recurring.
- **Room buttons generated automatically** from whatever Zoom accounts/rooms are configured (no hardcoded room list).
- **Book a slot** with:
  - AM / PM / BOTH shifts, or fully custom start–end times
  - Optional **recurring schedules** (daily, weekly, monthly) with day-of-week selection
  - **Meeting security settings** (Waiting Room, Passcode, Authenticated Users Only, etc.), mirroring Zoom's own options
  - Optional **registration required** toggle
- **Existing bookings view** per date/room, so requesters can see what's already scheduled before submitting.
- **Light / dark theme** toggle.

### For admins
- **Dashboard** with live stats (total, pending, approved, denied requests) and a searchable/filterable request table.
- **Approve / deny workflow**, with automatic conflict detection — approving a request auto-denies any overlapping pending ones.
- **Zoom account (room) management**:
  - Add/edit/delete accounts, each with its own capacity (pax), license expiry date, and status.
  - Accounts **auto-expire** once their license date passes — no manual bookkeeping needed.
  - Blocks approval of bookings that would run past an account's expiry, with a clear "renew first" prompt.
- **Meeting reminder banner** that surfaces upcoming approved meetings.
- **Export center**:
  - Export bookings to **Excel (.xlsx)** or **CSV**.
  - Filter by month and by **individual room** (not just capacity) — every room is listed by name.
  - **Expired rooms are included** in exports and filters, clearly marked "Expired," so historical bookings are never lost.
  - **Deleted rooms are excluded** automatically, since they no longer exist in the system.
  - Exported rows include full booking details: requestor, agency, date/shift/time, **room name + status**, pax capacity, recurrence, registration, security setting, approval status, and notes.

### Data & sync
- All data (bookings, accounts, settings) is synced through **Supabase** in real time, so multiple admins/tabs stay in sync.
- LocalStorage is used as an instant local cache for snappy UI updates, with Supabase as the source of truth.

## 🧱 Tech Stack

- **Frontend:** Vanilla HTML, CSS, JavaScript (no build step, no framework)
- **Backend:** [Supabase](https://supabase.com/) (Postgres + realtime + auth-ready)
- **Excel export:** [SheetJS (xlsx)](https://github.com/SheetJS/sheetjs)
- **Icons:** [Tabler Icons](https://tabler.io/icons)

## 📂 Project Structure

```
.
├── index.html      # Markup for both the public scheduler and the admin panel
├── script.js       # App logic: booking flow, admin panel, Supabase sync, exports
├── styles.css      # Styling (light/dark theme support)
└── README.md
```

## 🚀 Getting Started

1. **Clone the repo**
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. **Set up Supabase**
   - Create a free project at [supabase.com](https://supabase.com/).
   - Create the required tables (`accounts`, `bookings`, `settings`) matching the shapes used in `script.js` (see `bookingToRow` / `rowToBooking` for the exact schema).
   - Update `SUPABASE_URL` and `SUPABASE_ANON_KEY` at the top of `script.js` with your project's values.

3. **Set your admin credentials**
   - Change `DEFAULT_ADMIN_EMAIL` and `ADMIN_PASSWORD` in `script.js` before deploying — the defaults are placeholders and are **not secure**.

4. **Run it**
   - This is a static site — no build step required. Serve the folder with any static host (GitHub Pages, Netlify, Vercel) or just open `index.html` locally.

## 🔐 Security Notes

- The Supabase **anon key** is meant to be public in client-side apps, but make sure you've configured **Row Level Security (RLS)** policies on your tables so only intended operations are allowed.
- The built-in admin password check happens client-side — treat this as a light access gate, not a full auth system. For production use with sensitive data, consider swapping in Supabase Auth.

## 📄 License

Add your preferred license here (e.g. MIT).