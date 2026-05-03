# agora

A multi-agent system for stress-testing ideas through structured adversarial debate.

Two agents argue. A third judges. A fourth audits the judge. The output isn't a verdict — it's a clearer picture of where the disagreement actually lives.

---

## Why this exists

When you want to think hard about something, your options are bad. Online takes are one-sided and optimized for engagement. A single LLM gives you balanced-sounding mush that flattens real disagreement. Friends are scarce, biased, and reluctant to steelman positions they find distasteful.

`agora` is designed to produce what those options miss: the strongest case for each side, presented adversarially, then evaluated by something that is itself watched.

It is **not** a truth machine. It will not resolve contested empirical or moral questions, and any version that claims to is lying. Its value is in producing a clearer picture of *the disagreement itself* — usually the thing people most need and least have.

---

## How it works

Four agents with distinct roles, prompts, and (ideally) different model configurations to reduce shared blind spots.

**Debater A** and **Debater B** receive the question and are assigned positions. Each makes the strongest possible case for their side — no strawmanning, no premature concession. They proceed in rounds: opening, rebuttal, counter-rebuttal, closing. Each agent must engage directly with the other's previous arguments rather than restating its own.

**The Judge** receives the full transcript and produces a structured evaluation: which arguments landed, which were dropped, where the cruxes of disagreement actually live, and a tentative weighting of which side made the stronger case. The judge is explicitly instructed to identify points of genuine uncertainty rather than force a verdict.

**The Auditor** receives the question, the transcript, and the judge's evaluation, and looks for problems: did the judge favor the more articulate writer over the better argument? Did it penalize a side for being counterintuitive rather than wrong? Did it miss a strong point? Did it import assumptions not present in the debate?

You see all four outputs: transcript, judgment, audit, and a synthesis that surfaces the actual cruxes without resolving them.

---

## Modes

`agora` supports eight modes, each tuned for a different shape of problem.

### 1. General Debate

The default. Two agents argue opposing sides of a question you're curious about but not personally invested in. You're a spectator trying to understand a contested topic.

Use it when you want to learn the real shape of a disagreement before forming your own view. *Should cities ban cars? Is remote work actually more productive? Was Versailles the cause of WWII?*

### 2. Devil's Advocate (attack-my-position)

You submit your own view. The system attacks it. You sit and absorb the strongest objections without responding, then read the judge and auditor's take on whether the attack landed.

Use it before making a decision you're already leaning toward, or to pressure-test a belief you suspect you're holding for bad reasons. The discomfort is the point.

### 3. Defend-My-Position

The inverse. You submit your view *and* the strongest objections you're worried about. The system tries to defend your view against those objections. The judge evaluates whether the defense actually works or whether it's hand-waving.

Use it when you're about to argue your position publicly — a meeting, a piece of writing, a conversation with someone who'll push back — and you want to know in advance which objections you have real answers to and which ones will sink you.

### 4. Panel

Three to five agents, each holding a genuinely distinct position, on questions that don't reduce to two sides. The output is a map of the disagreement rather than a verdict.

Use it for political, ethical, or policy questions where two-sided framing is itself part of the problem. Most of them are.

### 5. Pre-Mortem

You describe a plan or decision you're about to make. The system assumes it failed twelve months later and argues for the most likely reasons why. Different from devil's advocate because it doesn't attack your reasoning — it accepts the plan and explores failure modes downstream.

Use it for plans, projects, launches, life changes. The reframe from "is this right?" to "assume this failed, why?" tends to surface different and often more useful objections.

### 6. Socratic

No debaters. A single agent interrogates you. It asks you to state your view, then asks follow-up questions designed to expose hidden assumptions, unclear definitions, and load-bearing beliefs you haven't examined. The judge and auditor watch for whether the agent is genuinely probing or just being annoying.

Use it when you can't articulate your view clearly enough to even submit it to the other modes. The output isn't a verdict but a sharper version of your own position.

### 7. Crux-Finding

You and another person (real or imagined) disagree. You submit both positions. The system runs a compressed debate whose only goal is to identify the actual crux — the specific sub-claim where you'd both have to agree before the top-level disagreement could resolve. Skips the verdict entirely.

Use it before a hard conversation with a partner, coworker, or family member, so you walk in knowing what the disagreement is *actually* about rather than arguing past each other for an hour.

### 8. Red Team

You submit a piece of writing, a pitch, an argument, a strategy doc, a product spec — anything you've made that's trying to be persuasive or correct. Multiple agents attack it from different angles: the skeptical investor, the hostile reviewer, the bored reader, the domain expert who spots the technical error.

Different from devil's advocate because it's not attacking a *position* — it's attacking an *artifact*. Use it before you ship something where the cost of being wrong in public is high.

---

## Roadmap

Planned for future releases:

- **Historical Mode** — run debates between specific historical thinkers (Hayek vs. Keynes, Hobbes vs. Rousseau, Mill vs. Stephen) arguing from their actual frameworks. Pedagogical rather than rigorous.
- **Calibration Mode** — record your prior belief before each debate and your posterior after. Over time, surface patterns in what actually changes your mind versus what doesn't. Turns the tool from a thinking aid into a mirror.
- **Persistent Cruxes** — store the cruxes from every debate you run. When a new question shares the underlying crux structure of an old one, surface it: *you debated something structurally identical three months ago and concluded X. Want to revisit?*

---

## Status

Early. Architecture is settled, modes 1–8 are the initial scope. Contributions, criticism, and pull requests welcome — especially for prompt engineering, where this lives or dies.

---

## License

MIT.
