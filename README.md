# The Workflow

A six-phase design-and-build process with an optional AI lane you can enter or
leave at any step. Model-independent. Mac, VS Code, no local model required.

**The one rule**

> The AI workflow and the existing workflow produce the same artifact. Use AI,
> skip it, or use it for one step — the output is the same, and it goes in the
> same place.

## Who it's for

Someone who knows Figma deeply and nothing else technical. If a step needs the
terminal, the guide should hide it or spell it out.

## Getting started

This is just a folder of Markdown. Nothing in the process depends on Git or on
any particular host — Git is only how the folder is shared. It works on GitHub,
GitLab, a company internal remote, a shared drive, or a plain local folder with
no remote at all.

Pull it down to the chosen home:

```bash
git clone <your-remote-url> ~/workflow
```

The current public home is GitHub, if that is the one you are using:

```bash
git clone git@github.com:MattybotStew/workflow.git ~/workflow
```

That uses SSH, so your account needs a registered key; for HTTPS, use
`https://github.com/MattybotStew/workflow.git`. To move to a different host
later, point the remote at it:

```bash
git remote set-url origin <new-remote-url>
```

No remote? Skip the clone. Copy the folder to `~/workflow/`, and run `git init`
inside it only if you want version history.

Create the workspace once, alongside the repo:

```bash
mkdir -p ~/studio/_shared ~/studio/projects
```

Then copy `templates/agent.md` into each new project folder under
`~/studio/projects/`.

## Roles

| Role | Owns | Produces |
|---|---|---|
| **Design** | The project folder, the agent file, the research | The knowledge base that grows with the project |
| **PM** | Client-facing decisions, scope, timeline | The written recap the client sees |

Design feeds PM. PM writes the recap. Neither does the other's job.

## The six phases

1. **Workspace** — create `~/studio/`, point the AI at it. Once.
2. **Project Setup** — project folder, copy the agent template, drop docs in
   `assets/`, fill in `agent.md`.
3. **Kickoff** — Design builds the knowledge base; PM writes the client recap
   within 48 hours and confirms engagement type in writing.
4. **Structure** — agree sitemap and wireframes. Template-owned: import starter,
   then map. Bespoke: wireframes as code, presented in Figma.
5. **Production** — design and build. Template-owned: starter decides the look,
   design catches up to content. Bespoke: tokens locked early, content changes
   are edits.
6. **Handoff** — deliver, document, archive.

Each phase has a When, a Do, an Output, a Check, and an Optional AI lane. Full
detail in [`guide/process.md`](guide/process.md).

## Folders

**Workspace (once):**

```
~/studio/
├── _shared/      # agents + knowledge shared across projects
└── projects/     # one folder per client
```

**Per project:**

```
~/studio/projects/client-name/
├── agent.md      # the orientation file — AI reads this first
├── assets/       # client docs, unsorted
├── code/         # the actual repo
└── research/     # knowledge base (built during kickoff)
```

There are no four buckets. Client docs go in `assets/` as-is; the agent reads
them directly.

## This repo

```
workflow/
├── README.md
├── guide/
│   └── process.md
├── prompts/
│   ├── 01-agent-file.md
│   ├── 02-knowledge-base.md
│   ├── 03-pm-brief.md
│   ├── 04-update-agent.md
│   └── 05-check-agent.md
├── templates/
│   └── agent.md
└── examples/
    └── agent-example.md
```

Clone it anywhere; `~/workflow/` is the chosen home. Copy
`templates/agent.md` into each new project folder.

## The AI lane (VS Code, Mac)

Tool: **OpenCode** running inside VS Code, not the terminal TUI.
Model: DeepSeek, or whatever your company provides. The repo is
model-independent — swap the model, keep the prompts.

Setup order:

1. Install the CLI: `brew install anomalyco/tap/opencode`
2. Run `opencode`, which installs the VS Code extension.
3. Connect the model via `/connect`.
4. Add the Figma MCP server to the workspace config.
5. Add the image MCP server to the workspace config.

If the company moves you to Gemini, nothing here changes except the tool config.

## Still open

- Prompt files for Phases 4–6 do not exist yet. Add one when a pattern repeats.
- The 48-hour recap is written as a target. Confirm whether it is a hard rule;
  if not, move it from "Do" to "advice" in the guide.
- Repo home is `~/workflow/`, kept separate from `~/studio/`.
