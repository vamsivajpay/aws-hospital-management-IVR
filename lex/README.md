## 🤖 Lex Bot Summary

The Lex bot acts as the conversational front-end for the Amazon Connect IVR system.

- Prompts callers to specify their reason for calling: **emergency**, **appointment**, or **billing**
- Routes callers accordingly based on their response
- Uses ASR (Automatic Speech Recognition) to match user utterances to predefined intents
- Supports fallback handling for unmatched input

---

## 🧠 Intents Overview

- **emergency**
    - Always active
    - Routes directly to the Emergency Ward queue

- **appointment**
    - Active during business hours
    - Outside hours, offers DTMF options for voicemail or hearing operating hours

- **billing**
    - Same logic as appointment
    - Checks hours of operation and provides voicemail fallback

- **FallbackIntent**
    - Captures unrecognized input
    - Routes to the General Ward queue

- **agentTransfer**
    - Used internally to route to a live agent when needed

- **voicemail**
    - Captures user messages when queues are unavailable or after hours

---

## 📁 Lex Bot Versions

This folder includes two packaged versions of the Amazon Lex bot as `.zip` files:

- **Draft Version**
    - Development-stage version for customization and iterative updates

- **Version 1**
    - Stable, production-ready version for immediate deployment

---

## 🔧 How to Use

- **For direct deployment**
    - Import the **Version 1** zip file into the Amazon Lex console to use the bot as-is in your Amazon Connect IVR system.

- **For customization**
    - Start with the **Draft Version** if you plan to modify the bot’s behavior (such as updating intents, slots, or fulfillment logic).
    - After making changes, publish a new version for deployment.
