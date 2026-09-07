# business-interview

A Claude Code skill that interviews you about your business and writes the answers into your project's context files, so Claude stops asking you the same things every session.

Claude Code reads a project's `CLAUDE.md` and whatever context files you keep next to it. Most people never fill them in properly, because writing "here is my business" into a blank file is a chore and the result reads like a brochure. This skill turns it into a twenty-minute conversation instead: nine blocks of three or four questions, one block at a time, and it writes the files for you at the end.

## What it does

- **Asks block by block, not all at once.** Business, product, customer, channels, money, competition, goals, stack, and how you want Claude to work. It waits for each answer and follows up when one is vague.
- **Forks when there is no business yet.** If block 1 reveals an idea rather than a company, it swaps to a pre-launch track: what already happened, what exactly you would sell, what you want out of it, and the price arithmetic done backwards from your income target. Asking an idea-stage founder about gross margin produces an invented number, which is worse than no number.
- **Refuses to guess.** If you do not know a figure, it writes `unknown` into the file. Nothing gets filled in on your behalf.
- **Writes the files, after you say yes.** It shows you the executive summary, the three gaps where Claude can help most, and exactly what it is about to write and where. Nothing is written before an explicit confirmation.

## What it does not do

- It is not a strategy document. It records what you tell it. If the answers are thin, the files are thin, and every skill downstream inherits that.
- It does not research your market, look up competitors, or read your analytics. No MCPs, no APIs, pure conversation.
- It cannot tell whether you are wrong about your own business. It will push once on a vague answer, then take it.
- Money questions are optional, and it will not ask twice. Skipping them leaves Claude noticeably less useful on anything involving price.

## Install

Copy this folder into a project's skills directory:

```bash
git clone https://github.com/aguevara92/business-interview.git
mkdir -p your-project/.claude/skills/business-interview
cp business-interview/SKILL.md your-project/.claude/skills/business-interview/
```

Then, in that project, run `/business-interview`.

No dependencies. Nothing to configure.

## Where it writes

By default it fills `context/business.md`, `context/profile.md`, `context/projects.md`, `context/roadmap.md` and `context/finances.md`. If those files do not exist, it creates them; if they exist and are already filled, it asks which blocks changed and merges rather than overwriting. Anything else it touches (an onboarding checklist, a journal, a clients folder) it touches only when that thing is already in your project. It will not scaffold a filing system you did not ask for.

## Re-running it

Run it again whenever the business changes. It asks which blocks are stale and re-runs only those, merging into what is already written. It is not destructive on a second pass.

## License

MIT. See [LICENSE](LICENSE).
