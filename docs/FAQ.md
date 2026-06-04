# Frequently Asked Questions

**The Silence Protocol — FAQ**

> Can't find your answer here? [Open a Discussion](../../discussions) or email us at Hyra549@proton.me.

---

## Table of Contents

**The Basics**
- [What exactly is The Silence Protocol?](#what-exactly-is-the-silence-protocol)
- [Who is this for?](#who-is-this-for)
- [Is this a product I can download?](#is-this-a-product-i-can-download)
- [Is it free to use?](#is-it-free-to-use)

**Notifications & Availability**
- [Does this mean turning off all notifications forever?](#does-this-mean-turning-off-all-notifications-forever)
- [What if someone sends me something truly important?](#what-if-someone-sends-me-something-truly-important)
- [What happens to messages I miss during a silence block?](#what-happens-to-messages-i-miss-during-a-silence-block)
- [Can I still check messages whenever I want?](#can-i-still-check-messages-whenever-i-want)

**Emergency Situations**
- [What about genuine emergencies?](#what-about-genuine-emergencies)
- [What if I am the on-call person for my team?](#what-if-i-am-the-on-call-person-for-my-team)
- [What if a family member needs to reach me urgently?](#what-if-a-family-member-needs-to-reach-me-urgently)
- [Won't people just override the silence anyway?](#wont-people-just-override-the-silence-anyway)

**Teams & Organizations**
- [How does this work for remote teams?](#how-does-this-work-for-remote-teams)
- [What if my manager doesn't support this?](#what-if-my-manager-doesnt-support-this)
- [How do we handle time-sensitive decisions that can't wait?](#how-do-we-handle-time-sensitive-decisions-that-cant-wait)
- [How do we onboard a new team to the Protocol?](#how-do-we-onboard-a-new-team-to-the-protocol)
- [What about clients or external stakeholders?](#what-about-clients-or-external-stakeholders)

**Tools & Apps**
- [Is there a client app I can install?](#is-there-a-client-app-i-can-install)
- [Does it integrate with Slack, Teams, or other tools?](#does-it-integrate-with-slack-teams-or-other-tools)
- [Can I use this with my phone's existing Do Not Disturb settings?](#can-i-use-this-with-my-phones-existing-do-not-disturb-settings)
- [Is there an API?](#is-there-an-api)

**Philosophy & Concerns**
- [Isn't this just glorified DND mode?](#isnt-this-just-glorified-dnd-mode)
- [What if I feel guilty for not responding faster?](#what-if-i-feel-guilty-for-not-responding-faster)
- [What if my team sees my silence as laziness?](#what-if-my-team-sees-my-silence-as-laziness)
- [Is this realistic in high-pressure industries?](#is-this-realistic-in-high-pressure-industries)

**Contributing**
- [How can I contribute to this project?](#how-can-i-contribute-to-this-project)
- [I disagree with one of the principles. Can I fork this?](#i-disagree-with-one-of-the-principles-can-i-fork-this)

---

## The Basics

---

### What exactly is The Silence Protocol?

The Silence Protocol is an **open-source framework** — a set of principles, rules, data schemas, and templates — that helps people and teams define healthy digital communication boundaries.

Think of it as a shared agreement about *when* and *how* to reach people, combined with technical tools to actually enforce those agreements in the software you already use.

It covers three layers:
- **Personal habits** — how you structure your own attention and availability
- **Social norms** — agreements your team makes about communication expectations
- **Technical standards** — data formats and patterns that let software respect those agreements

It is not a single application. It is a protocol — like how email has standards that different clients all follow.

---

### Who is this for?

The protocol is useful for:

- **Knowledge workers** who need uninterrupted time to think, write, or build
- **Remote and distributed teams** where communication spans time zones
- **Developers and designers** who want to build tools that respect human attention
- **Organizations** looking to reduce burnout and improve communication clarity
- **Individuals** who feel overwhelmed by digital noise and want a framework to push back

You don't need to be technical to benefit from the personal and team-level parts of the protocol. The technical specifications are there for developers who want to build tools that implement the protocol at the software level.

---

### Is this a product I can download?

Not as a single product — and that is intentional.

The Silence Protocol lives in this repository as **documentation, templates, and tools**. What you "install" depends on what you need:

| What you want | Where to go |
|---|---|
| Personal boundary rules and templates | [`/templates/`](../templates/) |
| Team communication contract | [`/templates/communication-contract.md`](../templates/communication-contract.md) |
| Workshop guides for your team | [`/workshops/`](../workshops/) |
| CLI tools and notification configs | [`/tools/`](../tools/) |
| Technical schemas for building apps | [Technical Spec](technical-spec.md) |

If you're looking for a ready-made app that implements these ideas, check the [community integrations list](integrations.md) for third-party tools built on top of this protocol.

---

### Is it free to use?

Yes, completely. The Silence Protocol is licensed under the **MIT License**, which means you can use, adapt, fork, and distribute it — including in commercial products — as long as you include the original license notice.

See [`LICENSE`](../LICENSE) for the full text.

---

## Notifications & Availability

---

### Does this mean turning off all notifications forever?

No. That is not the goal, and doing so would likely cause more anxiety, not less.

The protocol does not ask you to eliminate notifications. It asks you to **take control of them** — to decide which ones reach you, when, and through what channel.

The difference is:

| Reactive (before the protocol) | Intentional (with the protocol) |
|---|---|
| Every app can notify you at any time | You define specific windows for receiving alerts |
| Urgency is decided by the sender | Urgency must be declared and justified |
| Silence feels like absence | Silence is a visible, communicated state |
| You react to whatever arrives | You check in on your own schedule |

The goal is **notification on your terms**, not silence as punishment.

---

### What if someone sends me something truly important?

That is exactly what the **emergency passphrase** and **Reachability Profile** are designed for.

Every user can define conditions under which they *will* be interrupted, even during a silence block. For example:

- "Reach me immediately if you use the phrase `PROTOCOL_URGENT`"
- "Always put calls from my partner through, regardless of my mode"
- "If this is a production incident, tag it `[P0]` and it will reach me"

These conditions are declared in advance, shared with your team, and respected by the system. Important messages still get through — they just need to *earn* the interruption, rather than assuming it.

---

### What happens to messages I miss during a silence block?

Messages are **queued, not deleted**. They are delivered at the start of your next Response Window — silently, without a push notification storm — so you can review them when you are ready.

Your auto-reply lets senders know:

1. That you received their message
2. That you are currently in a silence mode
3. When you will be available to respond
4. How to reach you if it truly cannot wait

Nothing is lost. The only thing that changes is *when* you see it and *how much cognitive load* it creates.

---

### Can I still check messages whenever I want?

Yes. The protocol manages *incoming interruptions*, not your access to your own inbox.

You are always free to open an app and read messages when you choose to. The protocol simply ensures that those messages do not pull your attention away from you *before* you are ready. The difference between choosing to check and being interrupted is significant — one preserves autonomy, the other erodes it.

---

## Emergency Situations

---

### What about genuine emergencies?

The protocol has a built-in escalation path for real emergencies. It works like this:

1. **Emergency passphrase** — A pre-agreed word or phrase that, when included in a message or call request, bypasses the silence mode and delivers the alert immediately. You share this passphrase only with people who should have it.

2. **Reachability conditions** — You can pre-define roles or relationships that always get through (e.g., your child's school, your on-call rotation partner, your co-founder).

3. **Escalation request** — For platforms implementing the full technical spec, senders can submit a structured Interruption Request with a reason and urgency level. If it meets the user's criteria, it is escalated.

The key insight is: **genuine emergencies are rare**. Most things that feel urgent are not. The protocol creates a structure that makes the difference between the two explicit — and that makes real emergencies easier to recognize, not harder.

---

### What if I am the on-call person for my team?

On-call duties are a first-class use case in the protocol.

When you are on-call, you set your Reachability Profile to reflect that:

```json
{
  "reach_if": "sender_is_role",
  "role": "on_call_engineer",
  "via": ["call"],
  "requires_reason": true
}
