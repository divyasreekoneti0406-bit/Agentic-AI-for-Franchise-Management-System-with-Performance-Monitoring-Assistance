# FreightQuote AI — Milestone 2

## What Milestone 2 adds on top of Milestone 1

Milestone 1 delivered the **User Authentication module**: JWT session handling, a Streamlit UI,
SQLite-stored credentials, and Gmail-based OTP verification for password resets.

Milestone 2 unifies that security gateway with a full **multi-agent ML core** and an **LLM Copilot**,
and adds three hardening layers on top of the Milestone 1 auth system:

- **Progressive account lockout** — 3rd failed login locks the account for 5 minutes, 4th for 15
  minutes, 5th locks it permanently until an Admin unlocks it from the Admin Dashboard.
- **OTP resend rate limiting** — escalating cooldowns (60s → 3min → 5min → 1hr) on the Gmail OTP
  password-reset flow.
- **Real-time password strength checker** — 🔴 Weak (<5 chars, blocked) / 🟡 Average (5-9 chars) /
  🟢 Good (10+ chars), enforced on both Signup and Forgot Password.

On top of that hardened gateway, Milestone 2 unlocks:

- **3 autonomous ML agents** (Dynamic Pricing, Route Delay Classifier, Carrier Compliance Sentinel),
  each trained on 2 Kaggle datasets and comparing 5+ algorithms before a champion is selected.
- **An LLM Copilot** (Qwen2.5-3B-Instruct, 4-bit quantized) that answers freight-strategy questions
  and synthesizes the 3 agents' outputs into a structured JSON audit action.
- **A full Admin Dashboard** with Add User / Delete User / Unlock Account lifecycle controls and an
  ML Model Card tab showing every agent's saved training metrics.

## Tech Stack

- **Frontend:** Streamlit + streamlit-option-menu, custom navy/orange CSS theme (`ui_theme.py`)
- **Auth:** PyJWT, bcrypt, Gmail SMTP OTP (`auth.py`)
- **Database:** SQLite (`db.py`) — `users`, `password_history`, `ml_models` tables
- **ML:** scikit-learn (RandomForest, GradientBoosting, ExtraTrees, Ridge/Logistic, SVC, KNN,
  DecisionTree, AdaBoost), joblib for model persistence, kagglehub for dataset pulls
  (`train_ml_freight.py`)
- **LLM:** HuggingFace Transformers + bitsandbytes 4-bit quantization, Qwen2.5-3B-Instruct
  (`llm_engine_freight.py`)
- **Admin:** `admin_dash.py`
- **Tunnel:** pyngrok

## System Architecture

| Phase | Module | Responsibility |
|---|---|---|
| 1 — Security Gateway | `auth.py`, `db.py` | Login, Registration, Forgot Password (Gmail OTP) gate the whole app; progressive lockout state stored per-user. |
| 2 — Domain Intelligence | `train_ml_freight.py` | Agent 1: Dynamic Pricing · Agent 2: Route Delay Classifier · Agent 3: Carrier Compliance Sentinel. |
| 3 — Generative Advisory | `llm_engine_freight.py` | Qwen2.5-3B Copilot synthesizes Agents 1-3 into an executive strategy + structured JSON audit action. |
| 4 — System Administration | `admin_dash.py` | Add/Delete/Unlock users and the ML Model Card tab, restricted to `role == 'Admin'`. |

## Indian Port Coverage

| Port | Region | Specialty |
|---|---|---|
| Mumbai (JNPT) | West Coast | Container / general cargo hub |
| Mundra | West Coast (Gujarat) | India's largest private port |
| Chennai | East Coast | Automobile & container exports |
| Cochin | South-West Coast | Transshipment & spice trade |

## Colab Secrets Setup

Click the key icon (Secrets) in the left sidebar, add each of the following, and toggle
**notebook access ON** for each:

| Secret Name | Used For |
|---|---|
| `JWT_SECRET_KEY` | Signs & verifies login session tokens |
| `ADMIN_EMAIL_ID` | Bootstraps the admin account (fallback: `infosys@ai`) |
| `ADMIN_PASSWORD` | Bootstraps the admin account (fallback: `admin@123`) |
| `NGROK_AUTHTOKEN` | Public HTTPS URL for the Streamlit app |
| `HF_TOKEN` | HuggingFace auth for Qwen2.5-3B (4-bit) Copilot inference |
| `EMAIL_ID` / `EMAIL_PASSWORD` | Gmail SMTP sender for real OTP emails (optional — console fallback works without it) |
| `KAGGLE_USERNAME` / `KAGGLE_KEY` | Optional — trains agents on real Kaggle data instead of synthetic fallback |

## Kaggle API Setup (optional)

1. Log in at kaggle.com → profile picture → Settings → API → **Create New Token**.
2. This downloads a `kaggle.json` with your username and key.
3. Add both as Colab Secrets above (`KAGGLE_USERNAME`, `KAGGLE_KEY`).
4. The notebook works fine without this — it falls back to a seeded synthetic data generator.

## How to Run

1. Runtime → Change runtime type → **T4 GPU** → Save.
2. Run the `!nvidia-smi` cell to confirm the GPU is attached.
3. Add the Colab Secrets above.
4. Run all cells top to bottom: installs → module files → secrets → (optional Kaggle setup) →
   train all 3 agents → launch (Streamlit + ngrok).
5. Open the printed public HTTPS URL, log in with `ADMIN_EMAIL_ID` / `ADMIN_PASSWORD`, and explore
   Home → Agent 1/2/3 → AI Copilot → Admin Dashboard.

## Screenshots

_See `screenshots/` for: Home page, AI Copilot (prompt + response), ML Pricing Calculator,
Admin Panel → ML Model Card, Admin Panel → Add/Delete/Unlock user actions, a triggered lockout
message, and an OTP cooldown message._
