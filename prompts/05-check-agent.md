# 05 — Check the agent file

**Use in:** end of Phase 2, and any time you want a cold-read test.
**Input:** the project folder, nothing else.
**Output:** a pass/fail with specific fixes.
**Rule:** same artifact as the manual workflow — a file a model or teammate can
read cold.

---

Read only `agent.md`. Do not read `assets/`, `research/`, or `code/` for this
check. Then answer, in under a minute of reading:

1. What is this project?
2. Who is it for — audience, and who signs off?
3. What exists right now?
4. What is missing?
5. What is undecided, and who owns each item?

Then run these tests:

- **No-context test:** Were you able to answer all five without any other file?
  Name any question you could not answer.
- **Contradiction test:** Does anything in the file disagree with anything else
  in it?
- **Staleness test:** Is `Last updated` credible given Status? Does Status match
  the phase the file describes?
- **Owner test:** Does every item under "What's undecided" have an owner?
- **Plain-language test:** Could a non-technical teammate read this cold?

Output: a PASS or FAIL, then the specific lines to change. Be blunt. A file that
needs other files to be understood fails.
