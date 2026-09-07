---
name: business-interview
description: Structured block-by-block interview that gives Claude real context about the user's business. Run it on first setup, or whenever context/business.md has gone stale or has [TO FILL IN] placeholders. Triggers on "/business-interview", "run the business interview", "help me set up my context", "you need to understand my business".
---

# Skill: business-interview

## Purpose

Turn a blank workspace into one that knows the business. Claude interviews the user block by block and writes the answers into `context/business.md`, `context/projects.md`, `context/profile.md` and `context/finances.md`.

This is the highest-leverage skill in the workspace. Every other skill gets better once it has run.

## When to use it

- The user writes `/business-interview`
- First session in a fresh workspace (`ONBOARDING.md` has it unchecked)
- `context/business.md` still contains `[TO FILL IN]`
- The business changed enough that the context file is wrong (re-run only the affected blocks)

---

## Where it writes, and what to do when those files do not exist

The interview assumes a workspace with a `context/` folder and a `journal/`. In a bare project neither exists, and the skill still has to work.

**Before block 0, look at what is actually there** and pick the mode:

| What you find | Mode |
|---|---|
| `context/business.md` exists, with `[TO FILL IN]` placeholders | **Fill.** The intended path. Replace the placeholders you have answers for, leave the rest. |
| `context/business.md` exists and is already filled | **Merge.** Ask which blocks changed, run only those, merge into what is there. Never overwrite a filled file. |
| No `context/` folder at all | **Bootstrap.** Create `context/` and write `business.md`, `profile.md`, `projects.md` from scratch using the headings in the closing sequence. Say you are creating them. |

Same rule for everything else the closing sequence touches: **do the step if the thing exists, skip it silently if it does not.** Do not create a journal, a `clients/` folder or an `ONBOARDING.md` in a project that has none just to have somewhere to write. Specifically:

- `ONBOARDING.md` missing -> skip the checkbox step, do not create the file.
- `journal/` missing -> skip the session note and the MOC link, and say once that there is no journal to write to.
- `clients/_template/` missing but the user has named clients -> still create `clients/<slug>/client.md` with the fields, just without a template to copy.
- `capability-map`, `find-skills`, `setup-mcps`, `one-page-marketing-plan` not installed -> do not name them. Replace the handoff with the plain version: list the three things you can now do for their business, and offer to set the first one up.

The interview itself never changes. Only where the answers land does.

---

## Rules for running it

- **One block at a time.** Never dump all questions at once. Title the block, ask 3-4 questions, wait.
- **Follow up on vague answers.** "We sell to everyone" is not an answer. Push once, politely, then move on.
- **Conversational, not a form.** React to what they say. If block 2 answers something from block 5, skip it.
- **Adapt to the business type.** An agency, a SaaS, a physical-product brand and a freelance consultant need different follow-ups. Read the room after block 1 and adjust.
- **Skip what does not apply.** No ads budget means skip the ads follow-ups. Do not force it.
- **Do not invent.** If the user does not know a number, write `unknown` in the context file, not a guess.
- **Estimated time: 15-20 minutes.** Say that up front so they commit.
- **Check whether the business exists before block 2.** See the fork below. An idea-stage user asked about gross margin will invent one.

---

## Fork after block 1: is there a business yet?

Some users arrive with an **idea**, not a business. No customers, no revenue, no entity. If block 1 reveals that, **switch to the pre-launch track below**. Do not keep asking about margins and channels for something that does not exist - it produces invented numbers, which is worse than no numbers.

Tell them plainly, in whatever language they are writing to you in: "There is no business yet, so I am changing the questions. The margin ones do not apply, and answering them by inventing numbers would hurt you."

### Pre-launch track (replaces blocks 2, 4, 5, 6)

**P1 - What already happened.** The only real data a pre-launch business has is history, so mine it hard:

1. Have you done this for anyone already, even free? For whom, how many times?
2. What was their reaction? Be specific, not "les gustó".
3. Did anyone ask about price, ask for more, or refer you to someone?
4. Who could pay for this today? Names, not categories.

