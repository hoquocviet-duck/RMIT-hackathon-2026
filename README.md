# MedTide Vault — Zero-Knowledge Electronic Health Records with TideCloak

> **Official Submission for RMIT Hackathon 2026 - Challenge 2**  
> **Challenge Topic:** Vibe code a working app with TideCloak  
> **Team Name:** RMIT_HNI_ARGON4  
---

## 1. Overview & Problem Statement
Traditional Electronic Health Record (EHR) systems store sensitive patient diagnoses and prescriptions in centralized databases. If the database is breached—or if a curious Database Administrator / Compliance Auditor inspects the tables—private medical histories are immediately exposed in plaintext.

**MedTide Vault** solves this problem using **TideCloak** (Decentralized Identity and Access Management):
* **Patient-Owned Decryption Consent (RBAC):** Patients hold ultimate authority over their medical records and can dynamically grant or revoke decryption access for doctors in real-time.
* **Zero-Knowledge Auditing:** Compliance auditors and system administrators can monitor cryptographic access logs without ever having the decryption keys required to view sensitive medical plaintext.
* **Decentralized SSO:** Seamless authentication and role management powered by TideCloak realms and JWT tokens.

---

## 2. Key Features
1. **TideCloak SSO Authentication:** Connect to a local or remote TideCloak node (`http://localhost:8080`) with realm configuration (`medtide-prod`).
2. **Real-Time Role Switcher (RBAC):** Easily test and verify permissions across three distinct TideCloak roles:
   * **`patient`:** View decrypted personal medical records and toggle doctor consent (**Grant / Revoke Access**).
   * **`doctor`:** View patient records and create new signed & encrypted diagnoses/prescriptions (only when patient consent is active).
   * **`auditor`:** Inspect live IAM security logs while medical records remain strictly locked as ciphertext (`[ACCESS DENIED BY TIDECLOAK POLICY]`).
3. **JWT Token Inspector:** Built-in modal to inspect the decoded TideCloak JWT payload, active roles, and DKG encryption key metadata (`secp256k1`).
4. **Live Cryptographic Audit Trail:** Real-time logging of every authentication, role switch, record creation, and consent revocation event.

---

## 3. Tech Stack & Project Structure
* **Frontend:** HTML5, Tailwind CSS, Vanilla JavaScript (ES6+), Lucide Icons.
* **Backend / IAM:** Node.js / Express API & TideCloak Docker Container (`tideorg/tidecloak-dev:latest`).

```text
medtide-vault/
├── index.html          # Main Single-Page Application (SPA) UI
├── style.css           # Custom styling and dark-mode theme
├── script.js           # Application state, RBAC logic, and TideCloak handlers
├── docker-compose.yml  # TideCloak container configuration
├── demo-video.mp4      # Screen recording of the working application
└── README.md           # Project documentation
