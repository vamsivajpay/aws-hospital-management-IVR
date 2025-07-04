🤖 Lex Bot Summary
The Lex bot serves as the conversational front-end for the Amazon Connect IVR system. It prompts callers to specify their reason for calling—emergency, appointment, or billing—and routes them accordingly. The bot uses ASR (Automatic Speech Recognition) to match user utterances to predefined intents and supports fallback handling for unmatched input.

🧠 Intents Overview
emergency: Always active; routes directly to the Emergency Ward queue.

appointment: Active during business hours; outside hours, offers DTMF options for voicemail or hearing operating hours.

billing: Same logic as appointment; includes hours-of-operation check and voicemail fallback.

FallbackIntent: Captures unrecognized input and routes to the General Ward queue.

agentTransfer: Used internally to route to a live agent when needed.

voicemail: Captures user messages when queues are unavailable or after-hours.

📁 Lex Bot Versions
This folder includes two packaged versions of the Amazon Lex bot, each provided as a .zip file:

Draft Version: A development-stage version of the bot, intended for customization and iterative updates.

Version 1: A stable, production-ready version of the bot, suitable for immediate deployment.

🔧 How to Use
For direct deployment: Import the Version 1 zip file into the Amazon Lex console to use the bot as-is in your Amazon Connect IVR system.

For customization: Start with the Draft Version if you plan to modify the bot’s behavior—such as updating intents, slots, or fulfillment logic. After making changes, publish a new version for deployment.