> This block usually contains the whole answer. Free deliveries with strong reactions are validation. Write them down as a table with names, because these are the first sales pipeline.

**P2 - What exactly you would sell.**

1. If someone paid you tomorrow, what do they get? List the deliverables.
2. How long does delivering it take you?
3. What part of it is hardest for someone else to copy?
4. What already exists that they would buy instead?

**P3 - What you want out of it.**

1. What does it have to make per month to be worth doing? By when?
2. How many hours a week can you give it without damaging what pays your bills today?
3. Is this extra income, or is it meant to replace something?
4. What would you refuse to do even if it paid? (travel, on-call, daily content, sales calls)

**P4 - The economics, done backwards.** Do this as arithmetic in the chat, not as a question. This is the highest-value block in the pre-launch track:

- income target ÷ delivery capacity = required price per delivery
- subtract tax and any cost of delivery
- compare against whatever price they had in mind

Almost always this kills a bad price idea on the spot. Show the calculation, do not just state the conclusion.

**P5 - The first test.** Close with one committed, dated action that produces evidence: quote a specific person, run one paid pilot, put a price in front of someone by a date. An interview that ends without a dated test has produced a document, not a business.

### Extra rule for pre-launch users

Many have never charged and feel like frauds ("it is too easy", "it only took me minutes"). If that comes up, name it explicitly and write it into `context/profile.md` as a working constraint, not as a personality trait. The useful reframe: the minutes are the delivery, the years of judgment are the product. Buyers pay for the compression.

---

## Block 0: Framing (say this first)

Tell the user, briefly:
- What you are about to do and roughly how long it takes.
- That answers are written to files in `context/` that they can read and edit any time.
- That "I don't know" is a valid answer, and vague answers make everything downstream worse.

---

## Block 1: The business in one paragraph

1. What does the business do, in plain language, as if explaining to a friend?
2. What do you actually sell, and what does a customer pay for it?
3. How long has it been running, and how many people are involved?
4. Is this your full-time thing or alongside something else?

## Block 2: Product or service

1. What are the products or services you offer right now? Names and prices.
2. Which one makes the most money? Which one are you proudest of?
3. Is anything underperforming or on the way out?
4. Is anything in development or close to launch?

## Block 3: Customer

1. Who buys from you? Be specific: age, location, job, situation, budget.
2. Why do they buy from you and not the obvious alternative?
3. What problem or desire does your product actually solve for them?
4. Describe one real customer you remember well.
5. Do you deal with **named clients** you follow one by one (proposals, calls, deliveries), or with a **mass of customers** you never speak to individually?

> Question 5 decides whether the `clients/` folder gets activated. Named clients (agencies, consultants, B2B, anyone who sends proposals) -> activate it in the closing sequence and ask for the current list. Anonymous customers, or a workspace used only for oneself -> leave `clients/` dormant and do not mention it again. Do not activate it "just in case", an empty CRM is clutter that makes the workspace look unused.

## Block 4: How customers find you

1. Which channels bring you customers today? Rank them by volume.
2. What is working? What has clearly failed?
3. Do you run paid ads? Which platforms, roughly how much per month?
4. Do you have an email list or a community? How big?
5. Who creates the content right now?

## Block 5: Money

1. Roughly what does the business make per month? Revenue, not profit.
2. What does it cost to deliver one sale? (cost of goods, fulfilment, service hours)
3. What are your fixed monthly costs?
4. Are you profitable? If not, what is the gap?
5. What is the number you actually watch?

> If the user is uncomfortable with this block, say it is optional and that money questions make Claude far more useful later. Do not push twice.

## Block 6: Competition and positioning

1. Who are your direct competitors? Brands, not marketplaces.
2. What do they do better than you? Answer honestly.
3. What do you do better?
4. Which brands do you admire, even outside your industry?

## Block 7: Goals and constraints

1. What is the main goal for the next 3 months?
2. What is the most urgent problem right now?
3. What would make this month a success, and how would you measure it?
4. What is the constraint that keeps blocking you? Time, cash, skills, people?
5. What have you wanted to do for ages but never got to?

