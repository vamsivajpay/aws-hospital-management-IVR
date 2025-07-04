# 🧠 Voicemail Transcription & Sentiment Analysis – Hospital IVR

This module automates voicemail processing in a hospital IVR system using two AWS Lambda functions: `transcribe` and `comprehend`. It converts patient voicemails into text, analyzes sentiment, and stores the results for intelligent prioritization.

---

## 🔄 Workflow Overview

1. ☎️ A patient leaves a voicemail in Amazon Connect.
2. 📤 The audio file is uploaded to an S3 bucket (`eps24cimp001`).
3. ⚙️ `transcribe` Lambda Function
   - Triggered by the audio upload.
   - Starts an Amazon Transcribe job.
   - Saves the transcript JSON back to the same S3 bucket.

4. 📥 The transcript JSON is uploaded to S3.
5. ⚙️ `comprehend` Lambda Function
   - Triggered by the transcript upload.
   - Extracts the transcript text.
   - Uses Amazon Comprehend to detect sentiment.
   - Stores `contactId`, `sentiment`, and `text` in DynamoDB (`EPS24CIMP001`).

---

## 🧱 AWS Services Used

| Service              | Role                                      |
|----------------------|-------------------------------------------|
| Amazon S3            | Stores voicemail audio and transcript files |
| AWS Lambda           | Hosts `transcribe` and `comprehend` logic |
| Amazon Transcribe    | Converts audio to text                    |
| Amazon Comprehend    | Analyzes sentiment of the transcript      |
| Amazon DynamoDB      | Stores sentiment results for follow-up    |
