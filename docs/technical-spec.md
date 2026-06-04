# The Silence Protocol — Technical Specification

**Document version:** 1.0.0
**Status:** Draft
**Last updated:** 2026-06-04
**Maintainer:** The Silence Protocol Core Team

---

## Table of Contents

1. [Protocol Summary](#1-protocol-summary)
2. [Defining Digital Peace of Mind](#2-defining-digital-peace-of-mind)
3. [Core Principles](#3-core-principles)
4. [Technical Implementation](#4-technical-implementation)
5. [Usage Scenarios](#5-usage-scenarios)
6. [Versioning & Compatibility](#6-versioning--compatibility)
7. [Glossary](#7-glossary)

---

## 1. Protocol Summary

The Silence Protocol is a **structured behavioral and technical framework** designed to help individuals, teams, and software systems enforce healthy communication boundaries in digital environments.

At its core, this protocol answers one question:

> *"How should technology behave when humans need to be undisturbed?"*

The protocol operates on three levels:

| Level | Scope | Mechanism |
|---|---|---|
| **Personal** | Individual users | Personal rules, device settings, habits |
| **Social** | Teams & communities | Shared communication contracts |
| **Systemic** | Apps & platforms | API rules, status schemas, design patterns |

This document covers the **technical layer** — the data structures, rules, and implementation patterns that enable software to respect human attention.

---

## 2. Defining Digital Peace of Mind

### 2.1 Formal Definition

**Digital Peace of Mind (DPoM)** is a measurable state in which a person:

1. **Controls when** they receive information, rather than being subject to it continuously
2. **Understands clearly** what demands their attention and what can wait
3. **Trusts** that their silence will not be misread as absence, neglect, or hostility
4. **Has recovered** their capacity for sustained, uninterrupted thought

DPoM is not the absence of all digital activity. It is the **alignment between a person's cognitive state and the demands their devices place on them**.

### 2.2 Measuring DPoM

The following indicators can be used to evaluate whether a system supports or degrades Digital Peace of Mind:

| Indicator | Healthy Signal | Warning Signal |
|---|---|---|
| **Notification density** | < 10 actionable alerts/day | > 40 interruptions/day |
| **Response latency pressure** | Responses expected within hours | Responses expected within minutes |
| **Async-to-sync ratio** | > 70% async communication | < 30% async communication |
| **Focus block integrity** | Work blocks uninterrupted > 60 min | Constant context switching < 10 min |
| **Off-hour contact rate** | Near zero outside defined windows | Regular messages outside work hours |

### 2.3 What DPoM Is Not

- ❌ Ignoring people or being unreachable
- ❌ A blanket refusal to use technology
- ❌ Productivity optimization or time management
- ❌ A privilege available only to certain roles or seniority levels

---

## 3. Core Principles

The following **six principles** form the behavioral and technical backbone of the protocol. Every implementation decision should trace back to at least one of them.

---

### Principle 1 — Silence is the Default State

**Statement:** A user's status should default to *unavailable for interruption*. Presence must be explicitly declared, not assumed.

**Rationale:** Most notification systems assume that if a user has not turned something off, they are reachable. This inverts healthy cognitive boundaries. The protocol treats the human as the closed system; external signals must request access, not assume it.

**Technical implication:**
- Default user status: `silent`
- Explicit opt-in required to receive real-time notifications
- No "last seen" indicators without user consent

---

### Principle 2 — Response Windows, Not Response Pressure

**Statement:** Every user and team defines explicit **Response Windows** — time ranges during which they are reachable and replies are expected. Outside these windows, no message should signal urgency by default.

**Rationale:** The expectation of instant replies is a social construction, not a functional requirement for most communication. Async-first cultures consistently report lower burnout and equal or higher productivity.

**Technical implication:**
- Response windows stored as structured schedule objects (see [Section 4.2](#42-response-window-schema))
- Messages received outside windows are queued, not pushed
- Delivery receipts are separated from read receipts

---

### Principle 3 — Inverse Presence Signaling

**Statement:** Instead of broadcasting when you *are* available, users signal specific conditions under which they *want* to be reached. This inverts the traditional "online/offline" binary.

**Rationale:** Online status tells people *when you're there*, not *when you want to be interrupted*. These are not the same thing. A user can be online, in deep focus, and unreachable — and that should be expressible.

**Technical implication:**
- Replace binary presence (online/offline) with a **Reachability Profile**
- Reachability conditions are declarative rules (see [Section 4.3](#43-reachability-profile-schema))
- Systems surface: *"Reach out only if: [condition]"* rather than a green dot

---

### Principle 4 — Friction Toward Interruption

**Statement:** Real-time, synchronous interruptions (calls, pings, urgent flags) should require more steps to initiate than asynchronous messages. Urgency is a cost that the sender must justify.

**Rationale:** When it is equally easy to send a "quick question" as it is to interrupt someone mid-thought, the number of interruptions trends toward the sender's convenience, not the receiver's capacity. Adding intentional friction reduces low-value interruptions without blocking genuinely urgent ones.

**Technical implication:**
- Synchronous requests require a reason field (non-optional) before delivery
- Platforms implementing this spec should present a confirmation step before real-time alerts
- Urgency flags expire after a defined TTL (time-to-live) if not acknowledged

---

### Principle 5 — Transparent Unavailability

**Statement:** When a user is unavailable, the system communicates this clearly and without ambiguity — including *when* they are expected to respond. Silence should never be invisible.

**Rationale:** Much communication anxiety arises not from receiving a message, but from not knowing if it was received, read, or will ever be addressed. Clear unavailability signals remove this uncertainty from both parties.

**Technical implication:**
- Auto-replies are structured, not free-form, and include an estimated response time
- "Seen" indicators are opt-in
- Systems must expose a machine-readable `next_available_at` field for integrations

---

### Principle 6 — No Dark Patterns

**Statement:** Any implementation of this protocol must not introduce manipulation mechanisms that undermine the above principles — including social pressure indicators, read anxiety triggers, or gamified response scoring.

**Examples of prohibited patterns:**
- "X is typing..." shown indefinitely to provoke faster replies
- Red badge counters designed to exploit loss aversion
- Presence indicators shared without explicit user consent
- Notification summaries that manufacture false urgency

---

## 4. Technical Implementation

### 4.1 User Silence Status Object

The foundational data structure in this protocol is the **Silence Status Object**. It represents a user's current availability state and rules for being reached.

```json
{
  "user_id": "usr_8f3k2p",
  "display_name": "Rania",
  "silence_status": {
    "mode": "deep_focus",
    "active_since": "2026-06-04T09:00:00Z",
    "active_until": "2026-06-04T11:00:00Z",
    "message": "In a focus block. I will reply after 11:00.",
    "next_available_at": "2026-06-04T11:00:00Z",
    "allow_emergency_contact": true,
    "emergency_passphrase": "URGENT_SILENCE"
  },
  "updated_at": "2026-06-04T09:01:45Z"
}
```

**Field reference:**

| Field | Type | Description |
|---|---|---|
| `mode` | `enum` | One of: `available`, `deep_focus`, `offline`, `do_not_disturb`, `scheduled_away` |
| `active_since` | ISO 8601 | When the current mode started |
| `active_until` | ISO 8601 | When the mode expires (null = indefinite) |
| `message` | `string` | Human-readable status message |
| `next_available_at` | ISO 8601 | Expected return to availability (can be estimated) |
| `allow_emergency_contact` | `boolean` | Whether escalation bypass is permitted |
| `emergency_passphrase` | `string` | Keyword that unlocks urgent delivery (optional) |

---

### 4.2 Response Window Schema

A **Response Window** defines the time ranges during which a user expects to send and receive messages.

```json
{
  "user_id": "usr_8f3k2p",
  "response_windows": [
    {
      "day": "weekday",
      "windows": [
        {
          "label": "Morning check-in",
          "start": "08:30",
          "end": "09:00",
          "timezone": "Asia/Jakarta"
        },
        {
          "label": "Afternoon check-in",
          "start": "13:00",
          "end": "13:30",
          "timezone": "Asia/Jakarta"
        }
      ]
    },
    {
      "day": "weekend",
      "windows": []
    }
  ],
  "outside_window_behavior": "queue",
  "queue_delivery_at": "next_window_start",
  "version": "1.0"
}
```

**`outside_window_behavior` options:**

| Value | Behavior |
|---|---|
| `queue` | Messages are held and delivered at the next window start |
| `silent_deliver` | Messages are delivered silently (no alert, no badge) |
| `block` | Messages are rejected with an auto-reply |

---

### 4.3 Reachability Profile Schema

The **Reachability Profile** replaces traditional online/offline presence with conditional rules.

```json
{
  "user_id": "usr_8f3k2p",
  "reachability": {
    "base_mode": "async_preferred",
    "conditions": [
      {
        "reach_if": "topic_tagged_urgent",
        "via": ["direct_message"],
        "requires_reason": true
      },
      {
        "reach_if": "sender_in_group",
        "group": "immediate_family",
        "via": ["call", "direct_message"],
        "requires_reason": false
      },
      {
        "reach_if": "sender_is_role",
        "role": "on_call_engineer",
        "via": ["call"],
        "requires_reason": true
      }
    ],
    "default_fallback": {
      "action": "queue",
      "auto_reply": true,
      "auto_reply_template": "response_window_standard"
    }
  }
}
```

---

### 4.4 Interruption Request Schema

When a sender attempts a **synchronous interruption** (call, urgent ping), the system requires a structured request before delivery.

```json
{
  "request_id": "req_9a2m7z",
  "from_user": "usr_4d1n9q",
  "to_user": "usr_8f3k2p",
  "interrupt_type": "real_time_call",
  "reason": "Production deployment is failing, need decision on rollback.",
  "urgency_level": "high",
  "estimated_duration_minutes": 5,
  "sent_at": "2026-06-04T10:15:00Z",
  "ttl_seconds": 300,
  "passphrase_used": "URGENT_SILENCE"
}
```

**Rules:**

- `reason` field is **required** and non-empty for any `urgency_level` above `low`
- Requests expire after `ttl_seconds` if not accepted — they do not escalate automatically
- Systems must log all interruption requests for user review

---

### 4.5 Auto-Reply Template Structure

Auto-replies should be machine-readable as well as human-readable.

```json
{
  "template_id": "response_window_standard",
  "version": "1.0",
  "human_message": "Hi, I'm currently in a focus block and away from messages. I'll reply during my next response window: today between 13:00–13:30 WIB. If this is urgent, use the passphrase URGENT_SILENCE.",
  "machine_metadata": {
    "status": "unavailable",
    "next_available_at": "2026-06-04T13:00:00+07:00",
    "async_ok": true,
    "protocol_version": "silence-protocol/1.0"
  }
}
```

The `machine_metadata` block allows other systems (calendar apps, project management tools, CI/CD pipelines) to interpret availability programmatically.

---

### 4.6 Silence Mode Enum Reference

```json
{
  "silence_modes": {
    "available": {
      "description": "Fully reachable. Notifications delivered normally.",
      "default_notification_behavior": "immediate"
    },
    "deep_focus": {
      "description": "Active work session. No interruptions except emergencies.",
      "default_notification_behavior": "queue",
      "suggested_duration_minutes": 90
    },
    "do_not_disturb": {
      "description": "Deliberate rest or personal time.",
      "default_notification_behavior": "silent_deliver",
      "suggested_duration_minutes": null
    },
    "scheduled_away": {
      "description": "Planned absence — vacation, leave, off-hours.",
      "default_notification_behavior": "auto_reply",
      "requires_return_date": true
    },
    "offline": {
      "description": "Fully disconnected. No delivery.",
      "default_notification_behavior": "block"
    }
  }
}
```

---

## 5. Usage Scenarios

### Scenario A — Solo Developer in Deep Work

**Context:** A developer, Farhan, starts his 9:00 focus block. He is building a critical feature and cannot afford context switching.

**Flow:**

1. Farhan activates `deep_focus` mode via his IDE plugin or status app
2. His Silence Status Object is updated: `mode: deep_focus`, `active_until: 11:00`
3. A teammate sends him a Slack message at 9:45
4. Slack (implementing the protocol) queues the message — no badge, no sound
5. At 11:00, the session expires and Farhan's status returns to `available`
6. Queued messages are silently delivered — Farhan sees them when he's ready
7. His teammate sees the auto-reply: *"Farhan is in a focus block until 11:00. Message queued."*

**Result:** Farhan completes his session uninterrupted. His teammate is informed, not blocked.

---

### Scenario B — Team Adopting Response Windows

**Context:** A 6-person remote design team spans three time zones. Team members feel pressure to respond instantly to stay visible.

**Implementation:**

1. The team adopts a shared `response_windows` contract:
   - Morning sync window: 09:00–09:30 in each person's local time
   - Afternoon window: 15:00–15:30 in each person's local time
   - No expected responses outside these windows
2. Their project management tool reads each member's `next_available_at` field and marks tasks with estimated reply times instead of "seen" timestamps
3. A manager sends a question at 18:00 to a team member in Jakarta
4. The system queues delivery and shows: *"Delivered at next window: tomorrow 09:00 WIB"*
5. The manager receives no anxiety about whether the message was ignored

**Result:** Team communication becomes predictable. Social pressure to be "always on" is replaced by shared clarity about when responses will arrive.

---

### Scenario C — Emergency Escalation Bypass

**Context:** A production database goes down at 22:30. The on-call engineer needs to reach the senior backend developer immediately.

**Flow:**

1. Developer Siti has `do_not_disturb` mode active
2. The on-call engineer sends a call request with:
   - `reason`: "Database cluster unreachable, 3 services down, need infra access"
   - `urgency_level`: "high"
   - `passphrase_used`: "URGENT_SILENCE"
3. The system validates the passphrase and escalates the request
4. Siti's device receives a distinct emergency alert (different tone, bypass DND)
5. She joins the call within 2 minutes

**Without the protocol:** The engineer would have needed to call repeatedly, text multiple channels, and hope for the best — creating noise for everyone.

**With the protocol:** One structured request, one clear signal, one response.

---

### Scenario D — Platform Integration (API Consumer)

**Context:** A developer is building a team dashboard that shows member availability.

**API Call:**

```http
GET /api/v1/users/usr_8f3k2p/silence-status
Authorization: Bearer <token>
Accept: application/json
```

**Response:**

```json
{
  "user_id": "usr_8f3k2p",
  "display_name": "Rania",
  "silence_status": {
    "mode": "deep_focus",
    "next_available_at": "2026-06-04T11:00:00Z",
    "message": "In a focus block. I will reply after 11:00.",
    "async_ok": true
  },
  "protocol_version": "silence-protocol/1.0"
}
```

**The dashboard uses this to:**
- Display "🟡 Focus block — available at 11:00" instead of a red "offline" dot
- Disable the "@mention" button and replace it with "📩 Send async message"
- Show the team lead that Rania is working, not missing

---

## 6. Versioning & Compatibility

This specification follows **Semantic Versioning** (MAJOR.MINOR.PATCH).

| Version | Change type | Description |
|---|---|---|
| `1.0.0` | Initial release | Base schema definitions, 6 core principles |
| Future `1.x` | Backward-compatible | New optional fields, additional mode types |
| Future `2.0` | Breaking change | Revised core schema (migration guide required) |

Implementations should include a `protocol_version` field in all responses to support version negotiation between systems.

---

## 7. Glossary

| Term | Definition |
|---|---|
| **DPoM** | Digital Peace of Mind — the target state this protocol enables |
| **Silence Status** | The current machine-readable availability state of a user |
| **Response Window** | A declared time range during which a user actively processes messages |
| **Reachability Profile** | A conditional ruleset defining when and how a user can be interrupted |
| **Interruption Request** | A structured, justified request to contact a user synchronously |
| **Inverse Presence** | Declaring conditions for being reached, rather than broadcasting availability |
| **Focus Block** | A protected period of uninterrupted work, expressed as a silence mode |
| **Emergency Passphrase** | A pre-agreed keyword that unlocks contact during silence modes |
| **TTL** | Time-to-live — the duration after which an unacknowledged request expires |
| **Dark Pattern** | A design mechanism that exploits user psychology to encourage unwanted behavior |
| **Async-first** | A communication norm where asynchronous messages are the default, synchronous contact is the exception |

---

*This document is part of The Silence Protocol open-source project.*
*Contributions and feedback welcome via GitHub Issues and Pull Requests.*
*Licensed under MIT.*

