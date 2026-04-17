# Job Search Automation — n8n + OpenAI + Notion + Google Sheets

An AI-powered job application tracker built with n8n, OpenAI GPT-4o, Notion, and Gmail.

## What it does

Two connected workflows that automate the job search process end to end:

**Workflow 1 — Resume Tailor**
- Fill out a web form with a job description
- GPT-4o tailors your resume to match the role
- Application is automatically logged to a Notion database

**Workflow 2 — Email Classifier**
- Runs daily and scans your Gmail inbox
- GPT-4o classifies recruiter emails (Applied, Interview, Rejected, Other)
- Automatically updates the Notion application status
- Unclassified job emails are logged to Google Sheets for review

## Tech stack

- **n8n** — workflow automation (self-hosted via Docker)
- **OpenAI GPT-4o** — resume tailoring and email classification
- **Notion API** — application database
- **Gmail API** — inbox monitoring
- **Google Sheets** — unclassified email log

## Architecture

Workflow 1:

n8n Form → OpenAI (tailor resume) → Merge → Notion (create row)

Workflow 2:

Schedule Trigger → Gmail (get emails) → OpenAI (classify) → Code (parse)

→ Filter (drop irrelevant) → IF → Notion (update status)

→ Google Sheets (log unclassified)

## Setup

1. Import the workflow JSON files into your n8n instance
2. Add credentials: OpenAI API key, Notion API key, Google OAuth
3. Set up your Notion database with the required fields
4. Update the OpenAI system prompt with your own resume text
5. Activate both workflows

## Future plans

- Interview prep AI: use Notion application data + personal case studies to generate interview preparation notes per role
