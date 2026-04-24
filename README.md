# Gmail Event Agent

Agent automatisé qui analyse les emails d'événements entrants, les score selon des critères définis, et produit un dashboard des meilleures opportunités.

## Stack
- n8n (orchestration)
- Gmail API (lecture emails)
- Claude Haiku (scoring IA)
- Docker

## Setup
1. Copie `.env.example` en `.env` et remplis les variables
2. Lance `docker-compose up -d`
3. Importe le workflow depuis `workflows/event-scorer.json`
