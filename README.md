# Meeting Prep - Claude Code Plugin

Prepare for any meeting by analyzing documents, emails, and context. Claude generates a structured preparation document with talking points, conversation strategy, and pitfalls to avoid.

## Install

```bash
claude plugin add github:annetklo/meeting-prep
```

## Usage

Interactive (Claude will ask what it needs):
```
/meeting-prep
```

With arguments:
```
/meeting-prep --person "Jane Smith, CTO, Acme Corp" --context "Partnership discussion" --documents briefing.pdf feedback.pdf
```

## What it does

You give Claude your meeting documents (briefings, proposals, feedback, emails) and tell it who you're meeting. Claude analyzes everything and produces a structured prep document:

1. **Summary** of the other party's core message and tone
2. **Position analysis** for each major point: what they say, why it matters, and your suggested response
3. **Practical items** extracted from correspondence (scheduling, action items, logistics)
4. **Recommended approach** with 5 concrete conversation steps
5. **Pitfalls to avoid** based on the actual content

Output is a .docx (if python-docx is installed) or .md file.

## Options

| Flag | Description | Default |
|------|-------------|---------|
| `--person` | Name, role, organization | Asked interactively |
| `--context` | Meeting topic/context | Asked interactively |
| `--documents` | Files to analyze | Asked interactively |
| `--email` | Email text or file path | Optional |
| `--output-dir` | Where to save | Current directory |
| `--lang` | `en` or `nl` | `en` |

## Language support

Default output is English. Use `--lang nl` for Dutch section headers and content.

## Requirements

- Claude Code CLI
- Optional: `python-docx` for .docx output (`pip install python-docx`)

## License

MIT
