# 🤖 AI-Powered Digital Attendance System

An automated, touchless attendance solution that leverages **Facial Recognition** via Telegram and records data directly into Google Sheets. This system eliminates manual entry and provides a seamless "Check-in" experience using facial biometrics.

---

## 🌟 Features
* **Dual-Mode Workflow:** Separate logic streams for user registration and automated attendance logging.
* **High Precision:** Utilizes the Face++ API for high-confidence facial matching (80%+ threshold).
* **Real-time Logging:** Automatically records the name and timestamp in Google Sheets upon successful recognition.
* **Telegram Interface:** User-friendly interaction through a Telegram Bot—no custom app installation required.

## 🛠️ Tech Stack
* **Automation Platform:** [n8n](https://n8n.io/) (Self-hosted or Cloud)
* **Communication:** Telegram Bot API
* **Biometrics Engine:** Face++ (Cognitive Services)
* **Storage:** Google Sheets (Centralized attendance logs)
* **Logic:** JSON & JavaScript (n8n Function nodes)

---

## 🔄 Workflow Logic

### 1. Registration Workflow
The goal of this workflow is to "teach" the AI who the user is.
1. **Trigger:** User sends a photo to the Telegram Bot.
2. **Detection:** The image is sent to Face++ to detect facial landmarks.
3. **Indexing:** The face is added to a specific **FaceSet**.
4. **Identification:** A `User_ID` (User's Name) is assigned to that face record for future lookups.

### 2. Recognition & Attendance Workflow
The daily check-in process.
1. **Trigger:** Employee/Student sends a "selfie" to the Bot.
2. **Search:** The system queries the FaceSet to find a match.
3. **Validation:** If the **Confidence Score** is $\ge 80\%$:
    * The system identifies the user.
    * **Action:** Appends a new row to Google Sheets with Name, Date, and Time.
    * **Response:** Telegram sends an "Attendance Marked Successfully" confirmation.
4. **Fallback:** If the match is $< 80\%$, the system requests a clearer photo or prompts for registration.

---

## 🛡️ Privacy & Production Note
This repository contains the architecture and workflow configurations. To ensure security:
* Environment variables and API keys are stored in n8n credentials.
* The Google Sheet is private and accessible only via Service Account.
