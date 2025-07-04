# 🔧 Lambda Function – Fetch SSML Prompts from DynamoDB

This AWS Lambda function dynamically retrieves SSML-formatted voice prompts from a DynamoDB table based on a predefined list of prompt keys. It is designed to be invoked by Amazon Connect contact flows using the `Play Prompt` block with `Namespace: External`.

---

## 🎯 Purpose

- Centralizes IVR prompt management using DynamoDB.
- Enables real-time updates to voice messages without modifying contact flows.
- Supports dynamic SSML playback via Amazon Polly in Amazon Connect.

---

## 🧠 How It Works

1. Amazon Connect invokes this Lambda function using a `Play Prompt` block.
2. The function queries DynamoDB for a list of predefined `PromptKey` values.
3. It returns a dictionary of SSML strings, each mapped to a formatted attribute name.
4. Amazon Connect uses these attributes to play the corresponding voice prompts.

---
