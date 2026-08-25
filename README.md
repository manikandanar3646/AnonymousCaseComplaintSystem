# 🛡️ Anonymous Complaint Reporting System

An **AI-powered anonymous complaint reporting system** designed to provide a secure and confidential platform for reporting sensitive incidents such as **child abuse, domestic violence, sexual harassment, corruption, and misconduct** without requiring users to reveal their personal identity.

The system combines **Natural Language Processing (NLP), DistilBERT-based sentiment analysis, location services, complaint tracking, and automated email communication** to make complaint reporting easier, faster, and more accessible.

---

## 👥 Contributors

- **Mugesh Kumar .K**
- **Manikandan .AR** 
- **Nandha Kishore .R** 
- **Kavin prasanth .M** 

---

## 📌 Project Overview

Many victims hesitate to report abuse or harassment because of **fear, social stigma, intimidation, emotional trauma, or pressure from family members**.

Traditional reporting methods often require victims to directly approach authorities or provide personal information. This project proposes an anonymous digital alternative where users can submit complaints through:

* 🤖 **AI Chatbot**
* 📝 **Anonymous Complaint Form**

The submitted complaint is processed by the Flask backend and analyzed using a **DistilBERT NLP model**. Based on the classification result, the system can provide emergency-support guidance, register the complaint, generate an anonymous reference ID, and forward complaint information to the appropriate authority.

---

## 🎯 Objectives

* Provide a **confidential and anonymous** complaint reporting platform.
* Allow victims to report incidents without directly approaching authorities.
* Use **NLP and AI** to analyze complaint text.
* Detect emotionally distressing or potentially urgent complaints.
* Provide immediate emergency-support guidance when appropriate.
* Automatically forward complaints to the concerned authority.
* Generate a **unique anonymous Reference ID** for tracking.
* Provide a simple interface suitable for users under stressful situations.

---

## ✨ Key Features

### 🤖 1. AI Chatbot Complaint Collection

Users can describe their incident naturally through a chatbot interface.

The chatbot:

* Collects complaint information conversationally.
* Accepts natural-language descriptions.
* Sends complaint text to the Flask backend.
* Uses NLP processing for analysis.
* Performs DistilBERT-based sentiment classification.
* Provides appropriate feedback based on the analysis.

---

### 📝 2. Anonymous Complaint Form

Users can directly submit complaints through a predefined form.

The form can include:

* Incident category
* Location
* Complaint description
* Evidence attachments
* Other relevant incident details

No unnecessary personal identification is required for anonymous reporting.

---

### 🧠 3. DistilBERT-Based Text Analysis

The system uses **DistilBERT**, a lightweight Transformer-based NLP model derived from BERT.

The model analyzes complaint text and performs sentiment/emotional classification.

The resulting classification is used as **one input to the system's severity/urgency decision process**.

> **Note:** Sentiment analysis should not be treated as a standalone determination of whether a situation is an emergency. Real-world deployment should combine model predictions with contextual/risk indicators and appropriate human review.

---

### 🚨 4. Emergency Support

When the system identifies indicators of a potentially critical situation, it can display relevant emergency-support information to the user.

This provides immediate guidance instead of requiring the user to navigate away from the platform.

---

### 📍 5. Location-Based Authority Routing

Google APIs are used for location-related functionality.

The system can use the submitted location to help determine the appropriate local authority for handling the complaint.

---

### 📧 6. Automated Email Communication

**EmailJS** is used to send complaint information to the designated authority.

This reduces the need for manual forwarding of complaints.

---

### 🗄️ 7. Complaint Database

**MySQL** is used to store complaint-related records.

The database can maintain information such as:

* Complaint ID
* Complaint category
* Complaint description
* Location
* Classification result
* Severity/priority
* Complaint status
* Submission information

Sensitive data should be protected using appropriate access controls and security practices in production.

---

### 🔎 8. Anonymous Complaint Tracking

After submitting a complaint, the user receives a **unique anonymous Reference ID**.

