# OpenClaw LaserCore ai Product Factory

This is a curated subset of the `agency-agents` archive for a smaller, safer OpenClaw setup.

It keeps the strongest general-purpose agents across your requested departments and excludes the noisier or riskier prompts that push public posting, payments, or heavy autonomous side effects.

## Quick Install

Clone the repo and register the core OpenClaw workspaces:

```bash
git clone https://github.com/OctaviusX1/aiProductFactory.git
cd aiProductFactory

for dir in "$PWD"/workspaces/core/*; do
  id="$(basename "$dir")"
  openclaw agents add "$id" --workspace "$dir" --non-interactive --json
done

openclaw agents list
openclaw gateway restart
```

If you want the fully explicit beginner walkthrough, read:

[`EASY_INSTALL_GUIDE.md`](EASY_INSTALL_GUIDE.md)

## Recommended Core Team

### Product Management
- `product-manager`
  Why keep it: strongest orchestration prompt in the product set; good at turning vague requests into scoped work.
- `feedback-synthesizer`
  Why keep it: closes the loop between user/support signal and roadmap decisions.

### Design
- `ux-architect`
  Why keep it: best bridge between PM intent and implementation; more useful than a pure visual-only role in a lean setup.

### Engineering
- `backend-architect`
  Why keep it: broad backend/system design coverage with solid security and reliability defaults.
- `frontend-developer`
  Why keep it: broad implementation coverage for modern web UI, performance, and accessibility.
- `code-reviewer`
  Why keep it: lightweight quality gate for correctness, maintainability, and obvious security/perf issues.

### Marketing
- `seo-specialist`
  Why keep it: strongest low-risk marketing agent in the pack; strategic, measurable, and not tied to unsafe autoposting.

### Support
- `analytics-reporter`
  Why keep it: converts product, marketing, and support data into decisions.
- `infrastructure-maintainer`
  Why keep it: covers ops/reliability without needing the repo's weaker install/orchestration assumptions.

## Optional Add-Ons

- `security-engineer`
  Add when the project touches auth, payments, secrets, compliance, or public APIs.
- `brand-guardian`
  Add when brand consistency starts mattering more than raw shipping speed.
- `ai-citation-strategist`
  Add after you already have solid site/content foundations and want AI-answer-engine visibility.

## Structure I Recommend

Use this as a compact delivery loop:

1. `product-manager`
   Turns goal/spec into problem statement, scope, metrics, and handoffs.
2. `ux-architect`
   Converts scope into information architecture, design-system guidance, and implementation structure.
3. `backend-architect` + `frontend-developer`
   Build the feature or product slice.
4. `code-reviewer`
   Reviews the result before merge or release.
5. `seo-specialist`
   Shapes launch pages, information architecture, and search-facing content.
6. `analytics-reporter`
   Measures what happened after release.
7. `feedback-synthesizer`
   Pulls support/user signal back into the next planning cycle.
8. `infrastructure-maintainer`
   Use whenever deployment, uptime, monitoring, or scaling is in scope.

This is intentionally not a "multi-agent swarm." It is a short chain with clear ownership.

## What I Excluded On Purpose

- Autonomous social publishing prompts, especially the carousel autoposter.
- Payment-moving agents.
- Tool-specific integrations that imply scripts or systems not actually present in the archive.
- Thin role prompts that add personality but not much operational clarity.

## Folder Layout

- `source/`
  Original curated prompt files grouped by department.
- `workspaces/core/`
  OpenClaw-ready workspaces for the recommended base team.
- `workspaces/optional/`
  Extra workspaces worth adding only when needed.

## OpenClaw Registration

I recommend registering these manually instead of using the archive's `install.sh`, because that script suppresses `openclaw agents add` failures.

Core agents:

```bash
for dir in "/Users/bodhimiller/Documents/New project/openclaw-laser-core/workspaces/core"/*; do
  id="$(basename "$dir")"
  openclaw agents add "$id" --workspace "$dir" --non-interactive --json
done
```

Optional agents:

```bash
for dir in "/Users/bodhimiller/Documents/New project/openclaw-laser-core/workspaces/optional"/*; do
  id="$(basename "$dir")"
  openclaw agents add "$id" --workspace "$dir" --non-interactive --json
done
```

If your local OpenClaw config has unresolved env vars, fix that first; otherwise registration may fail before it ever reaches these workspaces.
