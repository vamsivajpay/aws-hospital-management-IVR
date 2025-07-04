# 🧩 Amazon Connect Contact Flows – Hospital Management IVR

This repository contains modular and intelligent contact flows designed for a hospital voice automation system using Amazon Connect. These flows handle patient interactions such as appointment booking, billing inquiries, emergency routing, and general support—powered by AWS Lex, Lambda, and dynamic prompt management.

---

## 📁 Contact Flows Included

| File Name                                | Purpose                                                                 |
|------------------------------------------|-------------------------------------------------------------------------|
| `hospital-main-contact-flow.json`        | Primary IVR flow that handles Lex interaction, intent routing, working hours, and queue logic. |
| `hospital-queue-flow.json`               | Queue-specific flow that plays dynamic SSML prompts or music while the caller waits. |

---

## 🧠 Flow Capabilities

### 🔹 Main Contact Flow
- Integrates with **Amazon Lex V2** to capture patient intent.
- Routes calls to queues: `appointments`, `billing`, `emergency`, `general`.
- Checks **working hours** and offers voicemail or callback if closed.
- Uses **Lambda** to fetch dynamic prompts from DynamoDB.
- Handles **queue capacity** with fallback options.

### 🔹 Queue Flow
- Invokes Lambda to fetch SSML messages based on queue.
- Updates contact attributes (e.g., `selectedQueue`) for agent context.
- Plays **on-hold music** or dynamic messages using `MessageParticipantIteratively`.
- Offers **interruptible prompts** and handles timeout gracefully.

---
