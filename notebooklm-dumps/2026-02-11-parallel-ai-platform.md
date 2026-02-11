# Parallel AI Platform - Complete Documentation

*Source: parallellabs.app - 2026-02-11*

## Overview
All-in-one AI platform per creare "virtual companies" con AI employees, workflows, content generation.

## Core Features

### 1. AI Employees
- **Creazione**: Name, title, photo, instructions
- **Personalità**: Friendly, professional, casual
- **Knowledge Base**: Documenti caricati per training
- **Tags/Departments**: Organizzazione

### 2. Knowledge Base
- **Upload**: PDF, Word, Text, Spreadsheet, HTML
- **Folders**: Organizzazione gerarchica
- **Tags**: Categorizzazione
- **Sharing**: Private/Shared/Public

### 3. Workflows (Automazione)
- **Triggers**: Webhook, Schedule, Manual
- **Conditions**: If/Then logic
- **Actions**: Email, HTTP request, Smart List update
- **Testing**: Test/Execute con logs

### 4. Smart Lists
- **Tipi colonna**: Text, Number, Email, Date, Select, Multi-Select
- **Import**: CSV/Excel
- **Actions**: Send to Sequence, AI Analysis, Browser Task

### 5. Sequences (Email Campaigns)
- **Step types**: Email, LinkedIn Message, LinkedIn Connection, Wait
- **Variables**: Personalizzazione con {{firstName}}, {{company}}, etc.
- **Performance tracking**: Sent, Opened, Clicked, Replied
- **Approvals**: Pending actions review

### 6. Content Tools
- **Content Engine**: Blog posts, social media, email newsletters
- **Images**: AI text-to-image (GPT-Image-1, DALL-E 3, Stable Diffusion)
- **Audio**: Text-to-speech con voice cloning
- **Video**: Text-to-video e image-to-video

### 7. Agents (Website Chatbots)
- **Embed**: Codice per siti web
- **Lead Capture**: Raccolta info visitatori
- **Knowledge connection**: Usa la Knowledge Base

## Admin Features

### Collaborators
- **Ruoli**: Owner, Admin, Member, Viewer
- **Feature Access**: Controllo granulare per feature
- **SSO**: Okta, Azure AD, Google Workspace

### Integrations
- **Communication**: Slack, Discord, Teams, Email SMTP
- **CRM**: HubSpot, Salesforce, Pipedrive
- **Social**: LinkedIn, Twitter/X, Facebook
- **Storage**: Google Drive, Dropbox, OneDrive, Notion
- **Development**: GitHub, GitLab, Webhooks

## Architecture Summary
```
Parallel AI Platform
├── Global Features (Companies, Profile, Support)
├── Core Features (Dashboard, Chat, Employees, Knowledge)
├── Workflow Features (Workflows, Smart Lists, Sequences, Inbox)
├── Content Tools (Engine, Images, Audio, Video, Voices)
└── Admin Features (Collaborators, Integrations, Agents)
```

## Pricing Model
- **Credits**: Used per AI features
- **Subscription tiers**: Free, Pro, etc.
- **Credit limits**: Visualizzati nel profile

---

*Platform URL: parallellabs.app*