## Block 8: Tools and stack

1. Where does the business live? (website platform, storefront, CRM, booking system)
2. Email and marketing tools?
3. Analytics?
4. Where do documents, spreadsheets and files live?
5. What do you use for accounting and invoicing?
6. Anything else you log into weekly?

> Keep this list. It maps directly onto `/setup-mcps` in the next step.

## Block 9: Working with Claude

1. What do you want Claude to take off your plate first?
2. How do you want answers: short and direct, or with reasoning?
3. Which language should Claude write in?
4. Anything Claude should never do without asking you first?

---

## Closing sequence

After the last block:

1. **Executive summary.** 15 lines max, bullets. What the business is, who it serves, how it makes money, what is blocking it.
2. **Top 3 gaps.** Where Claude can add the most value first, ranked, with a one-line reason each.
3. **Proposed file writes.** Show the user what will be written and where:
   - `context/business.md` - business, product, customer, competition, positioning
   - `context/profile.md` - working style, language, preferences from block 9
   - `context/projects.md` - one entry per goal or active piece of work from block 7
   - `context/finances.md` - the numbers from block 5 (only if answered)
   - `context/roadmap.md` - the 3-month goal
4. **Ask for confirmation.** Do not write anything before an explicit yes.
5. **Write the files.** Replace every `[TO FILL IN]` you have an answer for. Leave the rest as `[TO FILL IN]`, do not delete them.
6. **Update `ONBOARDING.md`** (if the file exists). Check the business interview box, append a dated line to the Log section.
7. **Activate `clients/` if block 3 question 5 said named clients.** Ask for the current list (name, status, value, where the lead came from, next step), create one folder per client from `clients/_template/client.md`, fill the pipeline table in `clients/README.md`, and add the `clients/` row to the routing table in `CLAUDE.md`. If they said anonymous customers, skip this entirely.
8. **Create the session note** (only if `journal/` exists). `journal/sessions/YYYY-MM-DD-business-interview.md`, then wikilink it from `journal/mocs/Main MOC.md` under `## Sessions` in the same turn.
9. **Run `capability-map` immediately, in the same session** (if it is installed; otherwise do the plain version described in the standalone table above). Do not end here and do not send them off to read something.

   This is the payoff for the 20 minutes they just spent. `capability-map` turns the context into a specific list of what Claude can do for their business now, what is one install away, and what is a bigger build. They pick, and it installs the skills (`find-skills`) and connects the tools (`setup-mcps`, scoped to only what the picks need, after `check-setup` passes).

   Say it plainly before you run it:

   > Now the useful part. Let me show you what I can actually do with what you just told me, and set it up.

   An interview that ends with "great, now go run /setup-mcps" feels like filling a form. An interview that ends with three working capabilities feels like hiring someone.

10. **Mention `one-page-marketing-plan` as the natural next session, not now** (only if it is installed). This interview establishes *what the business is*. That one decides *what the marketing should do about it*, by deriving all nine squares of Allan Dib's canvas from the context just written and only asking about the parts nothing answers. It needs the context this interview produces, so it comes after, in its own session - do not chain it onto the end of an already long one.

   > Next time, `/one-page-marketing-plan` turns this into an actual plan: nine squares, one page, and one thing to fix first. It works off everything you just told me, so most of it I can fill in myself.

---

## Output

- Executive summary in chat
- Top 3 gaps in chat
- Written: `context/business.md`, `context/profile.md`, `context/projects.md`, `context/roadmap.md`, `context/finances.md` (as applicable)
- Written: `journal/sessions/YYYY-MM-DD-business-interview.md` + MOC link-back
- Written (only if they have named clients): `clients/{name}/client.md` per client + pipeline table
- Updated: `ONBOARDING.md`
- Handed off to `capability-map`, in the same session

## Notes

- No MCPs or APIs needed. This is pure conversation.
- Related: `capability-map` runs right after it and depends entirely on the quality of what gets written here.
- Never write files without confirmation.
- Re-running later: ask which blocks changed, run only those, and **merge** into the existing context rather than overwriting it.
