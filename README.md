# Meeting Prep: Claude Plugin

Prepare for any meeting by analyzing documents, emails, and context. Claude generates a structured preparation document with talking points, conversation strategy, and pitfalls to avoid.

Built by [Mission Relearn](https://missionrelearn.com), an AI-literacy consultancy in the Netherlands.

## Install

### Option A: Claude Code (CLI)

Requires [Claude Code](https://docs.anthropic.com/en/docs/claude-code), the terminal tool.

**Step 1:** Open a terminal and start Claude Code:
```bash
claude
```

**Step 2:** Add this repository as a plugin marketplace:
```
/plugin marketplace add annetklo/meeting-prep
```

**Step 3:** Install the plugin:
```
/plugin install meeting-prep@meeting-prep
```

**Step 4:** Enable the plugin:
```
/plugin enable meeting-prep
```

Done. The `/meeting-prep` skill is now available in all your Claude Code sessions.

### Option B: Claude.ai (browser, no install)

You can use this skill directly in claude.ai without installing anything.

**Step 1:** Go to [claude.ai](https://claude.ai) and create a new Project (sidebar > Projects > New Project).

**Step 2:** Open the project, click "Set project instructions", and paste the contents of [`skills/meeting-prep/SKILL.md`](skills/meeting-prep/SKILL.md) into the instructions field.

**Step 3:** Start a conversation in the project. Upload your meeting documents (PDFs, emails, notes) and say:

```
Prepare me for a meeting with Jane Smith, CTO at Acme Corp.
The topic is a partnership discussion about platform integration.
```

Claude follows the same structured workflow and produces a meeting prep document.

## Usage

Interactive (Claude asks what it needs):
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

## Example output

```
## A. Summary

Smith's core message: Acme wants to integrate but needs clarity on data
ownership and timeline. Tone is constructive, with underlying concern
about vendor lock-in.

## B. Position Analysis

### 1. Data ownership
- **What they say**: "We need full export capability at any point."
- **Why it matters**: This signals past bad experiences with vendor lock-in.
- **Your position**: Confirm you support full data portability. Ask what
  export formats they need.

### 2. Timeline pressure
- **What they say**: "Q3 launch is non-negotiable."
- **Why it matters**: Leaves 10 weeks for integration work.
- **Your position**: Propose a phased rollout: core API by week 6, full
  feature set by week 10.
```

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

**Option A (CLI):**
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- Optional: `python-docx` for .docx output (`pip install python-docx`)

**Option B (browser):**
- A [claude.ai](https://claude.ai) account (free or paid)

## Troubleshooting

**"command not found" when running `claude`:** Install Claude Code first: `npm install -g @anthropic-ai/claude-code`

**Plugin install fails:** Make sure you completed step 2 first (`/plugin marketplace add annetklo/meeting-prep`). The marketplace must be added before you can install.

**Using claude.ai in the browser?** Skip the CLI steps entirely, use Option B above.

## License

MIT
