# 🗃️ DynamoDB Prompt Dataset – Hospital IVR System

This file defines the dynamic SSML prompts used in the Hospital Management IVR system. Each prompt is stored in a DynamoDB table and retrieved at runtime by a Lambda function to provide flexible, multilingual, and context-aware voice responses in Amazon Connect.

---

## 📄 File: `results.csv`

This CSV file contains two columns:

| Column Name     | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `PromptKey`      | A unique identifier used in the contact flow (e.g., `start-note`, `error-hoo`) |
| `SSML`           | The SSML-formatted message to be spoken by Amazon Polly                    |

---

## 🧠 Sample Entries

| PromptKey              | SSML Snippet                                                                 |
|------------------------|------------------------------------------------------------------------------|
| `start-note`           | `<prosody rate="88%">Hello welcome to Health rise hospital...`              |
| `appointment-hours-note` | `<speak><prosody rate='85%'>Appointment ward timings are...`             |
| `customerqueue-note`   | `Thank you for your patience... transferring your call to $.Attributes.selectedQueue` |
| `at-capacity-note`     | `Sorry we are experiencing high call volume...`                             |
| `lex-voicemail-note`   | `You called us in out of hours... press one to leave a voice mail...`       |

---PLEASE FIND SNAPSHOTS IN THE DIRECTORY FOR REFERENCE---

## 🧱 DynamoDB Table Schema

| Attribute Name | Type     | Description                                      |
|----------------|----------|--------------------------------------------------|
| `PromptKey`    | String (PK) | Matches the key used in the contact flow         |
| `SSML`         | String   | The full SSML message to be rendered by Polly    |

---

## ⚙️ Lambda Integration

The Lambda function (`fetch-prompts-handler`) receives a `PromptKey` from Amazon Connect and queries this table to return the corresponding SSML message.

### Example Query Flow:
1. Contact flow uses `Play Prompt` block with:
   - `Namespace`: `External`
   - `Key`: `start-note`
2. Lambda queries DynamoDB:
   ```json
   {
     "PromptKey": "start-note"
   }
