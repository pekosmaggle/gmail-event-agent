## Gmail Event Scoring Agent
AI agent that automatically scores event invitations received by email and stores results in Notion.

## What it does
-Monitors a Gmail label for incoming event invitations
-Fetches the full email content (including PDF attachments if present)
-Searches the web for additional event information (attendee count, sponsors, past editions)
-Scores the event against Weglot's qualification criteria (0-100)
-Stores the scored result in a Notion database

## Stack
**n8n** — workflow orchestration (self-hosted)
**Claude (Anthropic)** — AI scoring engine
**Tavily** — web search tool
**Gmail API** — email monitoring and attachment extraction
**Notion API** — output storage

## Workflow Architecture
Gmail Trigger -> HTTP Request (full email) -> Code JS (extract text + detect attachments)
IF -> [with PDF] -> HTTP Request (download PDF) -> Code JS (combine content)
Else -> [no PDF] -> AI Agent (Claude + Tavily) -> Code JS (parse JSON) -> Notion

## Prerequisites
-n8n self-hosted instance
-Anthropic API key
-Tavily API key
-Google Cloud project with Gmail API enabled (OAuth2 credentials)
-Notion integration token + database ID

## Setup
1. Import `gmail_event_agent.json` into your n8n instance
2. Configure credentials (see `.env.example` for required variables)
3. Create a Gmail label to monitor
4. Set up your Notion database with the required columns
5. Activate the workflow
