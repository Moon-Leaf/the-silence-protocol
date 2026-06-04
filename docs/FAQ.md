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
| Personal boundary rules and templates | [`/templates/`](templates/) |
| Team communication contract | [`/templates/communication-contract.md`](templates/communication-contract.md) |
| Workshop guides for your team | [`/workshops/`](workshops/) |
| CLI tools and notification configs | [`/tools/`](tools/) |
| Technical schemas for building apps | [`/docs/technical-spec.md`](docs/technical-spec.md) |

If you're looking for a ready-made app that implements these ideas, check the [community integrations list](docs/integrations.md) for third-party tools built on top of this protocol.

---

### Is it free to use?

Yes, completely. The Silence Protocol is licensed under the **MIT License**, which means you can use, adapt, fork, and distribute it — including in commercial products — as long as you include the original license notice.

See [`LICENSE`](LICENSE) for the full text.

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
```

Your silence mode does not need to change — you are still protected from routine interruptions. But the on-call escalation path is explicitly open. Your team knows how to reach you, your phone will alert you, and the rest of your attention remains intact until it is actually needed.

---

### What if a family member needs to reach me urgently?

This is one of the most important scenarios the protocol supports.

You define a contact group — "immediate family," for example — and specify that calls or messages from this group bypass your silence mode entirely. You share this with your family as part of setting up your profile.

```json
{
  "reach_if": "sender_in_group",
  "group": "immediate_family",
  "via": ["call", "direct_message"],
  "requires_reason": false
}
```

Your family always gets through. Your coworker's "quick question" does not.

---

### Won't people just override the silence anyway?

The protocol works best when adopted as a **shared social agreement**, not just a personal setting.

When your team has collectively agreed that silence modes will be respected, the social pressure to over-ride them shifts significantly. Bypassing someone's focus block becomes the exception that requires justification — not the default.

For individuals operating in environments without a team agreement, the protocol still provides value at the personal level. However, like any social norm, its full power emerges when the people around you also understand and respect it.

---

## Teams & Organizations

---

### How does this work for remote teams?

Remote teams are actually the *ideal* use case for this protocol. Distributed work already forces asynchronous habits — the protocol gives those habits a clear structure.

For remote teams, the key implementations are:

**1. Shared Response Windows**
Each team member publishes their response windows. A shared team calendar or dashboard shows when each person is in their check-in windows versus focus blocks.

**2. Time Zone Transparency**
The `timezone` field in all schedule objects makes it unambiguous what "09:00" means for each person. No more accidental late-night pings.

**3. Async-First Communication Norms**
The team agrees that the default channel for non-urgent work is async (written message, task comment, document). Synchronous communication (video calls, real-time chat) is reserved for things that genuinely benefit from it.

**4. Communication Contract**
A written agreement — adapted from the template in [`/templates/communication-contract.md`](templates/communication-contract.md) — that the team signs collectively and revisits quarterly.

---

### What if my manager doesn't support this?

Start with a conversation, not a policy.

Frame it around outcomes your manager cares about: fewer dropped balls, deeper work, reduced burnout, better predictability on timelines. The protocol is not "I will be less available." It is "I will be *predictably* available, and more effective in between."

A useful starting point: propose a **30-day experiment** with a single element of the protocol — such as defined response windows for one team channel. Measure the impact, then build from there.

The workshop in [`/workshops/noise-audit.md`](workshops/noise-audit.md) is designed specifically to facilitate this conversation with leadership.

---

### How do we handle time-sensitive decisions that can't wait?

Not everything is async. The protocol acknowledges this.

The goal is not to make every decision slow — it is to make the *distinction* between urgent and non-urgent explicit. Decisions that genuinely require real-time input use the synchronous channels that the Reachability Profile keeps open.

A practical heuristic used by many teams:

> **"If a 4-hour delay would cause real, measurable harm — escalate. If not — async."**

Most things that feel urgent do not meet that bar. Making the bar explicit removes the ambient pressure to treat everything as if it does.

---

### How do we onboard a new team to the Protocol?

The recommended onboarding path is:

1. **Run the Noise Audit workshop** (60 minutes) to map your current communication pain points — [`/workshops/noise-audit.md`](workshops/noise-audit.md)
2. **Read the Team Protocol guide together** — [`/docs/team-protocol.md`](docs/team-protocol.md)
3. **Draft your Communication Contract** as a team — [`/templates/communication-contract.md`](templates/communication-contract.md)
4. **Start with one principle** for the first two weeks (recommended: Response Windows)
5. **Hold a retrospective** at week 2 and week 6 using the review template — [`/workshops/quarterly-review.md`](workshops/quarterly-review.md)

Trying to implement everything at once typically fails. Incremental adoption, with reflection built in, has a much higher success rate.

---

### What about clients or external stakeholders?

External parties who are not part of your team agreement require a different approach.

Recommended practices:

- **Set expectations upfront.** Include your response window in your email signature: *"I check email at 09:00 and 15:00 WIB on weekdays."*
- **Use auto-replies proactively.** Structure your out-of-office to include a `next_available_at` time, not just a vague "I'll get back to you."
- **Define an escalation path.** For clients with genuine urgency needs, provide a dedicated contact or channel that bypasses your default response window.

Clients adapt quickly when expectations are clear and consistently met. Unpredictability — not deliberate response windows — is what erodes trust.

---

## Tools & Apps

---

### Is there a client app I can install?

Not yet — but it is on the roadmap.

Currently, the protocol is implemented through:

- **Configuration files and templates** you apply manually or semi-manually
- **OS-level DND settings** mapped to the protocol's silence modes (configs in [`/tools/notification-configs/`](tools/notification-configs/))
- **A CLI focus timer** for triggering silence modes from the terminal — [`/tools/focus-timer/`](tools/focus-timer/)
- **A Slack bot** that reads and respects team Response Windows — [`/tools/slack-etiquette-bot/`](tools/slack-etiquette-bot/)

A native cross-platform desktop client and a mobile companion app are planned for a future release. If you want to help build them, check [`CONTRIBUTING.md`](CONTRIBUTING.md).

---

### Does it integrate with Slack, Teams, or other tools?

Partially, and growing.

| Platform | Current support | Status |
|---|---|---|
| **Slack** | Status sync, message queuing bot | 📝 Planned / Roadmap |
| **Apple/macOS Focus Modes** | DND profile mapping | ✅ Available |
| **Android DND** | Schedule config templates | ✅ Available |
| **Microsoft Teams** | Manual status mapping guide | 📄 Docs only |
| **Notion / Linear** | Availability widget templates | 📄 Docs only |
| **Calendar integrations** | Focus block to calendar sync | 🔜 Planned |
| **Native mobile app** | Full protocol management | 🔜 Planned |

Contributions for new integrations are very welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md) to get started.

---

### Can I use this with my phone's existing Do Not Disturb settings?

Yes — and this is the recommended starting point for most people.

Your phone's DND settings can be mapped directly to silence modes in the protocol:

| Protocol Mode | iOS Focus equivalent | Android DND equivalent |
|---|---|---|
| `deep_focus` | Focus: Work | Priority Only |
| `do_not_disturb` | Focus: Personal / Sleep | Total Silence |
| `scheduled_away` | Scheduled Focus | Scheduled DND |
| `available` | Focus off | DND off |

Pre-configured profiles for both platforms are in [`/tools/notification-configs/`](tools/notification-configs/). They set up allowed contacts, allowed apps, and emergency bypass rules consistent with the protocol's principles.

---

### Is there an API?

The protocol defines a **specification** for what an API should look like — the schemas, fields, and behaviors described in [`/docs/technical-spec.md`](docs/technical-spec.md).

A reference implementation API server is currently in development. It will allow:

- Reading and writing a user's Silence Status Object
- Querying a user's Response Windows and Reachability Profile
- Submitting Interruption Requests
- Retrieving auto-reply templates

If you want to implement the API in your own stack before the reference server is available, the technical spec has everything you need to build it from scratch.

---

## Philosophy & Concerns

---

### Isn't this just glorified DND mode?

DND mode is a binary switch — it is either on or off, and it gives no information to the people trying to reach you.

The Silence Protocol goes significantly further:

| Do Not Disturb | The Silence Protocol |
|---|---|
| On/off switch | Structured modes with context |
| No information to sender | Clear auto-reply with return time |
| All contacts treated equally | Reachability conditions per relationship |
| No emergency path | Emergency passphrase system |
| Personal tool only | Shared team agreement layer |
| Device-level only | Cross-platform, integration-ready schema |

Think of DND as a lock. The Silence Protocol is the lock, the door, the mailbox, the intercom, and the sign on the front — a complete system, not just a single mechanism.

---

### What if I feel guilty for not responding faster?

This is one of the most common and honest concerns — and it points to something real.

The pressure to respond instantly is not just external. Many people have internalized it deeply, and setting boundaries can trigger genuine discomfort: anxiety about being seen as unhelpful, fear of missing something important, or guilt about making others wait.

A few things worth knowing:

- **Fast responses train people to expect fast responses.** Every time you reply in 2 minutes, you reset the expectation. Changing the pattern takes time, but it is possible.
- **Response windows provide cover.** When your team knows you check messages at 09:00 and 13:00, your 4-hour reply time is not rudeness — it is the system working as designed.
- **Guilt is often about approval, not actual harm.** Ask yourself: has someone been concretely harmed by waiting a few hours? Usually the answer is no.

The protocol gives you a structure to point to. "I don't respond immediately" is hard to defend alone. "Our team has a response window system" is a norm, not a personal failing.

---

### What if my team sees my silence as laziness?

Visibility anxiety — the fear that being unreachable makes you look unproductive — is widespread in remote and hybrid work environments.

The protocol addresses this directly through **Transparent Unavailability**. Your silence mode communicates:

- That you are actively working (not absent)
- What you are focused on (a focus block, a deep work session)
- When you will return (a concrete time, not a vague "later")

A green Slack dot signals that you are *online*. A `deep_focus` status signals that you are *working*. These are not the same thing, and the protocol makes the distinction visible.

Over time, teams that adopt the protocol typically find the opposite: people who protect their focus time produce higher-quality work, and that becomes the visible output that earns trust.

---

### Is this realistic in high-pressure industries?

Yes — and in some ways, high-pressure environments benefit the most from it.

Industries like healthcare, emergency services, and infrastructure operations already have highly evolved escalation systems precisely because they understand that not everything can be treated as maximum urgency. The Silence Protocol applies the same logic to knowledge work.

The question is not whether your industry is "too important" for boundaries — it is whether your current communication culture is actually producing better outcomes than a structured alternative would.

Some practical adaptations for high-pressure contexts:

- **Shorter response windows** (e.g., every 2 hours instead of twice a day)
- **Larger emergency passphrase groups** (more people with bypass access)
- **Role-based availability** (on-call rotations that explicitly open reachability)
- **Tiered urgency channels** (a dedicated `#urgent` channel that triggers alerts regardless of mode)

