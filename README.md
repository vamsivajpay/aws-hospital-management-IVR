# 🏥  Hospital Management IVR System – Powered by AWS

A cloud-native, voice-enabled contact center solution for hospitals, built using Amazon Connect and integrated with AWS Lex, Lambda, DynamoDB, and other AWS services. This system allows patients to interact with hospital services through natural language—enabling appointment booking, billing inquiries, emergency routing, voicemail, and callback options—all orchestrated through serverless automation and dynamic voice flows.

---

## 🎯 Key Capabilities

### 🧠 Conversational AI with Amazon Lex
- Detects patient intent (e.g., appointments, billing, emergencies, general inquiries).
- Supports fallback handling and intent clarification for seamless interaction.

### 🔁 Modular IVR Flow Design
- Built using Amazon Connect contact flows.
- Includes reusable logic blocks for routing, working hours, queue overflow, and voicemail.

### 📦 Dynamic Prompt Management via DynamoDB
- All IVR messages are stored in a DynamoDB table.
- A single Lambda function retrieves SSML prompts dynamically using `Namespace: External` and a key.
- Enables multilingual support and real-time updates without modifying flows.

### 📞 Smart Queue & Callback Handling
- Patients are routed to appropriate queues based on intent.
- If wait times exceed a threshold, the system offers a callback option to reduce hold time.

### 📨 Voicemail Support
- Patients can leave voicemails during off-hours or when queues are full.
- Two Lambda functions manage voicemail recording and processing, with optional transcription and sentiment analysis.

---

## 🧱 System Architecture

| Component           | Role                                                                 |
|--------------------|----------------------------------------------------------------------|
| **Amazon Connect**  | Hosts the IVR, manages call routing, queues, and prompt playback     |
| **Amazon Lex V2**   | Captures patient intent using natural language                       |
| **AWS Lambda**      | Executes logic for prompt retrieval and voicemail handling           |
| **Amazon DynamoDB** | Stores SSML prompt templates and configuration data                  |
| **Amazon S3**       | (Optional) Stores voicemail recordings                               |
| **Amazon Transcribe** | Converts voicemail audio to text                                  |
| **Amazon Comprehend** | Analyzes sentiment and extracts key phrases from transcripts      |
| **Amazon CloudWatch** | Logs and monitors Lambda executions                               |

---

## 🔧 How It Works

### 1. 📞 Patient Call Initiation
- Patient calls the hospital’s Amazon Connect number.
- Lex bot engages and captures the intent (e.g., “book an appointment”, “talk to billing”).

### 2. 🔀 Intent-Based Routing
- Based on the matched intent, the system routes the call to the appropriate queue.
- Includes logic for working hours and queue capacity.

### 3. 🗣️ Dynamic Prompt Playback
- At each prompt block, the system uses a dynamic key to fetch the SSML message from DynamoDB.
- Lambda returns the message, which is rendered using Amazon Polly.

### 4. 📲 Callback Option
- If the patient waits too long in a queue, they are offered a callback.
- The system captures their number and schedules a return call.

### 5. 📨 Voicemail Handling
- If voicemail is selected, the system records the message.
- Lambda functions manage storage (optional via S3), transcription (via Transcribe), and sentiment analysis (via Comprehend).

---


---

## 🚀 Deployment Guide

### 1. Amazon Connect
- Import both contact flow JSON files.
- Create queues: `appointments`, `billing`, `emergency`, `general`.
- Upload prompts and configure whisper flows if needed.

### 2. AWS Lex V2
- Deploy the `hospital-management` bot.
- Define intents: `appointmentIntent`, `billingIntent`, `emergencyIntent`, `FallbackIntent`.

### 3. AWS Lambda
- Deploy three functions:
  - `fetch-prompts-handler`: Retrieves SSML from DynamoDB.
  - `voicemail-recorder`: Handles voicemail recording logic.
  - `voicemail-processor`: Transcribes and analyzes voicemail content.

### 4. DynamoDB
- Create a table with keys for each prompt.
- Store SSML strings or references to Polly voices.

### 5. (Optional) S3, Transcribe & Comprehend
- Store voicemail audio in S3.
- Use Transcribe to convert audio to text.
- Use Comprehend to analyze sentiment and extract key phrases.

---

## 🧪 Testing Scenarios

- ✅ Call during business hours → Validate Lex routing and queue transfer
- ✅ Call after hours → Test voicemail fallback
- ✅ Wait in queue → Trigger callback offer
- ✅ Use unsupported intent → Test fallback and error handling
- ✅ Leave voicemail → Confirm recording, transcription, and sentiment analysis


---

## 👤 Author

**Vamsi**  


