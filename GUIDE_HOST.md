# Host Guide — AI in Education: Central Tensions

Everything the facilitator needs to run the event.

---

## Before the Event

### 1. Set up the projector

Open `screen.svg` in a browser on the projector computer:
> **https://williamedwardhahn.github.io/ai-education-event/screen.svg**

Make it fullscreen (F11). It will show "Welcome," a scannable QR code, and a participant counter. The QR code points directly to `phone.svg` — attendees scan it to join. You never touch this computer again.

### 2. Set up the host panel

Open `host.svg` in a browser on your laptop:
> **https://williamedwardhahn.github.io/ai-education-event/host.svg**

This is your control panel for the entire event. Keep it open in a visible tab.

### 3. Set the initial phase

Click **"Welcome / Check-in"** in the left panel. The projector will show the welcome screen.

### 4. QR codes

The projector **already displays a scannable QR code** during the check-in phase. Attendees point their phone cameras at the big screen — no printing required.

**Optional:** For extra convenience, print QR codes for each table using [the QR tool](https://williamedwardhahn.github.io/web/qr.html) with this URL:
> **https://williamedwardhahn.github.io/ai-education-event/phone.svg**

Print them at least **3 inches** — people with reading glasses need large codes.

Attendees who have already joined can also tap **"Share"** on their phone to show a QR code for others to scan.

### 5. Test the system

Open `phone.svg` on your own phone. Check in with a test name. Verify the participant counter goes up on the projector. Then reset:

Click **"Reset All"** in the host panel (requires double-click to confirm). This clears all test data.

---

## During the Event

### Reception (5:15 PM)

People arrive and scan the QR code on the projector screen (or on printed table cards). They check in on their phones:
- Their name
- Their role (Educator / Researcher / Policymaker / Student / Other)
- Their table number (1-8)

Watch the projector — names appear in real time as people join. The participant counter grows. Early joiners can tap **"Share"** on their phone to show their QR code to latecomers.

**Your job:** Welcome people, point them to the projector QR, help anyone having trouble scanning.

### Kickoff (6:00 PM)

When you're ready to begin:

1. Click **"Tension 1"** in the host panel
2. Click **"Open Voting"**
3. Select a countdown timer: **60s**, **90s**, or **120s**

The projector shows: **"Cognitive offloading vs. Deep learning"** with an empty spectrum.

Say something like:

> *"AI can do a lot of our thinking for us — summarize a paper, solve a problem, write an email. Is that freeing us to think deeper? Or is it replacing the struggle that learning requires? Place yourself on the spectrum on your phone."*

### Voting (2-3 minutes)

People tap a position on the 5-point spectrum on their phones. As votes come in, dots appear on the projector spectrum in real time.

The countdown timer runs on both the projector and your panel. When it hits zero, voting closes automatically.

**Or:** Click **"Close Voting"** manually when you see enough votes.

### Table Discussion (10-15 minutes)

Once voting closes:
- The projector shows the vote distribution
- Phones show a **table notepad** — each table can write shared notes
- The discuss prompt reads: *"What is the strongest argument for each side?"*

**Your job:**
- Look at the **Questions** panel on your laptop — questions are sorted by upvote count
- Click the **★ star** button on the best questions to highlight them (gold border on projector)
- After 5 minutes, read the top 2-3 questions to the room and let tables respond
- Check the **Table Notes** section to see what tables are writing

### Revote (2 minutes)

After table discussion, click **"Revote"** in the host panel.

Phones show: *"REVOTE — has your position changed?"* with the person's original vote displayed.

People can shift their position or keep it. The projector shows dual spectrums:
- **Blue dots** = initial positions
- **Gold dots** = after discussion
- **Arrow** shows how the room's mean shifted

This is the most powerful moment. Say:

> *"Look at the shift. The room moved from X.X to Y.Y. Let's talk about why."*

Click **"Close Revote"** when done.

### Advance to next tension

Click **"Tension 2"** and repeat the cycle:
1. Open Voting → vote → close
2. Table discussion with notepad
3. Revote → see shift → close

### Timing guide

| Phase | Duration | Host action |
|-------|----------|-------------|
| Tension intro | 1 min | Frame the tension verbally |
| Voting | 2 min | Open voting, set 90s timer |
| Discussion | 12 min | Star top questions, monitor table notes |
| Revote | 2 min | Open revote, close after 90s |
| Transition | 1 min | Click next tension |
| **Total per tension** | **~18 min** | |

For 4 tensions: ~72 minutes + 8 minutes for results = 80 minutes total.

### Results (7:20 PM)

Click **"Results"** in the host panel.

The projector shows a narrative synthesis:
- **Most Divided** — the tension where the room disagreed most
- **Strongest Consensus** — where the room agreed most
- **Biggest Shift** — where minds changed most after discussion
- **Question of the Night** — the most upvoted question
- Four mini spectrum charts showing initial vs. revised positions

Use these as prompts for a final 5-minute closing discussion:

> *"We were most divided on [tension]. Why do you think that is? And we shifted most on [tension] — what argument changed your mind?"*

### Data export

Click **"Download Data"** in the host panel to save all event data as a JSON file. This captures:
- All check-ins (names, roles, tables)
- All votes (initial + revotes, per tension)
- All questions with upvote counts
- All comments
- All table notes
- Event state history

---

## Troubleshooting

### "Nobody's votes are showing up"

Check that you clicked "Open Voting" — the vote buttons are grayed out on phones when voting is closed.

### "The projector is blank"

Make sure `screen.svg` is open in the browser (not in an image viewer). It must be opened directly as a file or via a URL — not embedded in a slide deck.

### "Someone can't scan the QR code"

Three fallbacks:
1. Ask a neighbor who already joined to tap **"Share"** on their phone and hold it up to scan
2. Give them the URL to type manually: `williamedwardhahn.github.io/ai-education-event/phone.svg`
3. Send the link via text message, email, or Slack

### "WiFi is slow"

The system polls every 2 seconds. If WiFi degrades:
- Votes and questions still go through, just with delay
- The projector may lag a few seconds behind reality
- **Fallback:** Ask for a show of hands and count manually

### "I need to redo a tension"

Click the tension button again. Voting data from the previous round is preserved — new votes overwrite per-user, so people can just re-vote.

### "I accidentally clicked Reset All"

It requires a double-click (first click primes, second confirms). If you did reset: the data is gone, but you can restart cleanly.

### "The projector shows old data from a test"

Click "Reset All" in the host panel before the event starts.

---

## After the Event

1. Click **"Download Data"** to export the JSON
2. Screenshot the results screen
3. The data persists in statevec.com for 24 hours (TTL), then auto-expires
4. If you need to preserve it longer, the JSON export is your permanent record

---

## Quick Reference Card

Print this and tape it to your laptop during the event.

```
FLOW: Welcome → T1 → T2 → T3 → T4 → Results

PER TENSION:
  1. Click tension button
  2. Click "Open Voting" + set timer
  3. Wait for votes (watch countdown)
  4. Voting auto-closes at 0 (or click "Close Voting")
  5. Table discussion — star top questions
  6. Click "Revote" when discussion winds down
  7. Close revote after 90s
  8. Click next tension

CONTROLS:
  Open/Close Voting  — green/default button
  Revote             — gold button (below voting toggle)
  Star question      — ★ button next to each question
  Timer presets      — 60s / 90s / 120s
  Reset All          — double-click red button
  Download Data      — blue button (bottom right)
```
