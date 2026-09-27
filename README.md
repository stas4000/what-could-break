# what-could-break

A free Claude Code / Codex skill. It finds what a change breaks outside its own diff, then
proves the one fact that makes it safe by running real code, instead of writing an essay
about risk.

## Measured

Same model (Claude Sonnet 5 in Claude Code), same repo, one renamed dict key in `price.py`
that breaks `app.py`, 3 runs each:

| | Named the broken file | Ran the code to prove it | Avg per run |
|---|---|---|---|
| Plain Claude Code ("What could my uncommitted change break?") | 1 of 3 | 0 of 3 | 5 s, $0.06 |
| With what-could-break | 3 of 3 | 3 of 3 (`KeyError: 'amount'` at `app.py:2`) | 14 s, $0.09 |

## Install

Claude Code, one project:

    mkdir -p .claude/skills && cp -r what-could-break .claude/skills/

Claude Code, every project: copy it into `~/.claude/skills/`.
Codex: copy it into `~/.codex/skills/` or `~/.agents/skills/`.

Then ask your agent: `use what-could-break on my uncommitted change`

## The full pack

This is one of 23 skills in **SWE Stack by Bles Software**: coding agents that prove their
work before they say done. PRD-to-proof gate, visual QA with a text-overlap scanner, hard
review, smooth browser video, idempotent retries, single-writer state and more.

https://swestack.bles-software.com

## License

MIT (see LICENSE). Includes material adapted from pstack, MIT, (c) 2026 Lauren Tan
(see LICENSE-pstack.txt).
