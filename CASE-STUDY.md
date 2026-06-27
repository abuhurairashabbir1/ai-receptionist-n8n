# AI Receptionist for a Home-Services Business (Fence Installation)

**A 24/7 AI assistant that chats with customers, qualifies leads, and instantly alerts the team — built with n8n + an LLM.**

---

## The problem

Home-services companies (fencing, roofing, landscaping, HVAC) live and die by their leads. But most inquiries arrive **after hours, on weekends, or while the crew is on a job site** — exactly when no one is free to answer.

Every unanswered message is a customer who simply calls the next company. The business never even sees the lead it lost.

## The solution

I built **an AI receptionist** that runs 24/7 and handles the front desk automatically:

1. **Greets and answers every customer instantly** — fence types, gates, process, general questions.
2. **Has a natural back-and-forth** — asks for details one or two at a time, like a real receptionist, not a clunky form.
3. **Collects and qualifies the lead** — name, phone, location, fence type, approximate length, and timeline.
4. **Knows when a lead is "ready"** — only flags a hand-off once it has both a name and a contact number.
5. **Instantly alerts the team** — the moment a qualified lead comes in, the full details are pushed to the team's channel, ready to act on.

All of this happens in **one connected automation** — no human touches it.

## The result / impact

- ⚡ **Replies in seconds, 24/7/365** — nights, weekends, holidays.
- 🎯 **Captures 100% of after-hours inquiries** that would otherwise be missed.
- 💰 **A fraction of the cost of a human receptionist** (~$3,000/mo, ~40 hrs/week) while covering **168 hrs/week**.
- 🧩 **Runs alongside the existing system** — low-risk, nothing to rip out or replace.

> The business stops paying for software and starts paying to *stop leads from walking out the door.*

## How it works (architecture)

```
Customer message
      │
      ▼
 Chat Trigger ──► AI Agent (LLM) ──► Parse & structure the reply
                      │                      │
              memory + system           Lead ready?
                 prompt                 ┌────┴────┐
                                       yes        no
                                        │          │
                            Alert the team    Reply to customer
```

**Key design decision:** instead of relying on the AI to call tools directly, the AI returns a **structured JSON response** every turn (reply + extracted lead fields + a `lead_ready` flag). Downstream nodes then handle the logic and the notification. This made the workflow **far more reliable and predictable** than a free-form agent — the AI focuses on conversation, the automation handles the actions.

## Tools & tech

- **n8n** — workflow automation engine
- **LLM (chat model)** — natural conversation + structured data extraction
- **Conversation memory** — keeps context across the chat
- **Webhook notifications** — instant lead alerts to the team channel (Discord/Slack/WhatsApp)

## Roadmap (what it can grow into)

- 📅 **Instant quoting** — customer picks fence type + footage + gates → gets a ballpark price
- 🗓️ **Live booking** — checks the estimator's calendar and offers the nearest open slots
- 🌐 **Ad-ready landing page** — a 3-step quote funnel to send paid traffic to
- ☎️ **Voice version** — answers phone calls and books callers
- ⭐ **Review & follow-up automation** — auto-requests Google reviews, chases unsigned quotes

---

*Demo data shown is fictional. Built as a reusable solution for home-services businesses.*
