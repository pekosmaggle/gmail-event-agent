## Gmail Event Scoring Agent
AI agent that automatically scores event invitations received by email and stores results in Notion.

## What it does
1. Monitors a Gmail label for incoming event invitations
2. Fetches the full email content (including PDF attachments if present)
3. Searches the web for additional event information (attendee count, sponsors, past editions)
4. Scores the event against Weglot's qualification criteria (0-100)
5. Stores the scored result in a Notion database

## Stack
1. **n8n** — workflow orchestration (self-hosted)
2. **Claude (Anthropic)** — AI scoring engine
3. **Tavily** — web search tool
4. **Gmail API** — email monitoring and attachment extraction
5. **Notion API** — output storage

## Workflow Architecture
Gmail Trigger -> HTTP Request (full email) -> Code JS (extract text + detect attachments)
1. [with PDF] -> HTTP Request (download PDF) -> Code JS (combine content)
2. [no PDF] -> AI Agent (Claude + Tavily) -> Code JS (parse JSON) -> Notion

## Prerequisites
1. n8n self-hosted instance
2. Anthropic API key
3. Tavily API key
4. Google Cloud project with Gmail API enabled (OAuth2 credentials)
5. Notion integration token + database ID

## Setup
1. Import `gmail_event_agent.json` into your n8n instance
2. Configure credentials (see `.env.example` for required variables)
3. Create a Gmail label to monitor
4. Set up your Notion database with the required columns
5. Activate the workflow
