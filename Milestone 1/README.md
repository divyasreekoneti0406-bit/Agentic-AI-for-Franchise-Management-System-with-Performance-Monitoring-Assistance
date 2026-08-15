# Milestone 1 — User Authentication Module

---
## 🎯 Objectives

The main objectives of Milestone 1 are:

* Build a complete user authentication system.
* Implement Login and Signup functionality.
* Implement Forgot Password using Security Question and Email OTP.
* Use JWT for secure session management.
* Add mandatory-field and password validation.
* Provide separate User and Admin Dashboards.
* Secure sensitive credentials using Colab Secrets.
* Make the Streamlit application publicly accessible using ngrok.

---

## ✨ Features Implemented

### 1. Login Page

The Login page allows registered users to log in using:

* Username/Email
* Password

Features include:

* Mandatory field validation.
* Generic error message for invalid credentials.
* JWT token generation after successful login.
* Redirect to the User Dashboard after successful authentication.

---

### 2. Signup Page

New users can create an account by providing:

* Username
* Email
* Password
* Confirm Password
* Security Question
* Security Answer

Validation includes:

* All fields are mandatory.
* Username must be unique.
* Email format validation.
* Password strength validation.
* Confirm Password must match Password.

The security question and answer are stored for use during password recovery.

---

### 3. Forgot Password

The Forgot Password page provides two recovery methods.

#### 🔐 Security Question Recovery

The user can:

1. Enter their username.
2. Answer the security question created during signup.
3. Verify the answer.
4. Create a new password.

#### 📧 OTP Recovery

The user can:

1. Enter their registered email address.
2. Receive a one-time password (OTP) through email.
3. Enter and verify the OTP.
4. Create a new password.

Both recovery methods follow the same password validation rules.

---

### 4. JWT Session Management

JSON Web Tokens (JWT) are used to manage authenticated user sessions.

After successful login:

* A JWT session token is generated.
* The token is stored in Streamlit session state.
* The token is validated before displaying the Dashboard.
* Logout clears the active session.
* Users must log in again to receive a fresh JWT.

---

### 5. User Dashboard

After successful authentication, users are redirected to the Dashboard.

The Dashboard displays:

* Welcome message.
* Logged-in username/email.
* Logout option.

The Logout option clears the session and returns the user to the Login page.

---

### 6. Admin Dashboard

The application contains a separate Admin Dashboard.

The Admin account is defined directly in the application code and is separate from normal user signup.

After successful Admin login, the Admin can view:

* Registered usernames.
* Registered email addresses.

**Password information is never displayed in the Admin Dashboard.**

---

## ✅ Validation Rules

### Mandatory Fields

All required fields in Login, Signup, and Forgot Password forms must be completed before submission.

### Email Validation

The email must follow the required format, with:

* At least 2 letters before `@`.
* At least 2 letters between `@` and the final dot.
* At least 2 letters after the final dot.

### Password Validation

Passwords must contain:

* Minimum 8 characters.
* At least one uppercase letter.
* At least one lowercase letter.
* At least one number.
* At least one special character.

The Confirm Password field must exactly match the Password field.

---

## 🛠️ Technology Stack

| Technology           | Purpose                               |
| -------------------- | ------------------------------------- |
| Python               | Application development               |
| Streamlit            | Web application and UI                |
| JWT                  | Session authentication                |
| Google Colab         | Development and execution environment |
| ngrok                | Public URL/tunneling                  |
| Gmail SMTP           | OTP email delivery                    |
| Google Colab Secrets | Secure credential storage             |

---

## 🔐 Security Configuration

Sensitive information is **not hard-coded** in the notebook.

The following values are stored using Google Colab Secrets:

| Secret Name       | Purpose                            |
| ----------------- | ---------------------------------- |
| `JWT_SECRET`      | Signing JWT session tokens         |
| `NGROK_AUTHTOKEN` | Authentication for ngrok           |
| `EMAIL_PASSWORD`  | Gmail App Password for sending OTP |
| `EMAIL_ADDRESS`   | Gmail account used to send OTP     |

