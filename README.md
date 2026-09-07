# 🏛️ RapidResolve - Grievance & Crime Management Portal

**RapidResolve** is a modular, console-based Citizen Grievance Redressal and Crime Management System built using **Core Java**, **JDBC**, and **MySQL**. It streamlines complaint registration, automated officer assignment, crime reporting, real-time QR code generation, and automated email credential dispatch.

---

## 🚀 Key Features

### 👤 1. Citizen Portal
* **Secure Registration & OTP Verification:** Sign up with profile details and an OTP verification flow, protected by an account lockout tracker (locks account for 5 minutes after 3 failed attempts).
* **Complaint Filing:** File complaints by area and category with automatic assignment to the least-busy officer.
* **In-Memory Sorted Dashboard:** In-memory Binary Search Tree (`ComplaintBST`) with in-order traversal for fast and sorted complaint retrieval.
* **Dynamic QR Code Generation:** Real-time generation of scannable PNG QR codes containing complaint summaries and citizen profile cards using **Google ZXing**.
* **Additional Services:** Emergency helpline lookup, suggestion box, feedback rating, and FAQ section.

### 👮 2. Officer Dashboard
* **First-Time Login Security:** Mandatory temporary password change on first login.
* **Case Management:** View assigned complaints and update complaint statuses (`NEW`, `OPEN`, `RESOLVED`, `CLOSED`).
* **Crime Logging:** Record and view FIRs/crime records directly using MySQL Stored Procedures.
* **Personal Reports:** Generate and export personal case summary reports to formatted `.txt` files.

### 🛡️ 3. Admin Control Center
* **Centralized Oversight:** View all system complaints, crime records, and citizen profiles.
* **Automated Officer Onboarding:** Add officers with auto-generated secure passwords, automatically delivered via **JavaMail API (SMTP)** to their email.
* **Audit Logging:** Database-backed system activity logging (`ActionTracker`) for all critical user actions.
* **Archival & Cleanup:** Transactionally archive resolved/closed complaints older than 1 year to dated `.txt` files and clean up database records.
* **Analytics:** View real-time feedback ratings, resolution statistics, and complaint distribution.

---

## 🛠️ Tech Stack & Libraries

| Category | Technologies / Libraries Used |
| :--- | :--- |
| **Language** | Java (JDK 8+, OOP Architecture) |
| **Database** | MySQL, JDBC (`mysql-connector-j`) |
| **Database Logic** | PreparedStatements, ACID Transactions (`commit`/`rollback`), Stored Procedures (`CallableStatement`) |
| **QR Code Generation** | Google ZXing (`core-3.5.2.jar`, `javase-3.5.2.jar`) |
| **Email Service** | JavaMail API (`javax.mail-1.6.2.jar`, `activation-1.1.1.jar`) via Gmail SMTP |
| **Security** | SHA-256 Cryptographic Hashing (`MessageDigest`), OTP Rate-Limiting (`Deque`) |
| **UI / UX** | Interactive CLI with ANSI color codes, ASCII art banner, and regex validation |

---

## 📂 Project Architecture

```plaintext
RapidResolve/
├── ActionTracker.java        # Centralized audit logging to database
├── Admin.java                # Admin dashboard and administrative operations
├── AdminManager.java         # Admin authentication and retrieval
├── CLIUtils.java             # Terminal styling, menus, input prompts, regex validation
├── Citizen.java              # Citizen user actions and menu workflows
├── Complaint.java            # Complaint model class
├── ComplaintBST.java         # Custom Binary Search Tree for sorted complaints
├── ComplaintManager.java     # Complaint filing, auto-assignment & lifecycle management
├── Crime.java                # Crime record model class
├── CrimeManager.java         # Stored procedure execution for crime logging
├── DBConnection.java         # Centralized JDBC connection & execution helper
├── HashingForPassword.java   # SHA-256 password hashing & migration utility
├── MainApplication.java      # Application entry point & login/signup router
├── OTPAttemptTracker.java    # Sliding-window rate limiter for OTP attempts
├── Officer.java              # Police officer model and dashboard
├── OfficerManager.java       # Officer credentials, auto-assignment & email sender
├── QRGenerator.java          # ZXing integration for generating QR code PNGs
├── ReportGenerator.java      # Automated .txt report generation and archival
├── User.java                 # Base class for User entities (OOP Inheritance)
└── UserManager.java          # Citizen profile CRUD & authentication
