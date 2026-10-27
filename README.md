# mermaid-write

An agent skill for writing Mermaid diagrams that stay readable in a pull request.

It gives an agent two things:

1. **Two rules** that keep a diagram legible — one line per node box, and notes short enough
   to survive a 1010 px column.
2. **601 example blocks over 32 diagram types** in `examples/`, so the agent copies a real
   shape instead of guessing the syntax.

## Install

Copy this folder into the skills directory of your agent.

```bash
# Claude Code
git clone https://github.com/iurev/mermaid-write ~/.claude/skills/mermaid-write

# pi (any directory listed in skillDirs)
git clone https://github.com/iurev/mermaid-write /path/in/skillDirs/mermaid-write
```

`SKILL.md` is plain Markdown with YAML frontmatter, so anything that reads the Agent Skills
format can use it.

## What is in here

| Path | What |
| --- | --- |
| `SKILL.md` | the two rules, the render advice, and the index of the examples |
| `examples/<type>.md` | one file per diagram type, 601 blocks together |

Read one file, not all. `examples/flowchart.md` is 37 KB; `examples/pie.md` is 0.4 KB.

## The rules, in one line each

- A node box holds one line. Several lines in one box become a wall of text — use a
  `classDiagram` field, or a `Note`, which may hold several lines.
- A long note widens the whole diagram. Past 1010 px the renderer scales it down until the
  text is unreadable, so keep notes short and put the full sentence in the prose.
- Never send diagram text to a hosted renderer (`kroki.io`, `mermaid.ink`, `mermaid.live`).
  Parse and render on your own machine.

## Where it comes from

`examples/` is copied from <https://pele.run/examples>, the example set of
[Pele](https://pele.run) — a Mermaid renderer by kepano, released under the MIT licence.
See [NOTICE.md](NOTICE.md).

The rules were written while drawing large sequence diagrams of a production checkout and
payment flow. Those diagrams are not part of this repository.

## Licence

MIT for this repository. The copied examples keep their own MIT notice — see
[NOTICE.md](NOTICE.md).
