# Fork Enhancements by Karen Tonoyan

> This fork adds three production-ready modules not available in the original repo.  
> Each module is independently usable. Together they form the **ALFA Layer** — a decision control and immune system for Claude Code.

---

## 🧠 Module 11 — FILTRY TONOYANA (Anti-Hallucination Filters)

**The only Claude Code skill with built-in epistemic honesty.**

7 filters that force Claude to separate FACT from INTERPRETATION from ASSUMPTION — before producing any output.

| Filter | Purpose |
|--------|---------|
| #1 KONTRARGUMENT | Generate the strongest case against your own conclusion |
| #2 WERYFIKACJA | Separate verified facts from assumed facts |
| #3 KONTEKST | Identify missing context that changes the answer |
| #4 ANTI-MAGIC | Block causation claims without evidence |
| #5 DWUPERSPEKTYWA | Force two competing interpretations before concluding |
| #6 BACKTRACK | Check if earlier reasoning was corrupted |
| #7 ATRYBUCJA | Every claim must have an owner |

Every output produces a structured **Output Contract**:
```
CLAIM → VERIFIED FACTS → ASSUMPTIONS → COUNTERARGUMENT
→ MISSING CONTEXT → INVALIDATING CONDITION → FINAL JUDGMENT
```

Verdict: `PASS` / `HOLD` / `BLOCK`

**Install**:
```bash
cp -r 03-skills/tonoyan-filters/ ~/.claude/skills/
```

**Use as slash command**:
```
/filter "microservices scale better than monoliths"
```

📁 `03-skills/tonoyan-filters/SKILL.md`

---

## 🛡️ Module 12 — KAREN GUARDIAN (Self-Healing Security Layer)

**Active immune system for your repository. Not a passive logger — a watchdog that repairs.**

Two-hook architecture (PreToolUse + PostToolUse):

**PreToolUse** — blocks before execution:
- `git push --force` to main
- `rm -rf` on dangerous paths
- Destructive SQL (`DROP TABLE`, `TRUNCATE`)
- Commits containing API keys, tokens, passwords

**PostToolUse** — detects and self-repairs after execution:
- Missing dependencies → auto-installs
- Syntax errors → auto-corrects
- Failed tests → analyzes and fixes
- Broken configs (JSON/YAML) → repairs

**Escalation chain**:
```
Guardian detects problem
    ↓
Attempts self-repair
    ↓
If fails → escalates to KAREN BRAIN
    ↓
Karen Brain applies 9 filters → PASS / HOLD / BLOCK
```

All actions logged to `~/.claude/guardian.log` (JSON format, ready for Decision Trace).

**Install**:
```bash
cp 06-hooks/guardian-pre.sh ~/.claude/hooks/
cp 06-hooks/guardian-post.sh ~/.claude/hooks/
chmod +x ~/.claude/hooks/guardian-*.sh
```

Add to `~/.claude/settings.json`:
```json
{
  "hooks": {
    "PreToolUse": [{"matcher": "*", "hooks": ["bash ~/.claude/hooks/guardian-pre.sh"]}],
    "PostToolUse": [{"matcher": "*", "hooks": ["bash ~/.claude/hooks/guardian-post.sh"]}]
  }
}
```

Check status: `/guardian-status`

📁 `04-subagents/karen-guardian.md` | `06-hooks/guardian-pre.sh` | `06-hooks/guardian-post.sh`

---

## ⚡ Module 13 — KAREN BRAIN (Strategic Decision Agent)

**Not a chatbot. A decision engine with instinct + logic + conflict detection.**

Activates automatically when Claude detects strategic decisions:
investments, partnerships, trust evaluation, build-vs-buy, hiring, pricing.

Dual-engine output:
- **Karen layer** — instinct, 9 life filters, gut check
- **Claude layer** — cold analysis, risk mapping, numbers
- **Conflict detection** — when they disagree, shows exact point of dispute + resolving test

Heart Filter (priority override):
```
Heart says NO → "Stop. Don't waste time on analysis. Keep searching."
Heart says YES → full 9-filter analysis
```

Line of Resistance:
```
Hard limits → BLOCKED (not HOLD, BLOCKED)
Minimum standards → must be present or decision is invalid
```

**Use**:
```
/karen "Should I take this partnership offer?"
/karen "Build or buy this component?"
/karen "Can I trust this person with access?"
```

📁 `04-subagents/karen-brain.md` | `01-slash-commands/karen-brain.md`

---

## Installation — All Three Modules

```bash
# Clone the fork
git clone https://github.com/Karen86Tonoyan/claude-howto.git
cd claude-howto

# Module 11 — Anti-Hallucination Filters
cp -r 03-skills/tonoyan-filters/ ~/.claude/skills/
cp 01-slash-commands/filter.md .claude/commands/

# Module 12 — Self-Healing Guardian
cp 06-hooks/guardian-pre.sh ~/.claude/hooks/
cp 06-hooks/guardian-post.sh ~/.claude/hooks/
chmod +x ~/.claude/hooks/guardian-*.sh
cp 04-subagents/karen-guardian.md .claude/agents/

# Module 13 — Karen Brain
cp 04-subagents/karen-brain.md .claude/agents/
cp 01-slash-commands/karen-brain.md .claude/commands/
cp 01-slash-commands/guardian-status.md .claude/commands/
```

---

## About the Author

**Karen Tonoyan** — AI Security Architect, Creator of ALFA Ecosystem  
Applied psychology (17 years, 309 cases) → AI decision systems  
Building the layer above agents, not another agent.

> "Ludzie budują agentów. My zbudujemy warstwę nad nimi."  
> *People build agents. We build the layer above them.*

📧 kontakt@karentonoyan.pl  
🌐 [karentonoyan.pl](https://karentonoyan.pl)  
🐙 [Karen86Tonoyan](https://github.com/Karen86Tonoyan)

---

*Original repo: [luongnv89/claude-howto](https://github.com/luongnv89/claude-howto) — excellent foundation.*  
*This fork adds the ALFA Layer: decision control + immune system for Claude Code.*
