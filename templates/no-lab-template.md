# Room: <Room Name>

**Platform:** TryHackMe / HackTheBox / Other
**Category:** Learn / Defensive / Theory / Tooling / etc.
**Difficulty:** Easy / Medium / Hard
**Estimated time:** `<xx min>`
**Tags:** `<telemetry, detection, forensics, networking, tooling, policy>`
**Objective(s):** One short sentence describing what the lab teaches (e.g., “Understand telemetry sources and write a basic detection rule for suspicious PowerShell usage”).

---

## TL;DR

One-sentence summary of what you learned and why it matters.
*eg:* “Intro to defensive security: enable process and command-line logging + write a Sigma rule to detect encoded PowerShell.”

---

## 1) Context / Why this lab exists

* Problem space / threat scenario the lab addresses (1–3 lines).
* Real-world relevance (who cares and when to use these skills).
* Prerequisites (what you should already know).

---

## 2) Learning objectives (explicit)

List the measurable learning outcomes (use bullets). Example:

* Identify three telemetry sources that detect lateral movement.
* Explain the difference between prevention and detection.
* Write or interpret a basic detection rule (Sigma/YARA/Suricata).
* Map an adversary TTP to a log source.

---

## 3) Quick checklist (what to do in this room)

1. Read module X — key concept Y.
2. Complete quiz / answer questions.
3. Try the mini-exercise (local or simulated).
4. Write one detection/hunting rule or mitigation.

---

## 4) Module-by-module walkthrough (concise)

For each module/section in the room, give:

* **Module N — Title**
  *What it covers (1–2 lines).*
  *Key points / takeaways (bullets).*
  *Answers to any explicit questions or quiz items (if present) — show question then your concise answer + 1-line justification.*

(Repeat for each module.)

---

## 5) Key concepts & definitions (cheat-sheet)

Short, bullet definitions you can copy into notes:

* **Telemetry** — What to collect (processes, network, DNS, auth events, application logs).
* **Detection vs Prevention** — Detection = observe & alert / Prevention = block or harden.
* **IOC / TTP** — Indicators of Compromise / Tactics, Techniques & Procedures.
* **Sigma / Suricata / YARA** — Portable detection rule formats and use-cases.

---

## 6) Practical exercises (do locally / simulate)

Give 2–4 hands-on exercises the reader can run on their own machine or in a safe lab. For each, include:

* **Goal:** clear one-line goal.
* **Steps / commands:** minimal reproducible commands or pseudo-steps.
* **Expected result / how to verify:** what output or log to look for.

**Example exercise:**
*Goal:* Generate a Sysmon process-create event with command-line.
*Steps:* Install Sysmon with a basic config; run `powershell -NoProfile -Command "Write-Host test"`
*Verify:* Check Sysmon Event ID 1 and confirm the command-line field contains the executed command.

---

## 7) Example detection / rule (template)

Provide a short, copyable example relevant to the lab (Sigma, YARA, Suricata snippet, or a simple Splunk query).

* **Purpose:** one line.
* **Rule / Query:** code block.
* **Notes on tuning / false positives:** 1–2 bullets.

**Example (Sigma-like pseudorule):**

```yaml
title: Suspicious PowerShell EncodedCommand
description: Detect PowerShell using -EncodedCommand which is often used for obfuscation
detection:
  selection:
    CommandLine|contains: -EncodedCommand
  condition: selection
falsepositives:
  - Legitimate admin scripts that intentionally use encoded payloads
level: medium
```

---

## 8) Common pitfalls & misconceptions

Bulleted list of things learners often get wrong, and short corrections/tips.

* "More logs = better" — not if they’re not collected, parsed, or used.
* Over-reliance on a single telemetry source (e.g., network-only) — use multiple.
* Excessive alerting without tuning leads to ignored alerts.

---

## 9) Notes / answers to lab questions (detailed)

If the room contains specific questions, list each with:

* **Q:** …
* **A:** … (explain reasoning briefly; reference module where the answer came from)

---

## 10) Further reading & resources

Curate 4–8 high-quality follow-ups (docs, blog posts, books, GitHub repos, tool docs). Include why each is useful (1 line).

---

## 11) Personal reflections / action plan

* What I understood well.
* What I need to practice next (concrete — e.g., “write 5 Sigma rules and test them against logs”).
* How I’ll apply this at work / projects.

