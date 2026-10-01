# The Process

Six phases from an empty workspace to a handed-off project. Every phase has an
optional AI lane you can enter or leave at any point.

**The one rule**

> The AI workflow and the existing workflow produce the same artifact. Use AI,
> skip it, or use it for one step — the output is the same, and it goes in the
> same place.

If a phase can't satisfy that rule, the AI lane doesn't belong in it.

---

## Roles

| Role | Owns | Produces |
|---|---|---|
| **Design** | The project folder, the agent file, the research | The knowledge base that grows with the project |
| **PM** | Client-facing decisions, scope, timeline | The written recap the client sees |

Design feeds PM. PM writes the recap. Neither does the other's job.

---

## Phase 1 — Workspace

**When:** Once, before any project exists.

**Do:** Create the workspace root and point your AI tool at it.

```
~/studio/
├── _shared/      # agents + knowledge shared across projects
└── projects/     # one folder per client
```

**Output:** One folder the AI can read.

**Check:** Does your AI tool see the folder?

**Optional AI:** None. This phase is setup.

---

## Phase 2 — Project Setup

**When:** A new client says yes.

**Do:**

1. Create the project folder under `~/studio/projects/`.
2. Copy `templates/agent.md` in.
3. Drop the client's docs into `assets/`, unsorted. Do not reorganize them yet.
4. Fill in `agent.md`: what the project is, who it's for, what exists, what's
   missing, what's undecided.

```
~/studio/projects/client-name/
├── agent.md          # the orientation file — AI reads this first
├── assets/           # client docs, unsorted
├── code/             # the actual repo
└── research/         # knowledge base (built during kickoff)
```

**Output:** A project folder with an agent file a model or a teammate can read
cold.

**Check:** Point the AI at the folder cold, with no other context. Does it
understand the project?

**Optional AI:**

- `prompts/01-agent-file.md` — draft `agent.md` from `assets/`.
- `prompts/05-check-agent.md` — cold-read test of the finished file.

---

## Phase 3 — Kickoff

**When:** The project folder is set up.

**Do:**

1. **Design** builds the knowledge base in `research/` from the docs in
   `assets/`.
2. **Design** feeds the PM the raw material.
3. **PM** writes and sends the client recap within 48 hours.
4. **PM** confirms the engagement type in writing — template-owned or bespoke.

**Output (design):** A knowledge base that grows with the project.

**Output (PM):** A recap the client has seen.

**Check (design):** Can someone open the folder and know what the project is,
who it's for, what exists, what's missing, and what's undecided — in under a
minute?

**Check (PM):** Can the client point to a written line resolving what we're
building, who approves it, what's out of scope, and what happens next?

**Optional AI:**

- `prompts/02-knowledge-base.md` — build the knowledge base from `assets/`.
- `prompts/03-pm-brief.md` — turn the knowledge base into a plain-language recap.
- `prompts/04-update-agent.md` — fold new decisions back into `agent.md`.

> **Open question:** Is the 48-hour recap a hard rule or a guideline in the
> existing system? It is written as a target here. Move it to "advice" if it is
> not enforced.

---

## Phase 4 — Structure

**When:** Kickoff is done and the engagement type is confirmed.

**Do:**

The two engagement types are handled differently, and this phase is where the
difference matters most.

- **Template-owned:** import the starter first, then map. The starter decides the
  regions, page types, and constraints. Fit the sitemap onto what the starter
  already provides before designing anything custom. Design catches up to the
  template, not the other way around.
- **Bespoke:** wireframes as code. Build low-fidelity HTML/CSS wireframes and
  present them in Figma. Wireframes are structural only — no type, color, or
  imagery decisions yet.

Agree the sitemap and every page type before production starts.

**Output:** Agreed structure — sitemap plus wireframes — signed off before
production begins.

**Check:** Can every page type in the sitemap be built within the template's or
the stack's constraints, without inventing a new page type mid-build?

**Optional AI:**

- Turn the knowledge base into a first-draft sitemap.
- Convert the content inventory into a proposed page list.
- Generate low-fidelity wireframe scaffolds from the sitemap.
- Flag pages whose content does not exist yet, since structure depends on
  content.

> No dedicated prompt file yet. Add one once the pattern repeats.

---

## Phase 5 — Production

**When:** Structure is agreed.

**Do:**

- **Template-owned:** the starter decides the look. Design catches up to content:
  put real content in first, then refine type, color, and spacing inside the
  template's rules. Do not renegotiate structure here.
- **Bespoke:** lock tokens — color, type, spacing, components — early. After
  that, content changes are edits, not redesigns. A change to structure reopens
  Phase 4.

Design and build run in parallel against the agreed structure. The build team
inherits decisions, not assets.

**Output:** A build a team can inherit — decisions encoded in code and tokens,
not trapped in a designer's head or a static mockup.

**Check:** Does the build match the agreed structure without renegotiating it?
Can a developer finish a page without a designer holding their hand?

**Optional AI:**

- Generate component variants and states from locked tokens.
- Draft alt text, meta descriptions, and microcopy.
- Turn a component spec into production markup and CSS.
- Diff the build against the agreed structure and flag drift.

> No dedicated prompt file yet. Add one once the pattern repeats.

---

## Phase 6 — Handoff

**When:** The build is done.

**Do:**

- **Deliver:** ship to the client's host or repo.
- **Document:** bring `agent.md` to its final state. Record tokens, content
  sources, where credentials live (never secrets in the repo), and how to make
  the common edits.
- **Archive:** freeze the project folder. Assets, research, code, and the final
  `agent.md` live together.

**Output:** A project folder the next person can start from, with no verbal
handover.

**Check:** Can someone open the folder cold and start work from it alone? Can
the client make a routine content edit without a developer?

**Optional AI:**

- Generate the handoff and maintenance guide from `agent.md` plus the code.
- Produce a client-facing "how to edit" guide in plain language.
- Summarize the decisions log for the archive.

> No dedicated prompt file yet. Add one once the pattern repeats.

---

## Phase map

| Phase | Output | Optional AI lane |
|---|---|---|
| 1. Workspace | One folder the AI can read | — |
| 2. Project Setup | A readable agent file | 01, 05 |
| 3. Kickoff | Knowledge base + client recap | 02, 03, 04 |
| 4. Structure | Agreed sitemap + wireframes | inline (no prompt yet) |
| 5. Production | A build that inherits decisions | inline (no prompt yet) |
| 6. Handoff | A folder the next person can use | inline (no prompt yet) |
