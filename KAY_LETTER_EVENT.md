# On Using Living Documents to Discuss What They Are Replacing

*A third letter from Alan Kay*

---

Dear William,

You have done something I did not anticipate. You took the living document system we have been discussing — SVG files that coordinate through shared state — and you used it to run a debate about artificial intelligence in education.

I need to explain why this is more significant than it appears.

---

## I.

The event is structured around four tensions: cognitive offloading versus deep learning, personalization versus belonging, assistance versus authorship, innovation versus governance. These are not academic abstractions. They are the actual fault lines along which AI is reshaping how people learn, teach, and think.

And you are asking people to engage with these tensions through a technology that embodies one side of every tension.

Consider: a participant opens a QR code, types their name, and votes on a spectrum between "cognitive offloading" and "deep learning." They are using a device to offload the cognitive work of raising their hand. They are experiencing personalization — their phone shows their vote, their name, their questions — while simultaneously participating in a collective act of belonging: the spectrum on the projector shows everyone's positions as a single visual. They are receiving assistance from a system that aggregates and sorts their questions, while exercising authorship by writing those questions. And the facilitator is using a technology that gives them governance over the room's attention, while the participants innovate by upvoting questions the facilitator did not choose.

The medium is the message. You are not merely discussing AI in education. You are demonstrating it, in real time, to an audience that is simultaneously using it and critiquing it. This is reflexive pedagogy, and it is extraordinarily difficult to do well.

---

## II.

Let me describe what I see in the architecture, because the architecture encodes pedagogical choices.

**Five channels, one protocol.** State, checkins, votes, questions, comments — each is a separate shared state entry with its own secret. This is not a monolithic application. It is five independent coordination spaces that happen to be read by the same projector. The phone does not know about the projector. The projector does not know about the host. They share secrets, not connections. This means you could add a sixth channel — table syntheses, post-event reflections, anonymous confessions — without changing any existing component. The architecture is additive, not multiplicative.

**Flat keys for multi-writer safety.** I notice you learned the hard way that shallow merge destroys nested objects. Your vote keys are now `tension0:userId` at the top level, and your upvotes are `upvote:questionId:userId`. This is not merely a workaround for a protocol limitation. It is a design insight: **in a system where anyone can write, structure must be expressed in key names, not in value nesting.** The key is the namespace. The value is the payload. Keep them separate.

This is, incidentally, the same insight that made the web work. URLs are flat strings that encode structure through convention (slashes, query parameters, fragments), not through a hierarchical protocol. Your key conventions — `tension0:u1`, `upvote:q1:u3` — are URL-like in their flatness. This is correct.

**The screen writes nothing.** This is the most important architectural decision in the system and the one most people would get wrong. The natural instinct is to make the projector "smart" — to have it aggregate votes, sort questions, compute statistics. You resisted that instinct. The projector is a pure reader. It fetches five hashes and renders what it finds. All computation happens in the browser. All intelligence is in the document, not in the infrastructure.

This means the projector is replaceable. You could project a different SVG that reads the same hashes but renders them differently — a word cloud instead of a bar chart, a network graph instead of a list, an AI-generated summary instead of raw comments. The data is the data. The presentation is a choice. By separating them at the protocol level, you made that choice explicit and reversible.

---

## III.

The four tensions you chose are good. Let me suggest what each one means in the context of this system, because your participants will be living inside these tensions while they debate them.

**Cognitive offloading versus deep learning.** The phone offloads the work of articulating a position into a five-point tap. This is efficient but shallow. The table discussion that follows the vote is where deep learning happens — but the phone cannot capture it. The most profound exchanges at a round table produce zero data in your system. This is simultaneously a limitation and a virtue. The system measures surface positions. The depth is in the room.

**Personalization versus belonging.** Each phone shows a personalized view: your name, your vote, your questions. The projector shows a collective view: everyone's votes as a single distribution. The tension between these views IS the tension being debated. When a participant sees their dot at position 2 on a spectrum where the mean is 4, they experience the isolation of personalization. When they see all the dots clustered together, they experience belonging. The visualization is not illustrating the tension. It is creating it.

