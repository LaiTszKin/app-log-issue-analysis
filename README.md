# App Log Issue Analysis

A Codex skill for evidence-driven application log investigations.

This skill helps agents analyze logs end-to-end, correlate runtime signals with code paths, and produce actionable incident findings with confidence levels and remediation steps.

## What this skill provides

- A structured workflow for incident investigation from scoping to remediation.
- A strict evidence standard (log lines + code correlation + impact + confidence).
- A checklist to avoid false conclusions.
- A pattern catalog for common operational failures (timeouts, retry storms, auth errors, resource pressure, schema mismatch, race conditions, and dependency outages).

## Repository structure

- `SKILL.md`: Main skill definition, principles, and output format.
- `agents/openai.yaml`: Agent interface metadata and default prompt.
- `references/investigation-checklist.md`: Investigation validation checklist.
- `references/log-signal-patterns.md`: Log signal pattern reference.

## Installation

1. Clone this repository.
2. Copy this folder to your Codex skills directory:

```bash
mkdir -p "$CODEX_HOME/skills"
cp -R app-log-issue-analysis "$CODEX_HOME/skills/app-log-issue-analysis"
```

## Usage

Invoke the skill in your prompt:

```text
Use $app-log-issue-analysis to inspect these logs and identify root causes.
```

Best results come from including:

- Service/component name
- Environment (prod/staging/dev)
- Incident time window (with timezone)
- Correlation IDs (trace/request/job/user/tx)
- Relevant log excerpts and recent deploy/config context

## Output expectations

The skill is designed to return:

1. Incident summary (scope, timeframe, overall status)
2. Confirmed issues ordered by severity
3. Hypotheses (when evidence is incomplete) with required validation data
4. Monitoring and prevention improvements

## Development notes

This repository is intentionally lightweight and focused on reusable investigation guidance.
