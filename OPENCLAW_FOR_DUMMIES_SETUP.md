# Step by Step Install Guide

This guide shows exactly how to install the core ai Product Factory agents from this repo into OpenClaw.

Repo:

[https://github.com/OctaviusX1/aiProductFactory](https://github.com/OctaviusX1/aiProductFactory)

## What This Installs

This installs the recommended core agents from `workspaces/core/`:

- `product-manager`
- `feedback-synthesizer`
- `ux-architect`
- `backend-architect`
- `frontend-developer`
- `code-reviewer`
- `seo-specialist`
- `analytics-reporter`
- `infrastructure-maintainer`

Important:

- install from `workspaces/core/`
- do not install from `source/`

`source/` contains the original prompt files.

`workspaces/core/` contains the actual OpenClaw-ready agent workspaces.

## Before You Start

Open Terminal and check that both Git and OpenClaw work:

```bash
git --version
openclaw --version
```

If either command fails, fix that first before continuing.

## Step 1: Clone The Repo

Run:

```bash
git clone https://github.com/OctaviusX1/aiProductFactory.git
cd aiProductFactory
```

If you already cloned it before:

```bash
cd aiProductFactory
git pull
```

## Step 2: Confirm The Core Folder Exists

Run:

```bash
ls workspaces/core
```

You should see agent folders such as:

- `product-manager`
- `frontend-developer`
- `backend-architect`

If you do not see them, you are in the wrong folder or the repo did not clone correctly.

## Step 3: Register The Core Agents

Run this exact command:

```bash
for dir in "$PWD"/workspaces/core/*; do
  id="$(basename "$dir")"
  openclaw agents add "$id" --workspace "$dir" --non-interactive --json
done
```

This loops through each packaged workspace and adds it to OpenClaw using the folder name as the agent ID.

## Step 4: Verify The Agents Were Added

Run:

```bash
openclaw agents list
```

You should see these IDs:

- `product-manager`
- `feedback-synthesizer`
- `ux-architect`
- `backend-architect`
- `frontend-developer`
- `code-reviewer`
- `seo-specialist`
- `analytics-reporter`
- `infrastructure-maintainer`

## Step 5: Restart The Gateway

If your OpenClaw gateway is already running, restart it:

```bash
openclaw gateway restart
```

This helps OpenClaw pick up the new agents immediately.

## Step 6: Test One Agent

Once setup is complete, test with a simple prompt inside OpenClaw.

Example:

```text
Use the product-manager agent to turn my startup idea into a short product brief.
```

Or:

```text
Use the frontend-developer agent to outline the UI for a SaaS dashboard.
```

If the agent responds correctly, setup worked.

## Optional: Install The Extra Agents Later

If you want the optional add-ons too, run:

```bash
for dir in "$PWD"/workspaces/optional/*; do
  id="$(basename "$dir")"
  openclaw agents add "$id" --workspace "$dir" --non-interactive --json
done
```

Optional agents:

- `security-engineer`
- `brand-guardian`
- `ai-citation-strategist`

## The Fastest Possible Install

If you just want the short version:

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

## Troubleshooting

### `openclaw: command not found`

OpenClaw is not installed or is not on your PATH.

Fix that first, then run:

```bash
openclaw --version
```

### `git: command not found`

Git is not installed.

Install Git first, then run:

```bash
git --version
```

### The agents do not show up

Check these in order:

1. Make sure you are inside the cloned repo.
2. Run `ls workspaces/core`
3. Re-run the install loop.
4. Run `openclaw agents list`
5. Run `openclaw gateway restart`

### You accidentally installed from `source/`

Delete the broken agent entries and install again from `workspaces/core/`.

## Best Practice

For beginners, install only `workspaces/core/` first.

Do not add the optional agents until you know you need them.

That keeps the setup lean and avoids clutter.
