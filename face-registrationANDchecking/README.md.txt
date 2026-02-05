🤖 AI-Powered Digital Attendance System
An automated, touchless attendance solution that leverages Face Recognition via Telegram and records data directly into Google Sheets. This system eliminates manual entry and provides a seamless "Check-in" experience using facial biometrics.

🌟 Features
Dual-Mode Workflow: Separate processes for user registration and automated attendance logging.

High Precision: Utilizes the Face++ API for high-confidence facial matching (80%+ threshold).

Real-time Logging: Automatically records the name and timestamp in Google Sheets upon successful recognition.

Telegram Interface: User-friendly interaction through a Telegram Bot—no custom app required.

🛠️ Tech Stack
Automation Platform: n8n (Self-hosted or Cloud)

Communication: Telegram Bot API

Biometrics Engine: Face++ (Cognitive Services)

Database/Storage: Google Sheets (for attendance logs)

Logic: JSON & JavaScript (n8n Function nodes)

🔄 Workflow Logic
1. Registration Workflow
The goal of this workflow is to "teach" the AI who the user is.

Trigger: User sends a photo to the Telegram Bot.

Detection: The image is sent to Face++ to detect facial landmarks.

Indexing: The face is added to a specific FaceSet.

Identification: A User_ID (User's Name) is assigned to that face record for future lookups.

2. Recognition & Attendance Workflow
The daily check-in process.

Trigger: Employee/Student sends a "selfie" to the Bot.

Search: The system queries the FaceSet to find a match.

Validation: If the Confidence Score is greater than 80%:

The system identifies the user.

Action: Appends a new row to Google Sheets with the Name, Date, and Time.

Response: Telegram sends a "Attendance Marked Successfully" message.

Fallback: If the match is below 80%, the system requests a clearer photo or prompts for registration.