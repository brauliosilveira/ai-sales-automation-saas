# AI Sales Automation SaaS

A production-grade SaaS platform for WhatsApp-based sales automation, built to help businesses manage contact data, validate phone numbers, launch campaigns at scale, extract lead sources, and improve message quality with AI-assisted content variation.

This repository is presented as a public portfolio case study for recruiters, hiring managers, and founders evaluating senior full-stack product work. It highlights the product architecture, automation strategy, multi-tenant SaaS design, operational workflows, and AI-assisted messaging features behind the platform while keeping the full source code private for commercial and security reasons.

🌐 **[View the Live Project](https://botpravender.com/)** | **[Try the Free Trial](https://botpravender.com/teste)**

<p>
<a href="https://www.youtube.com/watch?v=VskveXIBP2w">
  <img src="https://ytcards.demolab.com/?id=VskveXIBP2w&title=0&lang=en&background_color=%230d1117&title_color=%23ffffff&stats_color=%230d1117&max_title_lines=2&width=400" />
</a>
</p>

📺 **[Watch the Video Tour](https://www.youtube.com/watch?v=VskveXIBP2w)**

## Executive Summary

This project was built as a complete sales automation platform centered around WhatsApp operations.

Instead of treating outbound messaging as a simple blast tool, the platform was designed as a full operational system for:

- managing WhatsApp sending infrastructure;
- organizing and importing contact bases;
- validating whether numbers are actually on WhatsApp;
- extracting contacts from groups and address books;
- orchestrating campaigns with scheduling, delays, and rotation rules;
- monitoring performance through dashboards and delivery reporting;
- improving message variation and safety with AI-assisted spintax generation and quality checks.

The result is a SaaS product that connects acquisition, list building, outbound execution, and campaign analytics inside one environment.

The platform is also designed for cross-device access, allowing teams to operate from desktop and mobile environments through a PWA-style experience compatible with:

- Windows
- macOS
- Linux
- iPhone
- Android

## The Problem

Businesses running outbound sales through WhatsApp usually face the same operational bottlenecks:

- scattered contact bases with poor organization;
- low-quality phone data;
- no reliable way to validate whether a number is active on WhatsApp;
- manual campaign setup and little control over sending behavior;
- weak reporting after campaigns are launched;
- high risk of account bans caused by repetitive or low-quality messaging;
- too many disconnected tools for extraction, list management, sending, and analysis.

This platform was built to solve that operational fragmentation with a productized, multi-tenant SaaS workflow.

## What I Built

- A multi-tenant sales automation SaaS platform
- WhatsApp instance management for sending infrastructure
- Contact list creation, import, export, and organization
- WhatsApp number verification workflows
- Group and address-book extraction features
- Campaign creation with scheduling, rate controls, and instance rotation
- Delivery tracking and campaign reporting
- Dashboard analytics with usage and plan-limit visibility
- Trial-aware product flows and plan-based limits
- AI-assisted spintax generation for message variation
- Message quality checks to reduce risky sending patterns
- Worker-based asynchronous processing for outbound operations

## Core Product Capabilities

### WhatsApp infrastructure management

Users can connect and manage WhatsApp instances inside the platform, which act as the operational sending layer for campaigns and verification workflows.

### Contact and list operations

The platform supports:

- manual list creation;
- spreadsheet-based contact import;
- native export of contact bases;
- list-level organization for campaign targeting.

### WhatsApp verification

Before sending at scale, users can verify whether numbers are actually present on WhatsApp. This improves lead quality and reduces waste before campaign execution.

### Campaign orchestration

Campaigns are not treated as simple one-click blasts. The system supports:

- contact-list selection;
- multi-instance selection;
- daily send limits;
- restart windows for queue continuation;
- message rotation logic;
- scheduling;
- business-hours restriction;
- interval and batch pause configuration.

### Extraction workflows

The extractor layer allows users to build contact bases directly from:

- WhatsApp groups;
- phone address-book data.

Extracted data is saved back into the platform as usable lists and can be exported as spreadsheets.

### Reporting and analytics

The product includes dashboard-level and campaign-level visibility over:

- total sends;
- delivered messages;
- pending queue volume;
- cancellations;
- failures;
- success rate;
- campaign counts;
- list and contact usage;
- extraction usage against plan limits.

### AI-assisted messaging

The platform includes AI-assisted spintax generation and messaging-quality guidance to help users create more varied and less repetitive outbound content.

This matters because message quality directly affects deliverability and operational safety in WhatsApp-based outbound workflows.

## Product Roadmap

In addition to the capabilities already implemented, the product roadmap includes four major feature areas that expand the platform beyond outbound execution and into a broader automation operating system for sales teams.

### 1. Button-based campaign interactions

The campaign layer is being extended to support interactive buttons, including:

- link buttons for external pages or a primary WhatsApp contact;
- positive-intent buttons such as `Yes`, `I want this`, or `I am interested`, which can trigger an AI agent flow, chatbot flow, or human handoff;
- opt-out buttons such as `No`, `Not interested`, or `Block`, which store suppression intent directly on the lead/contact record.

This moves campaigns closer to structured interaction design rather than plain outbound messaging.

### 2. Account health intelligence

A dedicated account-health module is being introduced so the platform can evaluate WhatsApp-instance condition and automatically recommend or constrain how many messages an account should send per day.

The goal is to turn sending-capacity decisions into a guided, system-driven layer rather than a purely manual guess.

### 3. Intelligent account warming

The platform roadmap also includes an intelligent warm-up module focused on operational readiness. Instead of treating new instances as immediately ready for scale, the system will use structured warm-up missions, health checks, and readiness logic before higher-volume sending is allowed.

This expands the product from campaign execution into account preparation and operational governance.

### 4. Segmented B2B data acquisition

Another planned capability is segmented contact-base acquisition, where users can choose:

- business segment;
- city;
- state.

The platform will then generate a segmented B2B contact base that can be used to start outbound prospecting directly from within the same system.

This creates a more complete workflow that connects lead acquisition, qualification, campaign launch, and follow-up inside a single product.

## Technical Analysis of the App

Based on the application codebase, the platform is built with:

- Nuxt 4
- Vue 3
- Nitro server routes
- Supabase Auth
- Supabase Postgres
- a separate Node.js worker layer

The frontend and backend application logic live inside the Nuxt app, while asynchronous operational tasks are handled by a dedicated worker process.

The worker layer is responsible for execution-heavy workflows such as:

- outbound campaign processing;
- queue handling;
- delivery-status updates;
- WhatsApp number verification jobs.

This separation makes the product better suited for production usage, since high-volume operational jobs do not need to block the user-facing application layer.

## AI Layer

One of the most interesting parts of the product is the AI-assisted message workflow.

The platform includes:

- AI-generated spintax suggestions for WhatsApp messages;
- quality checks that warn about aggressive copy, low variation, risky links, and unsafe sending behavior;
- guidance to improve message diversity and reduce repetitive patterns.

This is a practical use of AI: not as a novelty feature, but as an operational layer that improves campaign quality and reduces risk.

## System Architecture

At a high level, the platform operates across four product layers:

### 1. SaaS application layer

The main app handles:

- authentication;
- dashboards;
- list management;
- campaign setup;
- extraction UI;
- reporting;
- account and plan-aware product flows.

### 2. Data and auth layer

Supabase is used for:

- authentication;
- profile and tenant relationships;
- campaign and queue persistence;
- list and contact storage;
- verification and extraction job state.

### 3. Worker execution layer

A separate worker process handles background operations such as:

- campaign send orchestration;
- stuck-job recovery;
- delivery-state updates;
- verification job processing.

### 4. External communication layer

The platform integrates with external services for:

- WhatsApp messaging and infrastructure;
- WhatsApp number verification;
- AI text assistance;
- transactional notifications.

It is also designed to remain accessible across both desktop and mobile usage patterns, giving operators flexibility to manage workflows from office or field environments.

## Technical Flow

### 1. Data acquisition

Contacts enter the system through imports, extraction workflows, or existing lists.

### 2. Data qualification

Users can validate whether contacts are active on WhatsApp before sending. This improves targeting quality and avoids wasting campaign volume on invalid numbers.

### 3. Campaign configuration

Users create a campaign by selecting a list, defining the message sequence, choosing WhatsApp instances, and configuring send limits, intervals, and scheduling rules.

### 4. AI-assisted message preparation

The platform can help generate spintax and assess message quality before launch, reducing repetition and improving operational safety.

### 5. Queue creation

Once confirmed, the system creates the campaign, snapshots the sending setup, builds queue items, and prepares the campaign for execution.

### 6. Background execution

The worker consumes queued items, rotates instances when needed, enforces timing rules, reacts to delivery events, and updates operational state asynchronously.

### 7. Monitoring and reporting

Users can monitor results through dashboard metrics, campaign reports, and delivery-state tracking inside the app.

## Key Engineering Decisions

### Build the product as a multi-tenant SaaS

The platform is designed around tenant/company boundaries, plan limits, and account-scoped operations instead of acting as a one-off internal tool.

### Separate app logic from execution-heavy worker logic

Outbound automation and verification jobs are handled outside the main app request cycle, which improves scalability and protects the user-facing experience.

### Treat sending safety as a product feature

Sending limits, interval controls, business-hours options, rotation logic, and quality checks are not minor details. They are essential to making large-scale WhatsApp automation more sustainable.

### Use AI as an operational enhancement, not a gimmick

The AI layer focuses on a very practical outcome: improving message variation and campaign quality rather than adding superficial chat features.

### Keep qualification close to execution

List management, number verification, extraction, campaign creation, and analytics all live in the same product. That reduces tool fragmentation and makes the workflow operationally coherent.

## Reliability and Operational Considerations

The analyzed implementation includes several production-minded design choices:

- asynchronous worker processing;
- queue-based campaign execution;
- background delivery updates;
- stuck-job recovery logic;
- instance rotation controls;
- plan-limit enforcement;
- verification before outbound execution;
- user-facing quality warnings before send.

## Why This Project Matters

This project demonstrates:

- end-to-end SaaS product development;
- multi-tenant architecture;
- full-stack product thinking across UI, backend, worker, and external integrations;
- operational automation for revenue-facing sales workflows;
- practical AI feature design tied to real product outcomes;
- asynchronous job processing and delivery-state orchestration;
- cross-platform SaaS product thinking through a PWA-style access model;
- a roadmap that expands the product into interaction design, account health, readiness automation, and segmented lead acquisition;
- a strong blend of product UX and systems engineering.

It also shows a very practical business skill: turning a messy outbound sales process into a structured, productized, and scalable workflow.

## Stack

- Nuxt 4
- Vue 3
- Nitro server routes
- Supabase Auth
- Supabase Postgres
- Node.js worker services
- WhatsApp API integration
- Groq/OpenAI-compatible API for AI-assisted spintax generation
- XLSX processing for contact import/export
- Transactional messaging integrations

## High-Level Architecture

```text
Users / Sales Teams
        |
        v
   Nuxt SaaS Application
        |
        +--> dashboards
        +--> campaign setup
        +--> list management
        +--> extraction workflows
        +--> reporting
        +--> AI-assisted message preparation
        |
        v
 Supabase Auth + Database
        |
        +--> campaigns
        +--> queue items
        +--> contacts and lists
        +--> tenant and plan data
        +--> extraction and verification jobs
        |
        v
 Node.js Worker Layer
        |
        +--> campaign execution
        +--> verification jobs
        +--> delivery updates
        +--> queue recovery
        |
        v
 WhatsApp / AI / Messaging Integrations
```

## Demo and Media

This case study is supported by screenshots showing the path from contact qualification and campaign setup to automated execution and reporting.

- `Dashboard - Operational Metrics and Plan Usage`
- `Campaign Builder - Multi-Step Send Configuration`
- `AI Message Variation - Spintax Generation and Quality Checks`
- `List Management - Contact Base Organization`
- `WhatsApp Verification - Contact Qualification Workflow`
- `Extractor - Group and Address-Book Lead Capture`
- `Campaign Reporting - Delivery Tracking and Performance`

## About This Repository

This is a public portfolio case study for full-stack, backend, SaaS, automation, and AI-enabled product roles.

The complete source code, internal integrations, secrets, and infrastructure details remain private for commercial and security reasons.

## My Role

I designed and implemented the product architecture and automation workflows behind the platform, including:

- SaaS product architecture;
- campaign orchestration logic;
- contact and list workflows;
- extraction and qualification features;
- AI-assisted messaging features;
- asynchronous worker-based execution;
- analytics and operational reporting;
- integration design for messaging and external services.

## Contact

If you would like a live walkthrough or want to discuss AI-enabled SaaS platforms, automation systems, outbound operations, or full-stack roles, feel free to reach out.

- Website: https://www.brauliosilveira.com
- LinkedIn: https://linkedin.com/in/brauliosilveira
- Email: hi@brauliosilveira.com
- YouTube: https://youtube.com/@venderpelowhats
