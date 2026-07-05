# Secure Lead Qualification Automation (n8n)

An automated lead intake and qualification system that classifies incoming leads using AI, while ensuring sensitive contact information (PII) never touches third-party AI services or team communication channels.

## What it does
- Receives lead data via webhook (form, WhatsApp, or any lead source)
- Masks phone numbers and emails BEFORE any AI processing
- Uses AI (via OpenRouter) to classify lead status (Hot/Warm/Cold) and intent
- Routes qualified leads to CRM (Airtable) + Slack alert
- Cold/spam leads are logged silently, no alert noise
- Raw contact info is stored ONLY in the access-controlled CRM — never exposed to AI or Slack

## Security design decisions
- **PII masking before AI calls**: names and inquiry text are sent to the AI; phone/email are never included in the AI request
- **Masked data in team alerts**: Slack notifications show masked contact info only (`+923****67`) — full details live only in Airtable
- **Least-privilege data flow**: each step only receives the data it needs to do its job

## Stack
n8n (self-hosted) • OpenRouter (Claude Haiku 4.5) • Airtable • Slack • Webhook trigger

## Demo
[Loom walkthrough link]

## Note
This is a portfolio demonstration. In a live client deployment, the webhook would connect directly to a real lead source (website form, WhatsApp Business API, etc.) instead of manual test calls.
