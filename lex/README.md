🤖 Lex Bot Summary
The Lex bot acts as the conversational front-end for the Amazon Connect IVR system.
It prompts callers to specify their reason for calling—emergency, appointment, or billing—and routes them accordingly.
The bot leverages ASR (Automatic Speech Recognition) to match user utterances to predefined intents, and includes fallback handling for unmatched input.

🧠 Intents Overview
emergency

Always active.
Routes callers directly to the Emergency Ward queue.
appointment

Active during business hours.
Outside business hours, offers DTMF options for leaving a voicemail or hearing operating hours.
billing

Follows the same logic as the appointment intent.
Includes an hours-of-operation check and voicemail fallback.
FallbackIntent

Captures any unrecognized input.
Routes callers to the General Ward queue.
agentTransfer

Used internally for routing callers to a live agent when needed.
voicemail

Captures user messages when queues are unavailable or after business hours.
📁 Lex Bot Versions
This folder contains two packaged versions of the Amazon Lex bot (provided as .zip files):

Draft Version

Development-stage version.
Intended for customization and iterative updates.
Version 1

Stable, production-ready version.
Suitable for immediate deployment.
🔧 How to Use
For Direct Deployment

Import the Version 1 zip file into the Amazon Lex console to use the bot as-is in your Amazon Connect IVR system.
For Customization

Start with the Draft Version if you plan to modify the bot’s behavior (e.g., updating intents, slots, or fulfillment logic).
After making changes, publish a new version for deployment.