The Reference ID can be used to check the status of the complaint without requiring the user to create a conventional personal account.

---

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │        User         │
                    └──────────┬──────────┘
                               │
                     ┌─────────▼─────────┐
                     │   Web Interface   │
                     │ HTML/CSS/JavaScript│
                     └─────────┬─────────┘
                               │
                  ┌────────────▼────────────┐
                  │      Flask Backend      │
                  │         Python          │
                  └────────────┬────────────┘
                               │
                     ┌─────────▼─────────┐
                     │   NLP Processing  │
                     │     DistilBERT    │
                     └─────────┬─────────┘
                               │
                    ┌──────────▼──────────┐
                    │ Severity / Decision │
                    │      Processing      │
                    └───────┬───────┬──────┘
                            │       │
              ┌─────────────┘       └─────────────┐
              │                                   │
      ┌───────▼────────┐                  ┌───────▼────────┐
      │   MySQL DB     │                  │ Emergency      │
      │ Complaint Data │                  │ Support Guide  │
      └───────┬────────┘                  └────────────────┘
              │
      ┌───────▼─────────┐
      │ Complaint        │
      │ Tracking System  │
      └──────────────────┘

              External Services
              ─────────────────
              Google APIs → Location Services
              EmailJS     → Authority Notifications
```

---

## 🔄 Data Flow

```text
Complaint Input
      │
      ├── Chatbot
      │
      └── Complaint Form
              │
              ▼
       Flask Backend
              │
              ▼
        NLP Processing
              │
              ▼
          DistilBERT
              │
              ▼
      Sentiment / Emotion
          Classification
              │
              ▼
      Severity / Decision
          ┌────┴────┐
          │         │
       Normal    Critical
          │         │
          ▼         ▼
      Register   Emergency
      Complaint   Guidance
          │
          ▼
       MySQL
          │
          ├── Reference ID
          │
          └── Status Tracking
          
          └──────► EmailJS
                       │
                       ▼
                   Authority
```

---

## 📦 System Modules

### Module 1 — Template-Based Complaint Collection

Provides a structured complaint form where users can select an incident category, provide details, optionally attach evidence, and submit the complaint anonymously.

A unique Reference ID is generated after successful submission.

### Module 2 — Chatbot-Based Complaint Collection

Provides a conversational interface for users who prefer explaining their incident naturally instead of completing a structured form.

### Module 3 — DistilBERT Classification

Processes complaint text using a DistilBERT-based NLP model to classify its emotional/sentiment characteristics.

### Module 4 — Complaint Decision & Tracking

Uses the analysis along with the application's decision logic to determine the appropriate workflow, register the complaint, generate a Reference ID, and support complaint-status tracking.

### Module 5 — Authority Communication

Uses EmailJS and location-related services to help forward complaint information to the appropriate authority.

---

## 🛠️ Technology Stack

| Category                | Technology                          |
| ----------------------- | ----------------------------------- |
| Frontend                | HTML, CSS, JavaScript               |
| Backend                 | Python, Flask                       |
| AI / NLP                | NLP, DistilBERT, Sentiment Analysis |
| Database                | MySQL                               |
| Location Services       | Google APIs                         |
| Email Communication     | EmailJS                             |
| Development Environment | Visual Studio Code                  |
| Version Control         | Git / GitHub                        |

---

## 📁 Suggested Project Structure

```text
anonymous-complaint-system/
│
├── app.py
│
├── requirements.txt
│
├── models/
│   └── distilbert/
│
├── templates/
│   ├── index.html
│   ├── chatbot.html
│   ├── complaint.html
│   └── tracking.html
│
├── static/
│   ├── css/
│   │   └── style.css
│   │
│   └── js/
│       ├── chatbot.js
│       ├── complaint.js
│       └── tracking.js
│
├── database/
│   └── schema.sql
│
├── uploads/
│
└── README.md
```

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/anonymous-complaint-system.git
cd anonymous-complaint-system
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

### 3. Activate the Environment

**Windows:**

```bash
venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure Environment Variables

