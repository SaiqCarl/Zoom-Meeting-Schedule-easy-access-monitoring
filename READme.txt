# Zoom Meeting Scheduler

A modern web-based Zoom Meeting Scheduler designed for organizations to manage meeting room reservations, Zoom account assignments, and scheduling approvals through an intuitive user interface and administrator dashboard.

The application is deployed using **GitHub**, **Vercel**, and **Supabase**, providing a secure, scalable, and production-ready solution for managing Zoom meeting reservations.

---

##  Features

### User Portal

- View Zoom room availability
- Interactive monthly calendar
- AM / PM booking visualization
- Submit booking requests
- Recurring meeting scheduling
- Existing booking viewer
- Booking window restrictions
- Weekend booking prevention
- Responsive design
- Light / Dark mode

---

### Admin Panel

- Secure administrator login
- Booking request management
- Approve or deny reservations
- Booking statistics dashboard
- Zoom account management
- Zoom license expiration tracking
- Room capacity management
- Excel report export
- Automatic email notifications
- Automatic account expiration detection

---

##  Booking Features

- One-time reservations
- Daily recurring meetings
- Weekly recurring meetings
- Monthly recurring meetings
- AM Shift (07:00–12:00)
- PM Shift (13:00–18:00)
- Whole-day reservations
- Automatic conflict detection
- Visual booking indicators

### Calendar Legend

| Color | Meaning |
|--------|----------|
|  Green | Available |
|  Yellow | Partially Booked / Pending |
|  Red | Fully Booked |
|  Blue Border | Recurring Meeting |

---

##  Zoom Account Management

Administrators can:

- Create Zoom accounts
- Edit Zoom accounts
- Delete Zoom accounts
- Assign room capacities
- Track license expiration dates
- Automatically deactivate expired licenses
- Warn users when a Zoom license is nearing expiration

---

## 📊 Admin Dashboard

The administrator dashboard provides:

- Total booking requests
- Pending approvals
- Approved bookings
- Denied bookings
- Booking details
- Search and filtering
- Excel export
- Zoom account monitoring

---

##  Project Structure

```
Zoom-Meeting-Scheduler/
│
├── index.html
├── styles.css
├── script.js
├── DICT.png
├── README.md
│
└── supabase/
    ├── migrations/
    ├── functions/
    │   ├── send-booking-email/
    │   ├── send-approval-email/
    │   ├── send-denial-email/
    │   ├── send-license-warning/
    │   └── weekly-report/
    └── config.toml
```

---

##  Technology Stack

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript

### Backend

- Supabase

### Hosting

- Vercel

### Database

- PostgreSQL (Supabase)

### Authentication

- Supabase Auth *(future implementation)*

### Email Notifications

- Supabase Edge Functions
- Resend Email API *(recommended)*

### Data Export

- SheetJS (XLSX)

### Version Control

- GitHub

---

##  Deployment

The project follows the following deployment workflow:

```
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Vercel Deployment
    │
    ▼
Supabase Backend
    │
    ├── PostgreSQL Database
    ├── Edge Functions
    ├── Storage
    └── Authentication
```

### Deployment Process

1. Develop locally.
2. Commit and push changes to GitHub.
3. Import the repository into Vercel.
4. Connect the project to Supabase.
5. Configure the required environment variables.
6. Deploy.

Every commit pushed to the **main** branch automatically triggers a new deployment through Vercel.

---

##  Database

The production version stores all application data in **Supabase PostgreSQL**.

Tables include:

- Bookings
- Zoom Accounts
- Administrator Settings
- Room Availability
- License Expiration Information

---

##  Email Notification System

Email notifications are handled entirely through **Supabase Edge Functions**, eliminating the need for client-side email services.

### Booking Workflow

```
User
│
▼
Submit Booking Request
│
▼
Supabase Database
│
▼
Supabase Edge Function
│
▼
Email Service (Resend)
│
▼
Administrator receives notification
```

### Approval Workflow

```
Administrator
│
▼
Approve / Deny Booking
│
▼
Supabase Database
│
▼
Supabase Edge Function
│
▼
Requester receives email notification
```

### Scheduled Notifications

The system can also automatically send:

- Zoom license expiration reminders
- Daily booking summaries
- Weekly booking reports
- Administrative notifications

---

##  Security

Unlike traditional client-side email solutions, all emails are sent from the server through Supabase Edge Functions.

Benefits include:

- No public API keys
- Secure server-side processing
- Better scalability
- Easier maintenance
- More reliable email delivery
- Support for HTML emails and attachments

---

##  Production Architecture

```
                        Users
                          │
                          ▼
                Zoom Meeting Scheduler
                     (Vercel Hosting)
                          │
                          ▼
                     Supabase Backend
           ┌──────────────┼──────────────┐
           │              │              │
           ▼              ▼              ▼
     PostgreSQL      Edge Functions    Storage
           │              │
           │              ▼
           │        Resend Email API
           │              │
           └──────────────▼
                   Email Notifications
```

---

##  Future Improvements

- Supabase Authentication
- Multi-admin roles
- Google Calendar integration
- Zoom API integration
- Automatic Zoom meeting creation
- Audit logging
- Real-time updates
- Dashboard analytics
- SMS notifications

---

##  Screenshots

Add screenshots after deployment.

```
screenshots/

homepage.png
calendar.png
booking-form.png
admin-dashboard.png
zoom-accounts.png
```

---

##  Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push to GitHub.
5. Open a Pull Request.

---

##  License

This project is intended for educational, organizational, and scheduling purposes.

Feel free to modify and extend it to suit your organization's requirements.

---

##  Author

**SaiqCarl**

Computer Engineering Student  
University of Batangas

Built as a modern Zoom Meeting Reservation System powered by **GitHub**, **Vercel**, and **Supabase**.