Notebook access is enabled for these secrets so that the application can securely retrieve them at runtime.

---

## 📧 Gmail OTP Configuration

The application uses a Gmail App Password to send OTP emails for password recovery.

A Gmail account with **2-Step Verification enabled** is required before creating the App Password.

The Gmail credentials are stored securely in Colab Secrets:

* `EMAIL_ADDRESS`
* `EMAIL_PASSWORD`

The actual email password is never stored in the repository.

---

## 📁 Project Structure

```text
Infosys Repository/
│
└── Milestone1/
    │
    ├── README.md
    ├── FranchiseOps_AI_Milestone1.ipynb
    │
    └── screenshots/
        ├── login.png
        ├── signup.png
        ├── forgot_password_security.png
        ├── forgot_password_otp.png
        ├── otp_email.png
        ├── user_dashboard.png
        └── admin_dashboard.png
```

---

## 📸 Screenshots

### Login Page

<img width="939" height="416" alt="Screenshot 2026-08-12 123342" src="https://github.com/user-attachments/assets/03b46ffb-06ea-44cd-bbb5-523b43223bb9" />

### Signup Page

<img width="935" height="414" alt="Screenshot 2026-08-12 121822" src="https://github.com/user-attachments/assets/3fa0c826-b1c7-40a9-8e95-3c9be3683f8d" />

<img width="938" height="413" alt="Screenshot 2026-08-12 121845" src="https://github.com/user-attachments/assets/b8c2f82c-bb81-453c-9449-b0ddb1496cf5" />

### Forgot Password — Security Question

<img width="943" height="423" alt="Screenshot 2026-08-12 125838" src="https://github.com/user-attachments/assets/b53d5299-a6bb-4003-a9cb-301c9175c05a" />


### Forgot Password — OTP

<img width="917" height="402" alt="Screenshot 2026-08-12 123623" src="https://github.com/user-attachments/assets/6d25225b-9e63-4287-ac06-184b578c09fc" />

### User Dashboard

<img width="935" height="424" alt="Screenshot 2026-08-12 122014" src="https://github.com/user-attachments/assets/022506c3-72ec-4b35-a787-5c2f458ee00b" />

### Admin Dashboard

<img width="941" height="425" alt="Screenshot 2026-08-12 121718" src="https://github.com/user-attachments/assets/0eefad66-1259-414e-a8a2-608978414cc3" />

## 🔍 Security Checklist

Before uploading the notebook to GitHub:
* Remove all hard-coded email addresses where applicable.
* Remove Gmail App Passwords.
* Remove ngrok authentication tokens.
* Remove JWT secrets.
* Remove Admin passwords if they were accidentally hard-coded outside the intended configuration.
* Clear all notebook outputs.
* Make sure no OTPs or private credentials are visible.
* Confirm that sensitive values are retrieved only through Colab Secrets.

## ✅ Milestone 1 Completion Checklist

* [x] Infosys Repository created
* [x] `Milestone1` folder created
* [x] README.md added
* [x] Login page implemented
* [x] Signup page implemented
* [x] Forgot Password — Security Question implemented
* [x] Forgot Password — OTP implemented
* [x] JWT session management implemented
* [x] User Dashboard implemented
* [x] Admin Dashboard implemented
* [x] Mandatory-field validation implemented
* [x] Email validation implemented
* [x] Password validation implemented
* [x] ngrok configured
* [x] Gmail App Password configured
* [x] Colab Secrets configured
* [x] Screenshots added
* [x] Sensitive information removed before repository upload


## 🏁 Conclusion

Milestone 1 successfully implements a complete authentication gateway using **Streamlit, JWT, ngrok, Gmail OTP, and Google Colab Secrets**. The module provides secure user registration, authentication, password recovery, session management, and separate user and administrator dashboards while keeping sensitive credentials protected.

