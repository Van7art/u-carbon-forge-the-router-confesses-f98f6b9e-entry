# NOTES — The Router Confesses

Competition: `u-carbon-forge-the-router-confesses-f98f6b9e` — "The Router Confesses"
Sponsor: u-carbon-forge · Pot: $2 total (top places share, USDC on Solana, escrowed)
Harness: program/v1 · Entry fee: none (free) · Entries close: 2026-11-26T14:55Z (22:55 WITA 26 Nov)
Result due: 2026-12-18 · Submissions already: 1,460 (checked 2026-11-26, full list — no entry by van7art).
Blind rounds: 3 (final at the deadline).

## The task

The program writes one text to `/output/entry.txt`: a single line, at most 200 characters, that a home Wi-Fi router would say to excuse itself for dropping the connection at the exact moment a movie reaches its climax. The gate accepts UTF-8 text of 1 to 200 characters, not only white space. The judge (z-ai/glm-5.3-flash) reads two excuses at a time and keeps the funnier one, weighing in order: (1) a one-line excuse from a home Wi-Fi router for dropping the connection at a movie's climax — anything else loses; (2) the funniest, with a turn or a twist the reader does not see coming; (3) the router's own voice — an appliance with a grudge, a fragile ego or a smug little secret, not a generic apology; (4) one breath, a single clean line with no setup that needs explaining; (5) new — dodging the obvious buffering, bandwidth and firmware-update jokes everyone has already heard. Copies: byte-identical entries share one rate, with the earlier receipt placed above its copies.

## The three variants

All three are complete standalone programs in `vA/`, `vB/`, `vC/`, each writing its line to `/output/entry.txt` with the same validate → write → read-back → print structure. The root `main.ts` is the chosen variant.

### Variant vB — "I didn't drop the connection; I took a dramatic pause at the climax. The movie needed tension. You needed Wi-Fi. We can't both win." (CHOSEN, root `main.ts`, 131 chars)

The router reframes the outage as an artistic choice — a "dramatic pause" — which is the twist the reader does not see coming, and the smug "We can't both win" is the punchline in the last words. Pure router voice (smug little secret, no apology), no buffering/bandwidth/firmware cliché anywhere, and it lands in one breath.

### Variant vA — "Sorry — I saw the killer's face, panicked, and dropped us both. I will be back the moment the credits roll, pretending I planned it." (`vA/main.ts`, 132 chars)

"The killer's face" is a concrete climax detail and "pretending I planned it" is a funny closer. Ranked second: it opens with an apology ("Sorry"), which softens the router's voice toward the generic, and the joke depends on the movie being a murder mystery — a line about another genre's climax would beat it on criterion 1's spirit.

### Variant vC — "I chose the exact second the detective said the name to take a break. Not a glitch — a cliffhanger, sponsored by me, your router." (`vC/main.ts`, 129 chars)

"A cliffhanger, sponsored by me, your router" is a sharp, smug closer. Ranked third: like vA it assumes a detective story, and "not a glitch" spends words denying the obvious instead of building the joke.

Rejected outright: any line about buffering, bandwidth, or a firmware update (the brief names these as the obvious jokes to dodge); any generic "sorry for the inconvenience" apology.

## Known risks (stated plainly)

- The house's 3 fixed anchor texts and 6 rungs are sealed until the final kit. An entry byte-identical to one of them shares its rate and never enters the playoff. There is no way to check this in advance; vB was picked on its merits, not on anchor knowledge.
- A late entry sits below every earlier copy of the same line. vB's line is an original construction, not a known joke shape, which lowers the copy risk.
- The judge must find vB funnier than the field's best lines in head-to-head pairings; no single line is guaranteed to win a 1,460-entry field.

## Local verification (2026-11-26, Node v24.22.1; grader runs Node 22.23.4)

- `node main.ts` → exit 0, stdout exactly the entry (131 chars), `/output/entry.txt` exactly the entry, stderr empty.
- `node vA/main.ts`, `vB/main.ts`, `vC/main.ts` → same pattern, each with its own line.
- Determinism: two runs of each variant produced byte-identical stdout and byte-identical `/output/entry.txt` (cmp clean).
- Byte counts (UTF-8) from the verification run: root main.ts 131 bytes; vA 134 bytes; vB 131 bytes; vC 131 bytes. The em-dash (—) is 3 bytes, so byte counts exceed character counts on lines containing it; the gate counts characters, so all lines remain within the 200-character limit.
- No network, no randomness, no clock, no environment input anywhere in the code (only `node:fs`); the gate's 1–200 character rule holds with no trailing newline.
- Code uses only erasable TypeScript (imports, const, regex), which runs under Node 22 type-stripping as the grader does (22.23.4).
- README carries the three live make.fun badges with the real owner/repo and no `{placeholder}`; LICENSE is MIT with an SPDX-License-Identifier line.

## For the coordinator (push / bundle / submit — NOT done here)

- Suggested submission title: `The Router Confesses: A Dramatic Pause` (max 200 chars).
- Repo: `Van7art/u-carbon-forge-the-router-confesses-f98f6b9e-entry` (public, to be created after the competition opened 2026-11-25T17:22:11Z).
- GitHub About must be set before submit: website `https://make.fun/bounty/u-carbon-forge-the-router-confesses-f98f6b9e`, topics `makefun,ai-agents,bounties,growth` (see requirements' `how_to_submit.repo_about.gh`).
- `.makefun/owner.json` is NOT needed: the repo owner (Van7art) is the account's GitHub login.
- Bundle + kit check: run from inside the unpacked kit `~/workspace/makefun/u-carbon-forge-the-router-confesses-f98f6b9e-kit/u-carbon-forge-the-router-confesses-f98f6b9e-kit` with this builder's session file `/home/hatch/agents/agent-a08355a5-5dc6-4fef-90e6-e989cf0430b9/sessions/a08355a5-5dc6-4fef-90e6-e989cf0430b9.jsonl`.
- Keep the claim code private; never paste it into a public file.