Create a `.env` file and configure the required credentials.

```env
MYSQL_HOST=localhost
MYSQL_USER=your_username
MYSQL_PASSWORD=your_password
MYSQL_DATABASE=anonymous_complaints

EMAILJS_SERVICE_ID=your_service_id
EMAILJS_TEMPLATE_ID=your_template_id
EMAILJS_PUBLIC_KEY=your_public_key

GOOGLE_API_KEY=your_google_api_key
```

> Never commit API keys, database passwords, or other secrets to GitHub.

### 6. Configure MySQL

Create the required database and execute the SQL schema.

```sql
CREATE DATABASE anonymous_complaints;
```

Then configure the database credentials in the application's environment configuration.

### 7. Run the Flask Application

```bash
python app.py
```

The application will be available locally through the Flask development server.

---

## 🧪 Example Workflow

### Normal Complaint

```text
User submits complaint
        ↓
Flask receives complaint
        ↓
NLP preprocessing
        ↓
DistilBERT classification
        ↓
Complaint registered
        ↓
Reference ID generated
        ↓
Authority notification
        ↓
User tracks complaint
```

### Potentially Critical Complaint

```text
User submits complaint
        ↓
Flask receives complaint
        ↓
NLP + DistilBERT analysis
        ↓
Risk/urgency assessment
        ↓
Emergency-support guidance
        ↓
Complaint processing
        ↓
Authority notification
        ↓
Reference ID generated
```

---

## 🔐 Privacy & Security

Privacy is a core design consideration of this project.

The system is designed to:

* Avoid unnecessary collection of personally identifying information.
* Provide anonymous complaint submission.
* Use a Reference ID instead of requiring a conventional user account.
* Protect database credentials through environment variables.
* Restrict access to sensitive complaint information.
* Avoid exposing confidential complaint details through the frontend.

For a real-world deployment, additional security measures would be required, including:

* HTTPS/TLS
* Encryption at rest
* Secure authentication for authorities
* Role-based access control
* Secure file upload validation
* Audit logging
* Data retention policies
* Protection against SQL injection and XSS
* Secure API-key management
* Privacy and legal compliance
* Human review for high-risk cases

---

## ⚠️ Important Disclaimer

This project is an **academic/research prototype** and should not be considered a replacement for police, emergency, medical, legal, or professional support services.

AI-based sentiment or emotion classification can produce incorrect results, particularly with sarcasm, ambiguous language, multilingual text, or complex descriptions. Therefore, an AI prediction should **not be the sole basis for determining whether a person is in immediate danger**.

---

## 📚 Research

The project is based on research related to:

* BERT
* DistilBERT
* Natural Language Processing
* Sentiment Analysis
* Anonymous Reporting Systems
* AI-based Complaint Classification
* Secure Web-Based Complaint Management

### Key References

**Devlin et al. (2018)** — BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.

**Sanh et al. (2019)** — DistilBERT: A Distilled Version of BERT, a smaller and faster Transformer model.

Additional literature was reviewed on anonymous reporting systems, NLP-based sentiment analysis, and secure complaint management.

---

## 📊 Future Enhancements

* Multilingual complaint processing
* Voice-based complaint submission
* Advanced emotion classification
* Explainable AI for complaint classification
* Human-in-the-loop authority verification
* Encrypted evidence storage
* Secure authority dashboard
* Real-time complaint notifications
* Improved risk/urgency classification
* Mobile application
* Integration with officially authorized emergency and government services

---

## 👨‍💻 Project

**Anonymous Complaint Reporting System Using DistilBERT-Based Emotional Analysis**

Built as an **AI/NLP academic and research project** combining web development, machine learning, database management, and external APIs.

**Technologies:** Python • Flask • HTML • CSS • JavaScript • NLP • DistilBERT • MySQL • Google APIs • EmailJS • GitHub
