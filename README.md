# AI in Education: Central Tensions

**MPCR Labs Round Table Series**
**Tuesday, April 7, 2026 — 6:00 PM**
**The Gruber Sandbox, FAU Boca Raton**

A guided roundtable debate on where AI is supporting learning — and where it may be quietly undermining it.

## The 4 Tensions

1. **Cognitive offloading** vs. **deep learning**
2. **Personalization** vs. **belonging**
3. **Assistance** vs. **authorship**
4. **Innovation** vs. **governance**

## The System

Three SVG living documents coordinating through [statevec.com](https://statevec.com):

| File | Who uses it | What it does |
|------|------------|--------------|
| `phone.svg` | Attendees (phone) | Check in, vote on spectrum, ask questions, post comments |
| `host.svg` | Facilitator (laptop) | Advance tensions, open/close voting, highlight questions |
| `screen.svg` | Projector (big screen) | Live dashboard — votes, questions, comments, participant count |

## Setup

### Before the event

1. Open `host.svg` on the facilitator's laptop
2. Click "Welcome / Check-in" to set the phase
3. Open `screen.svg` on the projector — it shows the welcome screen
4. Generate a QR code pointing to the hosted `phone.svg` URL using [the QR tool](https://williamedwardhahn.github.io/web/qr.html)
5. Display the QR code on the projector or print it for tables

### During the event

| Time | Action |
|------|--------|
| 5:15 PM | Reception — QR codes on tables, people scan and check in |
| 6:00 PM | Host clicks "Tension 1" + "Open Voting" |
| | Attendees vote on spectrum, submit questions |
| | Facilitator highlights top questions for discussion |
| | Table discussion (10-15 min) |
| | Host clicks "Close Voting" |
| 6:20 PM | Host clicks "Tension 2" + "Open Voting" — repeat |
| 6:40 PM | Tension 3 |
| 7:00 PM | Tension 4 |
| 7:20 PM | Host clicks "Results" — summary on projector |

### After the event

The `screen.svg` results view shows all vote distributions and stats. Screenshot it or leave it open.

## How it works

All three SVGs coordinate through [statevec.com](https://statevec.com) — a shared state service where a secret gives write access and its SHA-256 hash gives read access.

```
phone.svg  ──PATCH──►  statevec.com  ◄──GET──  screen.svg
host.svg   ──PUT────►       │
                             │
                    (shared state)
```

- **Phone** writes checkins, votes, questions, comments (PATCH merge — multi-writer safe)
- **Host** writes event state: current tension, voting open/closed (PUT — single writer)
- **Screen** reads everything, writes nothing

No accounts. No server to configure. No app to install. Open a file, you're in.

## Secrets

| Channel | Secret | Purpose |
|---------|--------|---------|
| State | `mpcr:ai:state` | Event flow (host only) |
| Checkins | `mpcr:ai:checkins` | Participant list |
| Votes | `mpcr:ai:votes` | Spectrum votes per tension |
| Questions | `mpcr:ai:questions` | Questions with upvotes |
| Comments | `mpcr:ai:comments` | Discussion comments |

## Reset

To clear all data and start fresh, the host clicks "Reset All" in `host.svg`. This clears state, votes, questions, and comments.

## Hosted by

**Machine Perception & Cognitive Robotics (MPCR) Lab**
FAU Boca Raton Campus
[MPCRLab.com](https://mpcrlab.com)
