---
layout: post
title: "Automating a Beach Hostel: Event-Driven Guest Messaging + AI FAQ Bot"
subtitle: "Beds24, Make.com, WhatsApp and GPT-4o mini for a real hostel in Jericoacoara"
date: 2026-07-17
header-img: "img/raiz-kite-architecture.png"
tags: [Automation, DataPipeline, LLM, API, Make, WhatsApp]
---

> A small hostel in Jericoacoara (Brazil) was sending every check-in and check-out message by hand on WhatsApp and answering the same guest questions dozens of times a day. During an on-site work-trade, I designed and shipped an event-driven automation, then built an AI FAQ bot on top of it.

![Architecture diagram](/img/raiz-kite-architecture.png)

## Results

- **[X] bookings** processed automatically since July 2026, with zero manual check-in/check-out messages
- Every booking is logged into a structured **booking registry**, the hostel's first queryable dataset (channel, length of stay, lead time)
- AI bot cost estimated at **~US$ [X] per 1,000 messages**, [X]× cheaper than the next alternative evaluated
- Reception staff saves **~[X] min/day**

## Part 1 — Automated guest messaging (in production)

**Event flow:** Beds24 (PMS) → webhook → Make.com → WhatsApp + Google Sheets

1. A single Beds24 Auto Action fires on booking events and sends a webhook with guest data (name, phone, dates, room, booking channel).
2. In Make.com, a **Router** branches on `firstNight` (arrival) vs `lastNight` (departure). One scenario handles both, because Beds24 allows only one watch slot per property.
3. Phone numbers are normalized with regex before being sent to the WhatsApp gateway.
4. Each event is appended to the booking registry.

**Data-quality issues handled:**
- **Timezones**: Make runs in UTC, so dates are corrected to local time (UTC−3).
- **Template limits**: some PMS variables arrive as literal strings in the webhook, so the scenario calls Beds24 API v2 to enrich each booking.
- **Missing contacts**: some OTAs don't share guest phone numbers. These bookings are flagged instead of failing silently.

## Part 2 — AI FAQ bot (in progress)

Incoming WhatsApp messages → Make.com → GPT-4o mini (with the hostel FAQ as system prompt) → reply.

- A `fromMe = false` filter prevents infinite reply loops.
- Answers are scoped to the FAQ: prices, kite lessons, transfers, house rules.

### Model cost analysis

| Model | Input / 1M tokens | Output / 1M tokens | Cost per message* |
|---|---|---|---|
| GPT-4o mini | $0.15 | $0.60 | ~$0.00007 |
| Claude Haiku 4.5 | $1.00 | $5.00 | ~$0.00055 |

*Typical FAQ exchange: ~250 input + ~60 output tokens.

For short, scoped answers, the cheaper model was good enough, at roughly 8× lower cost.

### WhatsApp provider evaluation

I compared six gateways (Z-API, Evolution API, Green-API, MegaAPI, Uazapi and the official Meta Cloud API) on stability, ban risk, billing reputation and policy compliance. Key constraint: a single number can't run on an unofficial API and the official API at the same time, so migration is all-or-nothing. The choice had to be right from the start.

## What I'd do next

- Move the registry from Google Sheets to a database (Postgres or DuckDB) and build an **occupancy & channel dashboard** (seasonality, lead time, revenue by OTA)
- Log bot conversations to measure deflection rate and find questions the FAQ doesn't cover
- Migrate to the official WhatsApp Cloud API

## Stack

Beds24 API · Make.com · Webhooks · Google Sheets · WhatsApp (Z-API) · OpenAI GPT-4o mini