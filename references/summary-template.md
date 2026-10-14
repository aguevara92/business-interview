# SUMMARY.md - template and rules

`SUMMARY.md` lives at the root of the workspace, next to `ONBOARDING.md`. It is the first thing the user reads after the interview and the document the facilitator opens in the meeting. It is written **once** at the end of the interview and **rewritten** (not appended) if the interview is re-run.

## Rules

1. **Their words.** Reuse the nouns they used. If they said "the Thursday report", write "the Thursday report", not "recurring reporting".
2. **Nothing invented.** Every line traces back to an answer. No numbers they did not give. `unknown` is written as `unknown`.
3. **Every "did not know" item carries its evidence.** Write the inference and, in the same line, the answers it comes from ("you said X in block 2 and Y in block 5"). If the evidence is thin, the item does not go in.
4. **Ranked, not listed.** Problems, strengths and projects are ordered by what costs or yields the most, bottleneck first.
5. **No padding, no praise.** If a section has two real items, it has two items. An empty section says "Nothing here yet" in one line.
6. **Length: one screen per section at most.** The whole file reads in under ten minutes.
7. **Language: the one the user writes in.**
8. **Reflect the interview, not the catalogue.** No capability, skill or MCP appears here that is not tied to a project in section 8.

## Sections, in this order

```markdown
# What I learned about [name / business]

> Written by Claude on YYYY-MM-DD from the interview. Read it, correct anything wrong, and tell me. Everything below also lives in `context/`, which is what I actually work from.

## 1. Who you are and what you do
Three to five lines. Open with the person from block 0: name and where they are. Then the business (or the work), what is sold or produced, to whom, since when, alone or with whom, full-time or not.

## 2. What you told me
The facts, compressed, block by block. Short bullets under one bold label per block. This is the record; the sections after it are the reading.

## 3. Your problems, ranked
Numbered. Each one: the problem in one line, what it costs (time, money, attention) in their numbers or `unknown`, and where it came up. The one they named as the blocker goes first, even if something else looks bigger to you.

## 4. What works
What is going well and the assets they have: data they already collect, a habit that holds, a tool they actually use, a relationship, a product that sells itself. Bullets. This is where the roadmap will build from.

## 5. What does not work
Manual loops, things done by hand every week, decisions postponed, tools paid for and unused, dependencies on one person. Bullets, each with the evidence.

## 6. What you knew, and what you did not
Two lists.

**You already knew this** - the things they named as problems or goals themselves. Short, it is their list.

**You did not say this, and it is in your answers** - the inferences: patterns across blocks, a cost they never added up, a bottleneck they described as normal, a strength they undersold. Each item: the inference, then `(from: block N, block M)`. Minimum three if the evidence supports it; if it does not, say plainly there were fewer. This section is the reason the interview was worth the time. Do not weaken it with hedges.

## 7. Your roadmap: the next three months
One theme for the quarter, in one line. Then one block per month: the objective, the measurable result, and what has to be true for it to happen. Derived from block 7 (goals), bounded by the constraint they named (time, cash, skills, people). If they gave no goal, say so and propose one, marked as a proposal.

## 8. Your projects
A table. One row per piece of work that came out of the interview: the goals from block 7, whatever is in development from block 2, and every problem from section 3 that has a concrete deliverable.

| # | Project | Goal (what done looks like) | First step | Needs | When |
|---|---|---|---|---|---|

- **Needs**: the tool it depends on, and the connection that gives Claude access to it. Take the tool from block 8 and the connection from `.claude/skills/setup-mcps/references/mcp-catalog.md`. Write "nothing" when plain Claude with the context is enough. Never name a connector the catalogue does not have; write "no connector, manual" instead.
- **When**: `now` (nothing to set up), `after connecting [tool]`, or `later` (a bigger build).

The "Needs" column is what `capability-map` and `setup-mcps` read. It is the list of what to install, in order of the projects it serves.

## 9. What happens next
Normal mode: "Next I show you what I can do for each of these, and set it up. That is `capability-map`, it runs now."
Facilitated mode: "This is where I stop. Nothing else happens until your meeting with [facilitator]. When you are in it, type: [resume phrase]. Then we check your machine together, pick from this list, and connect what the first project needs, with you doing the clicks."
```
