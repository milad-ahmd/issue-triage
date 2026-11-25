> [!NOTE]
> **This skill lives in the main collection: [milad-ahmd/agent-skills](https://github.com/milad-ahmd/agent-skills/tree/main/skills/issue-triage)**. Please ⭐ star it there; that's where updates land first.
> Docs: **https://milad-ahmd.github.io/agent-skills/skills/issue-triage/** · Claude Code: `/plugin install all-skills --marketplace milad-ahmd/agent-skills`

<div align="center">

# 🏷️ issue-triage

**Triages open GitHub issues: duplicates, missing repro info, stale threads, labels and priority, writes on approval. An Agent Skill for Claude Code, Cline, Cursor, Codex and other AI coding agents.**

[![License: MIT](https://img.shields.io/github/license/milad-ahmd/issue-triage)](LICENSE)
[![Stars](https://img.shields.io/github/stars/milad-ahmd/issue-triage?style=social)](https://github.com/milad-ahmd/issue-triage)
![Category](https://img.shields.io/badge/category-Git%20%26%20Workflow-blue)
![Works with](https://img.shields.io/badge/works%20with-Claude%20Code%20%7C%20Cline%20%7C%20Cursor%20%7C%20Codex-8A2BE2)

[Install](#-install) · [Usage](#-usage) · [How it works](skills/issue-triage/SKILL.md) · [All skills](https://github.com/milad-ahmd/agent-skills)

</div>

> Part of **[agent-skills](https://github.com/milad-ahmd/agent-skills)**, a growing collection of practical skills for AI coding agents.

## 📦 Install

**One command (installs the whole collection):**

```bash
curl -fsSL https://raw.githubusercontent.com/milad-ahmd/agent-skills/main/install.sh | bash -s -- issue-triage
```

**Manually (Claude Code):**

```bash
git clone https://github.com/milad-ahmd/issue-triage /tmp/issue-triage
mkdir -p ~/.claude/skills && cp -r /tmp/issue-triage/skills/issue-triage ~/.claude/skills/
```

**Per project:** copy `skills/issue-triage` into `<project>/.claude/skills/`.
**Any other agent:** paste [`SKILL.md`](skills/issue-triage/SKILL.md) into your rules or system prompt.

## 💬 Usage

Just ask your agent:

```text
Triage the open issues on our repo
Which bug reports are missing a version or steps to reproduce?
```

The full workflow, rules and output format are in [`SKILL.md`](skills/issue-triage/SKILL.md).

## 🔎 Sample output

`triage.py` is plain Python 3 with no dependencies and never writes to GitHub. Real output on the 15 made-up issues that ship with it (`gh issue list --json …` saved to a file, or `--repo owner/name` to fetch them):

```text
$ python3 triage.py issues.json --top 5

Triage of 15 open issues from fixtures/issues.json, as of 2026-11-25 (stale after 30 days, duplicate threshold 0.35)
Read-only report: nothing was changed on GitHub. Labels and duplicates are suggestions.

Needs attention first
   1. #101   P1  Crash on startup when the config path contains unicode ch...  severe: crash, crashes; 12 reactions; 2 other commenters; 2 duplicate candidates; no maintainer reply yet
   2. #108   P1  App crashes on startup if config directory has a unicode ...  severe: crashes; 3 reactions; 1 duplicate candidate; no maintainer reply yet
   3. #107   P1  Login token is printed in debug logs                          severe: token is printed; 4 reactions; no maintainer reply yet
   4. #110   P1  Data loss: sync deletes local files when the remote folde...  severe: data loss, deletes local, regression; 6 reactions; 1 other commenter; reporter replied last
   5. #102   P2  Add support for YAML config files                             20 reactions; 1 other commenter; 1 duplicate candidate; reporter replied last

Duplicate candidates (TF-IDF cosine >= 0.35; confirm by reading both)
  #117 may duplicate #102  score 0.61  shared: yaml, support, add, file, config, toml
  #119 may duplicate #101  score 0.46  shared: path, unicode, character, config, unicodedecodeerror, charmap
  #108 may duplicate #101  score 0.43  shared: crash, startup, unicode, config, character, path

Bug reports missing repro details
  #103   missing: version, steps, expected/actual, error/logs    It doesn't work
  #106   missing: version, steps, expected/actual, error/logs    Export to CSV drops rows with empty fields
  #108   missing: version, steps, expected/actual                App crashes on startup if config directory has ...
  #113   missing: version, expected/actual, error/logs           Upload fails for files over 2 GB

Stale (no activity for 30+ days)
  #109    127 days  never answered
  #106     75 days  waiting on reporter (last reply @maint-amy)
…
```

The agent reads the flagged issues, drafts replies, and shows the `gh issue edit/comment/close` commands for your approval before anything changes on GitHub.

## 🧩 More skills

See the full collection: **[milad-ahmd/agent-skills](https://github.com/milad-ahmd/agent-skills)**.

## 🤝 Contributing

This repo is a read-only mirror. Please open issues and PRs in **[milad-ahmd/agent-skills](https://github.com/milad-ahmd/agent-skills)**.

## 📄 License

[MIT](LICENSE) © Milad Ahmadi

<div align="center">

**If this skill saved you time, a ⭐ helps others find it.**

</div>
