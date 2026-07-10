# Milestone 1 — User Authentication Module

**Infosys Springboard Internship 7.0 · Batch 1**

## 📌 What is Milestone 1?

Milestone 1 is the first deliverable of the internship project: a complete, self-contained **user authentication system** built with Streamlit and made publicly accessible from Google Colab using ngrok. It covers account creation, secure login, session handling, password recovery (via two independent methods), and a separate administrator view — all running from a single notebook.

## ✅ Features Built

- **Signup** — Username, Email, Password, Confirm Password, Security Question, Security Answer, all mandatory. Usernames and emails must be unique; duplicate signups are rejected with a clear message.
- **Login** — Accepts Username or Email + Password. On success, issues a JWT session token. On failure, shows one generic error (never reveals whether the username or the password was wrong).
- **Forgot Password (merged OTP + Security Question)** — Two independent recovery routes from the same page:
  - **Security Question route** — enter your username, answer your stored security question, set a new password.
  - **OTP route** — enter your username, the app looks up your registered email and sends a 6-digit one-time code to it via Gmail SMTP, you verify the code, then set a new password.
- **Password reuse protection** — every password ever set (at signup and at each reset) is stored as a bcrypt hash in a password-history table. Both reset routes check against this history, so a previously used password cannot be set again.
- **JWT session management** — a signed JWT is issued on login and validated before the Dashboard is shown; logging out clears the session.
- **Field & format validation** — no form submits with an empty required field; email must be shaped like `ab@cd.ef`; passwords must be at least 8 characters with an uppercase letter, a lowercase letter, a number, and a special symbol, and Confirm Password must match exactly.
- **User Dashboard** — welcome message with the logged-in username, plus a Logout action.
- **Admin Dashboard** — separate login using an admin username/password defined in code (not a signup account); shows all registered users (username, email, join date — never any password data), with a live **search** box and a **delete** button per user.
- **Secrets management** — JWT signing key, ngrok token, and Gmail credentials are never hard-coded; all are read from Google Colab Secrets at runtime.

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| UI / Frontend | Streamlit (custom neo-brutalist CSS theme) |
| Session Auth | JWT (PyJWT) |
| Password Hashing | bcrypt |
| Database | SQLite |
| Email / OTP Delivery | Gmail SMTP (smtplib) |
| Public Tunnel | ngrok (pyngrok) |
| Charts | Plotly |
| Runtime | Google Colab |

## ▶️ How to Run the Notebook

**1. Set up Colab Secrets** (key icon 🔑 in the left sidebar) — add these four, and enable notebook access for each:

| Secret Name | Value |
|---|---|
| `JWT_SECRET` | any long random string, used to sign session tokens |
| `NGROK_AUTHTOKEN` | your personal ngrok Authtoken (from the ngrok dashboard) |
| `EMAIL_ADDRESS` | the Gmail address that will send OTP emails |
| `EMAIL_PASSWORD` | a 16-character Gmail **App Password** for that address (requires 2-Step Verification enabled first) |

**2. Run the notebook cells in order:**
1. Install dependencies (`streamlit`, `streamlit-option-menu`, `pyngrok`, `pyjwt`, `bcrypt`, `plotly`).
2. Write `app.py` (contains the full authentication app).
3. Launch — starts the Streamlit server and opens a public ngrok URL.

**3. Open the printed ngrok URL** in your browser to use the app. Press Ctrl+C or the Colab Stop button to shut the server down cleanly.