The protocol is a framework with adjustable parameters, not a rigid prescription.

---

## Contributing

---

### How can I contribute to this project?

Many ways — technical and non-technical alike:

- **Share your experience:** Used the protocol personally or with your team? Write it up as a case study in [`/research/case-studies/`](research/case-studies/)
- **Improve the docs:** Fix typos, clarify confusing passages, add examples
- **Build tools:** Implement integrations, scripts, or browser extensions
- **Translate:** Help make the protocol accessible in other languages
- **Run a workshop:** Facilitate the Noise Audit with your team and document what you learned
- **Open issues:** Spotted a gap in the framework? Disagree with something? Open a GitHub issue

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for guidelines, and [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) for community standards.

---

### I disagree with one of the principles. Can I fork this?

Absolutely. That is one of the best things about an open-source framework.

Fork the repository, adapt the principles to your context, and build your own variant. If you think your changes would benefit the wider community, open a Pull Request and start a conversation — disagreement that is well-reasoned and kindly expressed is one of the most valuable things an open project can receive.

The only thing we ask is that forks clearly distinguish themselves from the upstream project to avoid confusion about what "The Silence Protocol" means in its original form.

---

<div align="center">

*Still have questions? [Open a Discussion](../../discussions) or email Hyra549@proton.me — we read everything.*

**[Back to README](README.md) · [Read the Docs](docs/) · [Technical Spec](docs/technical-spec.md)**

</div>

