TripMate AI

Plan together in chat. Let AI organise the trip.

TripMate AI is an AI-powered travel planning assistant that turns group conversations into organised, collaborative travel itineraries.

Instead of searching through hundreds of WhatsApp messages to find flight details, hotel bookings, restaurant recommendations and agreed activities, TripMate AI extracts relevant information, organises decisions and keeps everyone updated through a central trip workspace.

The initial pilot is designed for the Birdy Group Seoul trip (2–7 May 2027), with four travellers.

---

1. Product Vision

Make group travel planning effortless by turning everyday conversations into structured, actionable travel plans.

Core principles:

- Chat-first: Plan trips through familiar messaging channels.
- AI-assisted: Extract, organise and connect information automatically.
- Collaborative: Keep travellers aligned on plans and decisions.
- Organised: Maintain one reliable source of truth for each trip.
- Human-controlled: Important changes require organiser approval.

2. MVP Scope

The first release focuses on a WhatsApp-based travel assistant.

Trip Management

- Create and manage trips.
- Add travellers and assign organiser roles.
- Maintain trip dates, destinations and travel preferences.
- Store trip-related information centrally.

AI Conversation Intelligence

- Process shared messages and travel information.
- Extract dates, times, locations, bookings and activities.
- Interpret shared links, images and documents.
- Identify decisions, preferences and unresolved questions.
- Retain source references for extracted information.

Collaborative Itinerary

- Generate daily itineraries.
- Organise activities by date and time.
- Distinguish proposed activities from confirmed plans.
- Detect conflicting dates, times and activities.
- Track itinerary versions and changes.

Approval Workflow

- Detect group agreement where possible.
- Require organiser approval for significant changes.
- Notify members of approved changes.
- Preserve confirmed activities unless changes are explicitly approved.

Travel Assistant

- Answer questions using stored trip information.
- Retrieve relevant itinerary details.
- Provide daily itinerary reminders.
- Notify travellers of pending decisions and changes.

3. User Experience

Initial channel: WhatsApp

The intended experience:

1. Travellers share travel information through a supported WhatsApp integration or forwarding workflow.
2. TripMate AI interprets messages and extracts relevant information.
3. AI proposes itinerary updates and identifies decisions.
4. The organiser reviews and approves significant changes.
5. The trip workspace maintains the latest confirmed itinerary.
6. Travellers receive scheduled daily updates and can ask trip-related questions.

Important WhatsApp constraint: Standard WhatsApp Cloud API does not provide unrestricted access to existing personal WhatsApp group conversations. The MVP must use supported messaging, forwarding or manual-sharing workflows. Any WhatsApp Groups API capability will be evaluated separately, subject to eligibility.

4. Technology Stack

Layer| Technology
Frontend| Next.js, React, TypeScript
Backend| Next.js server actions / API routes
Database| Supabase PostgreSQL
Authentication| Supabase Auth
File storage| Supabase Storage
AI| OpenAI API, Structured Outputs
Messaging| WhatsApp Business Cloud API
Maps| Google Maps Platform
Scheduled jobs| Supabase Cron / background workers
Monitoring| Application logging and Sentry

5. Core Data Model

Initial database entities:

- "profiles" – user profiles
- "trips" – trip information and configuration
- "trip_members" – travellers and roles
- "itinerary_days" – daily itinerary structure
- "itinerary_items" – activities, bookings and destinations
- "messages" – conversation records
- "extracted_facts" – structured information extracted by AI
- "change_requests" – proposed itinerary changes and approvals
- "audit_logs" – important actions and change history

Row Level Security (RLS) is enabled to protect trip data and restrict access to authorised members.

6. AI Design Principles

TripMate AI must prioritise accuracy, transparency and user control.

- Never invent bookings or confirmations.
- Clearly distinguish suggestions from confirmed arrangements.
- Never interpret silence as agreement.
- Preserve the source of extracted information.
- Detect conflicting information rather than silently choosing one version.
- Never silently remove confirmed activities.
- Require approval for high-impact itinerary changes.
- Maintain an auditable history of important decisions.

7. Development Roadmap

Phase 1 – MVP

- User authentication
- Trip creation and member management
- WhatsApp message intake
- AI extraction and classification
- Central trip information repository
- Itinerary generation and management
- Organiser approval workflow
- Daily itinerary notifications
- Trip-related AI Q&A

Phase 2 – Enhanced Travel Assistant

- Maps and route planning
- Weather information
- Voice message processing
- Multilingual support
- Group expense and budget management
- Booking status tracking

Phase 3 – Ecosystem and Commercialisation

- Flight status and travel alerts
- Booking platform integrations
- Group polls and voting
- Travel recommendations and marketplace
- Travel agency and commercial partner integrations

8. MVP Success Metrics

Metric| Target
Message classification accuracy| ≥95%
Booking information extraction accuracy| ≥90%
Itinerary retrieval accuracy| ≥98%
Approved changes correctly applied| ≥95%
Daily notification delivery| ≥99%
Duplicate scheduled notifications| 0
Trip Q&A accuracy| ≥90%
Unapproved high-impact changes| 0

9. Project Structure

The intended repository structure:

tripmate-ai/
├── app/
│   ├── auth/
│   ├── login/
│   ├── trips/
│   └── api/
├── components/
├── lib/
│   ├── supabase/
│   ├── ai/
│   └── whatsapp/
├── supabase/
│   └── schema.sql
├── public/
├── .env.example
├── package.json
└── README.md

10. Getting Started

Prerequisites

- Node.js (LTS)
- npm
- Supabase project
- OpenAI API key
- WhatsApp Business Cloud API credentials (when messaging integration is enabled)

Local Setup

git clone https://github.com/danthumb/tripmate-ai.git
cd tripmate-ai
npm install

Create a ".env.local" file using ".env.example" as a template.

Configure the required environment variables:

NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
OPENAI_API_KEY=
WHATSAPP_ACCESS_TOKEN=
WHATSAPP_PHONE_NUMBER_ID=
WHATSAPP_VERIFY_TOKEN=

Start the development server:

npm run dev

Open "http://localhost:3000".

Never commit API keys, access tokens or Supabase service-role credentials to GitHub. Keep privileged credentials server-side.

11. Pilot Project

Birdy Group – Seoul, South Korea

- Travel dates: 2–7 May 2027
- Group size: 4 travellers
- Initial messaging channel: WhatsApp
- Approval model: Hybrid (AI detects agreement; organiser approves important changes)
- Objective: Validate whether AI can reduce the effort of coordinating group travel while keeping everyone informed and aligned.

---

Project owner: Dan
Repository: https://github.com/danthumb/tripmate-ai
Supabase project: "tripmate-ai" (Singapore region)

TripMate AI – Plan together in chat. Let AI organise the trip.