---
layout: post
title: "Automating Guest Messaging + AI FAQ Bot"
subtitle: "Beds24, Make.com, ZApi and GPT-4o mini for a real hostel"
date: 2026-07-17
header-img: "img/raiz-kite-architecture.png"
tags: [Automation, DataPipeline, LLM, API, Make, ZApi]
---

> A hostel in Jericoacoara (Brazil) was sending every check-in and check-out message by hand on WhatsApp and answering the same guest questions dozens of times a day. During an on-site work-trade, I designed and shipped an event-driven automation, then built an AI FAQ bot on top of it.



## Part 1 — Automated guest messaging (in production)

**Event flow:** Beds24 (PMS) → webhook → Make.com → Google Sheets + WhatsApp

![Logical Flow Blueprint](/img/makeWppAuto-architecture-jerihostel.png)

1. Multiple **Beds24 Auto Actions** fire on different events and send a webhook with guest data (name, phone, dates, room, booking channel and others).
2. In Make.com, the payload is first **normalized** (phone numbers cleaned via regex, dates converted to local time) and the **event type** is identified. A **Router** then sends each event down its own branch (new booking, check-in, check-out). Each branch looks up or updates the booking in the registry and sends the matching WhatsApp message. Keeping every event in a single scenario avoids duplicated logic and fits a Beds24 limit of one watch slot per property.
3. Phone numbers are normalized with regex before being sent to the WhatsApp gateway.
4. Each event is appended to the booking registry.

The registry works as the hostel's **single source of truth**: each booking is created once and then updated through its lifecycle, instead of logged as duplicate rows. That gives clean data for later analysis (lead time, channel mix, length of stay).

**Data-quality issues handled:**
- **Timezones**: Make runs in UTC, so dates are corrected to local time (UTC−3).
- **Missing contacts**: some OTAs don't share guest phone numbers. These bookings are flagged instead of failing silently.
- **Idempotency**: check-in updates match on booking ID, so re-sent webhooks don't create duplicates.

## Part 2 — AI FAQ bot (in progress)

**Event flow:** Incoming WhatsApp messages → Make.com → GPT-4o mini (with the hostel FAQ as system prompt) → reply.

![Logical Flow Blueprint](/img/makeFaqAI-architecture-jerihostel.png)

- A `fromMe = false -- from_guest` filter prevents infinite reply loops.
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

## Stack

Beds24 API · Make.com · Webhooks · Google Sheets · WhatsApp (Z-API) · OpenAI GPT-4o mini