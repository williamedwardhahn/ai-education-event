# AI in Education: Central Tensions

**MPCR Labs Round Table Series**
**Tuesday, April 7, 2026 — 5:15 PM Reception, 6:00 PM Kickoff**
**The Gruber Sandbox, FAU Boca Raton Campus**

A guided roundtable debate on where AI is supporting learning — and where it may be quietly undermining it. Participants use their phones to vote, ask questions, and capture table discussions. A live projector dashboard shows the room's collective intelligence in real time.

## The 4 Tensions

1. **Cognitive offloading** vs. **deep learning**
2. **Personalization** vs. **belonging**
3. **Assistance** vs. **authorship**
4. **Innovation** vs. **governance**

## The System

Three SVG living documents coordinating through [statevec.com](https://statevec.com):

| File | Who | What |
|------|-----|------|
| `phone.svg` | Attendees (phone) | Check in, vote on spectrum, ask questions, comment, table notepad, revote |
| `host.svg` | Facilitator (laptop) | Advance tensions, open/close voting, revote, highlight questions, timer, export |
| `screen.svg` | Projector (big screen) | Live votes, questions, comments, table notes, vote shift, narrative results |

## Guides

| Document | For |
|----------|-----|
| [GUIDE_HOST.md](GUIDE_HOST.md) | **Facilitator** — setup, flow, timing, troubleshooting, quick reference card |
| [GUIDE_PARTICIPANT.md](GUIDE_PARTICIPANT.md) | **Attendees** — how to scan, vote, ask, discuss, revote |

## Per-Tension Flow

```
1. Frame the tension (facilitator speaks)
2. Open Voting → participants vote on 5-point spectrum (90s timer)
3. Close Voting → table discussion begins
   - Table notepad active on phones
   - Facilitator stars top questions
4. Revote → participants can shift their position after discussion
5. Close Revote → projector shows initial vs revised with shift arrows
6. Advance to next tension
```

## Architecture

```
phone.svg  ──PATCH merge──►  statevec.com  ◄──GET──  screen.svg
host.svg   ──PUT──────────►       │
                                  │
                         (6 shared channels)
```

| Channel | Secret | Who writes | Data |
|---------|--------|-----------|------|
| State | `mpcr:ai:state` | Host | Phase, current tension, voting/revote open |
| Checkins | `mpcr:ai:checkins` | Phones | Name, role, table per participant |
| Votes | `mpcr:ai:votes` | Phones | `tension0:userId` = 1-5, `revote0:userId` = 1-5 |
| Questions | `mpcr:ai:questions` | Phones | Question text + `upvote:qId:userId` flat keys |
| Comments | `mpcr:ai:comments` | Phones | Comment text, author, tension |
| Tables | `mpcr:ai:tables` | Phones | `table1:tension0` = shared notes text |

All phone writes use PATCH merge with flat top-level keys (shallow merge safe).

## Setup Checklist

- [ ] Open `host.svg` on facilitator laptop
- [ ] Open `screen.svg` on projector (fullscreen F11)
- [ ] Generate QR code for `phone.svg` URL → [QR tool](https://williamedwardhahn.github.io/web/qr.html)
- [ ] Print QR codes for tables (3+ inches, large enough for reading glasses)
- [ ] Test: scan QR on your phone, check in, verify projector shows your name
- [ ] Reset all test data (double-click "Reset All" in host panel)
- [ ] Print facilitator quick reference card from [GUIDE_HOST.md](GUIDE_HOST.md)

## Hosted by

**Machine Perception & Cognitive Robotics (MPCR) Lab**
FAU Boca Raton Campus
[MPCRLab.com](https://mpcrlab.com)

## Technology

Built with [statevec](https://statevec.com) — zero-auth state sharing for agents and living documents. No accounts, no app, no server to configure. Open a file, you're in.