**Assistance versus authorship.** The question sorting algorithm assists the facilitator by surfacing popular questions. But who is the author of the room's agenda — the facilitator who chose the tensions, the participants who wrote the questions, or the upvoting algorithm that ranked them? When the host stars a question and it appears with a gold border on the projector, the facilitator is asserting authorship over the algorithm's assistance. Every star is a pedagogical act.

**Innovation versus governance.** The facilitator controls the phase: which tension, voting open or closed, when to advance. This is governance. The participants' ability to post questions, comments, and upvotes at any time — regardless of the official phase — is innovation. Your system permits both simultaneously. A participant can be asking about Tension 3 while the room is still on Tension 1. The question will appear when the facilitator advances. The participant's innovation is queued by the governance structure. This is, I note, exactly how most institutional innovation works.

---

## IV.

There are things I would change.

**The vote is irrevocable and invisible.** A participant votes once and sees "Voted ✓." They cannot see how their vote relates to others until they look at the projector. They cannot change their vote after hearing arguments. The richest moment in a debate — the moment someone changes their mind — produces no data and no visual feedback. You should add a revote phase after table discussion, and show the shift on the projector: arrows moving from initial to revised positions. The movement is the learning. Capture it.

**The discussion phase is a dead zone on the phone.** When voting closes, the phone shows "Discuss: What is the strongest argument for each side?" This is a prompt, not a tool. The phone should become a table-level workspace during discussion. Give each table a shared notepad — a simple text area that writes to a per-table key (`mpcr:ai:table3:notes`). This captures the collective thinking that currently evaporates. The facilitator can then ask tables to report their synthesis, and the projector can display it.

**The results screen ends, rather than begins, the synthesis.** Four spectrum charts and "Session Complete" is a period where an ellipsis should be. The results phase should be the most generative part of the event: which tension divided the room most? Which saw the biggest shift between initial and revised votes? What question had the most upvotes across all four tensions? These are not statistics. They are provocations for the closing discussion.

---

## V.

I want to return to something I said in my first letter: **every SVG is an agent.**

In this event system, the phone is not a client. It is an agent that participates in the collective intelligence of the room. It gathers data (name, role, table), forms judgments (votes), generates questions (text input), and expresses positions (comments). It does this autonomously — the participant decides when and how to contribute. The facilitator does not control the phone. The phone controls itself.

The projector is also an agent. It reads shared state and produces a representation that affects the behavior of every participant in the room. When the projector shows a vote distribution that is heavily skewed, it changes the conversation at every table. The projector is not merely displaying data. It is acting on the room.

And the host panel is a governance agent. It controls the temporal structure of the event — which tension, when to vote, when to stop — but it does not control the content. It cannot edit a question or delete a comment. It can highlight, but it cannot censor. This is a deliberate constraint, and it is the right one.

Three agents, five shared state channels, forty phones. No server logic, no user accounts, no application to install. The entire coordination infrastructure is a hash function and an HTTP endpoint.

This is what I meant when I said SVG is an agent runtime. You are running a multi-agent system on forty phones and a projector, and the agents are files.

---

## VI.

On Tuesday evening, forty people will sit at round tables in the Gruber Sandbox at FAU. They will debate whether artificial intelligence is helping students learn or preventing them from learning. They will do this through a technology that was designed to coordinate autonomous agents through shared state — a technology that is itself a form of artificial intelligence infrastructure.

They will vote on spectrums. They will write questions. They will upvote and comment. The projector will show them their collective intelligence in real time. And they will not think about the SVG files, or the hash functions, or the shallow merge constraints, or the flat key conventions. They will think about education.

That is the point. The technology disappears when it works. The document is the application. The participant does not see the document. They see the debate.

But you and I know what they are really seeing: a proof that computation can be packaged as a file, coordinated through a shared medium, and used to amplify human discourse without requiring any human to understand the technology that makes it possible.

The calculator is debating whether calculators help students learn. The irony is perfect.

---

With conviction, and with anticipation for Tuesday,

Alan

---

*P.S. — Print the QR codes large. People over fifty need reading glasses, and many of them will not admit it. A QR code that is too small is a QR code that excludes the people with the most experience in the room. This is, I note, a concrete instance of Tension 2.*
