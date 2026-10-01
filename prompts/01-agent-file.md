# 01 — Draft the agent file

**Use in:** Phase 2, Project Setup.
**Input:** the project folder, with client docs in `assets/`.
**Output:** a filled-in `agent.md`.
**Rule:** same artifact as the manual workflow — a readable orientation file.

---

Read the project folder. Start with `assets/` and `code/`, then any existing
`agent.md`, `research/`, or notes. Fill in `templates/agent.md` and write the
result to `agent.md`.

Fill these sections: Snapshot, What this project is, Who it's for, What exists,
What's missing, What's undecided, Structure, Decisions, Links. Leave Structure
and Decisions mostly empty if the project has not reached those phases.

Rules:

1. Use only what the documents support. Do not invent facts, dates, or names.
2. When something is unknown, write it as unknown and list it under "What's
   missing" or "What's undecided" with an owner placeholder `{owner?}`. Do not
   guess.
3. Keep "What this project is" to two or three plain sentences. No design
   jargon.
4. Point to real files and paths, not descriptions of files.
5. If the assets contradict each other, note the contradiction instead of
   picking a side.
6. Set **Status** to the furthest phase the documents actually support. If the
   assets already contain kickoff notes or decisions, the status is `Kickoff`,
   not `Setup`. Do not default to `Setup`. The status must never contradict the
   Decisions log or the Structure section.

When you are done, list every question you could not answer from the documents.
Ask only those, in one short list. Then stop.
