# WERTHER — Stage 1 design proposal

A state-graph adventure adaptation of *The Sorrows of Young Werther* (Boylan translation,
`werther.txt`). One path through the game is the novel; the dramatic question is whether the
player can leave it.

Status: **approved and built** — the game lives in `index.html` (single self-contained file,
deployable via GitHub Pages). All design checks below are enforced mechanically by a test
harness that drives the actual game graph.

---

## Revision (prose layer + choice density)

The graph, flags, gates, marks, endings, and verdicts of the original build stand. The prose
layer was rewritten to an inverted narrative stance:

- **The Editor narrates.** Every node is brisk third-person editorial summary with Werther's
  voice in short quoted flashes. **Letter voice now signals loss of agency**: full letters
  return at the two sanctioned set pieces (the Klopstock storm, N05; the pistol debate, N08)
  and flood back across the December endgame (N27 onward; N28–N30 exempt from all budgets;
  N29–N30 carry only hollow converging choices). The Editor returns once, at N31, to bury him.
- **Budgets:** default nodes ≤150 words of base text (enforced by the harness at 155);
  short nodes under 40 words for pace: N10, N16, N19, CAN, N22.
- **Choice density:** a choice at every node, no pure continues; 116 choices total. Trivial,
  flavour, and fatal forks are presented identically.
- **Second-tier memory ("mems").** Persistent, never-gating tints set by choices (e.g. the
  locked drawer of August returns in the last letter; the walnut-tree scandal chills the
  judge in December; the fever argument of 12 August fails before the bench). The five
  gating flags stay exactly as approved; mems only select sentences.
- **New forks:** W1 (the widow visited, June 1771), V1 (lingering at the vicarage with
  Frederica), C1 (the canary's kiss refused), WT1 (the walnut-tree protest), HM1 (an
  afternoon with mad Heinrich), plus converging conduct-forks (Albert warm/cool, the lad's
  September plea, the ribbon in the drawer). Old N02/N03 folded into N01; N21 split into
  N21/CAN/WAL — the canon spine remains exactly 31 stations.
- **Fixes:** Albert-continuity variant on the early-embassy path (N14 addresses a stranger);
  bridge node O2B for the O2→N22 seam; finis wording ("stations", not "letters"); dead
  sentinel-delete removed.

---

## Addendum: escape corridors

Three corridors leave the novel's geography entirely; none rejoins the spine; each ends in
its own FINIS (ending count now 9). Documentation thins with distance from the book:
précis → fragments → pay-books, bills of lading, playbills → the editor's open conjecture,
with lacunae rendered as "· · ·". Fidelity accounting simply reads low, as it should.

| corridor | entry (surface-ordinary choice) | gate / rarity | run | ending & verdict |
|---|---|---|---|---|
| **THE GALLERY** | third option at M1: the Mine-Master's winter contract | two coordinated non-canon choices (N18 mines → M1 stay) | G1–G5, Sept 1772 → 1775: survey work; Christmas below; the March flood known only from the pay-book ("seven came up alive"); a one-line 1774 scrap | E7 — "You went under the story, and it lost the sound of you." |
| **THE NORTH** | fourth option at N18: "ask the world for employment — anything, so it be far" | **gated on PATRON**; without it the letter goes unanswered and the spine resumes (tinted) | P1–P5, Jul 1772 → 1775: the Count's Petersburg commission; Riga and the sea; skating the frozen Neva on 21 December; white nights; a doubtful chalk portrait, "a lady with a bird upon her finger" | E8 — "You escaped by the breadth of a continent; the archive ends at the frontier." |
| **THE PLAYERS** | third option at ST4: ride a stage or two with a troupe | deep in the stay-branch (stay + flee already diverged) | T1–T4, Jun 1772 → 1774: scene-painting; prompting *Emilia Galotti* on 22 Dec 1772; a 1773 playbill — *The Friend of the House*, "Herr Wärther," misspelt | E9 — "You escaped into borrowed words, and no one could tell your voice from the play's." |

Corridor mems (never gating): TOOLCHEST (the Homer in the survey-chest, ribbon present only
if it was never locked in the Wahlheim drawer), LASTLETTER (the unsent Wahlheim letter the
editor declines to open), BADSEA ("the sea — failed"), LINDENS (two trees in every painted
forest), ASKEDLOVER. One engine touch: part-conditions may now require multiple mems
(`mem: [..]`), needed for the ribbon/drawer interaction in E7.

---

## Revision 2: the first-time reader

A comprehensibility and pacing pass; graph, flags, mems, gates, endings, corridors, and
verdicts unchanged.

- **Full first-time-reader audit** (83 targeted rewrites): every character introduced at
  first appearance and re-introduced on return (Wilhelm named as the letters' addressee in
  N01; Albert as "Charlotte's promised husband"; the peasant-lad, Frederica, Madame S—, the
  flower-hunter Heinrich all restated); every allusion glossed in passing or cut (Klopstock
  identified as the poet and his ode; "particles" become the ambassador's grammar;
  raree-show, Lavater, the king's shilling, "kanne", "Lear", "assizes", "Emilia Galotti"
  all glossed or replaced); every callback restates what it calls back to (the fever
  argument, the June meddling, the walnut-tree scandal, the friend-of-the-house playbill).
- **Choice-label legibility:** all ~90 labels audited; no pronoun without a same-sentence
  antecedent; objects of actions named (the N01 widow/Charlotte misbinding fixed per spec).
- **June 16 lightened:** N04 cut to ~120 words (warning, bread-cutting, "Albert is a worthy
  man," the waltz question); the N05 set piece enters at "Never did I dance more lightly,"
  drops the waltz vow, and runs straight to the storm and the glossed Klopstock moment.
- **Endgame de-costumed:** N29→N30 and N30→N31 each carry a single bare option, "(the
  letter continues)" — the visible death of choice. Standing no-continue rule suspended
  inside the canon endgame only.
- Word budget re-enforced everywhere (≤150 outside the three set pieces; harness-checked).

---

## 0. Frame

- The game opens with Goethe's Preface in the editor's voice ("I have carefully collected
  whatever I have been able to learn of the story of poor Werther…") as the title screen,
  then hands narration to Werther's first person — mirroring the novel and quietly planting
  the Herausgeber mechanic before the player knows it is a mechanic.
- Every node is a dated letter (or, late on the canon path, an editor passage). Every action
  moves the calendar strictly forward; the graph is acyclic by construction.
- **Starting node: N01, May 4, 1771** (the novel's first letter, lightly trimmed).

## 1. Node list

51 nodes: 31 on the canon spine (adapted from Goethe), 20 invented branch nodes.
"Feeds" lists the letters (by date) that supply each node's text.

### Canon spine — Book I (1771)

| id | date | content | feeds |
|----|------|---------|-------|
| N01 | May 4 | Arrival: flight from Leonora, the aunt's business, spring solitude | May 4 |
| N02 | May 10–27 | The idyll: Homer at the fountain, Walheim discovered, the children | May 10, 12, 13, 15, 17, 22, 26, 27 |
| N03 | May 30–Jun 15 | The peasant lad's confession of love for the widow; the invitation to the ball | May 30 (+ short invented bridge) |
| N04 | Jun 16 | **The ball**: Charlotte cutting bread; the aunt's warning; the storm; "Klopstock!" — **FORK F1** | Jun 16, 19 |
| N05 | Jun 21–Jul 8 | Settled at Wahlheim; the vicarage of S— (Frederica); the fountain baptism | Jun 21, 29, Jul 1, 6, 8 |
| N06 | Jul 13–26 | "She loves me!"; the touched fingers; her melody; Wilhelm's embassy proposal — **FORK F3** | Jul 10, 11, 13, 16, 18, 19, 20, 24, 25, 26 |
| N07 | Jul 30–Aug 10 | Albert arrives; the strange threefold peace | Jul 30, Aug 8, 10 |
| N08 | Aug 12 | The pistols; the suicide debate with Albert | Aug 12 |
| N09 | Aug 15–28 | Nature turns devouring monster; the birthday ribbon | Aug 15, 18, 21, 22, 28 |
| N10 | Aug 30–Sep 3 | Breaking point; Wilhelm's ultimatum: go — **FORK F4** | Aug 30, Sep 3 |
| N11 | Sep 10 | The farewell under the chestnut trees; departure by night | Sep 10 |

### Canon spine — Book II (1771–72)

| id | date | content | feeds |
|----|------|---------|-------|
| N12 | Oct 20–Dec 24 | The embassy at D—: the ambassador's particles; Count C's friendship | Oct 20, Nov 26, Dec 24 |
| N13 | Jan 8–Feb 8, 1772 | Winter; the storm-bound letter to Charlotte; Miss B— — **flag choice F5 (BELLA)** | Jan 8, 20, Feb 8 |
| N14 | Feb 17–20 | The reprimand; news that Albert and Charlotte are married | Feb 17, 20 |
| N15 | Mar 15–16 | The assembly at Count C's; driven from the company; Miss B—'s tears — sets **SCAR**; **FORK F6** | Mar 15, 16 |
| N16 | Mar 24–Apr 19 | Resignation tendered and granted — **flag choice F7 (PATRON)** | Mar 24, Apr 19 |
| N17 | May 5–9 | Pilgrimage to the native town; arrival at the Prince's lodge | May 5, 9 |
| N18 | May 25–Jun 11 | The army scheme dissuaded; restlessness at the Prince's — **FORK F8** | May 25, Jun 11 |
| N19 | Jul 16–29 | The wanderer; "I wish to be near Charlotte again, that is all" | Jul 16, 18, 29 |
| N20 | Aug 4–21 | Wahlheim again: little John dead; the changed gate | Aug 4, 21 |
| N21 | Sep 3–15 | The canary's kiss; the blue coat; the walnut trees felled; the lad dismissed | Sep 3, 4, 5, 6, 12, 15 |
| N22 | Oct 10–27 | "Ossian has superseded Homer" — **flag choice F10 (POET)**; the void | Oct 10, 12, 19, 26, 27 |
| N23 | Oct 30–Nov 22 | Wine reproof; "dear Werther"; the religion letter | Oct 30, Nov 3, 8, 15, 21, 22 |
| N24 | Nov 24–30 | The vow to her lips; Heinrich the madman among the rocks | Nov 24, 26, 30 |
| N25 | Dec 1–6 | Heinrich was her father's secretary; "play that air no longer" | Dec 1, 4, 6 |
| N26 | Dec 7–10 | The murder at Walheim; the failed defense; "You cannot be saved, unfortunate man!" — **FORK F11** | editor's report, recast as a letter in the manner of Mar 15 |
| N27 | Dec 12–15 | The flood at midnight ("Plunge!"); the dream embrace — **FORK F12** | Dec 12, 15 |
| N28 | Dec 20 | Her injunction: not before Christmas Eve; "we cannot go on in this manner" — **FORK F13** | Dec 20 + editor |
| N29 | Dec 21 | **EDITOR.** The Ossian night: the reading, the embrace, the locked door. No choices. | editor + Ossian passage + "It is all over, Charlotte" |
| N30 | Dec 22 | **EDITOR.** The note for the pistols; her trembling hands; the last letters. No choices. | editor + final letter fragments |
| N31 = **E1** | Dec 23 | **EDITOR. Ending: The Sorrows** — the shot at midnight; death at noon; burial by night, no priest | closing pages, near-verbatim |

### Branch nodes (invented; motifs reused from the letters cited)

| id | date | content | goes to |
|----|------|---------|---------|
| A1 | Jun 19–Jul 5, 1771 | The guarded summer: art succeeds for once, heart on a leash; she is at the fountain anyway — **FORK F2** | N06 or A2 |
| A2 | Aug–Sep 1771 | The post accepted (the very post of Jul 20/Aug 22); leave-taking; first weeks at D— | **J2 →** N12 |
| ST1 | Oct 1771 | Staying: the harvest; three at the hunting-lodge; Albert watching | ST2 |
| ST2 | Nov 1771–Jan 1772 | Winter closeness and strain; Charlotte's warmth and her firmness | ST3 |
| ST3 | Feb 20, 1772 | The wedding, witnessed — **FORK F14** | ST4 or ST5 |
| ST4 | Mar–Jun 1772 | Flight: the native village, the roads, anywhere | **J3 →** N19 |
| ST5 | Mar–Jul 1772 | Remaining: the closed door; Albert's request that he come less often | **J4 →** N20 |
| L1 | Apr 1772 | After the declaration: the aunt's war; Count C's protection | L2 |
| L2 | May 1772 | Her answer; rank renounced; resignation with head high | E2 |
| **E2** | Jun 16, 1772 | **Ending: The Answer** — betrothed to Miss B—, one year to the day after the ball | — |
| O1 | Apr–Jun 1772 | Endurance: the apology performed; the particles learned | O2 |
| O2 | Jul–Sep 1772 | Advancement; the mirror shows the ambassador — **FORK: relapse or remain** | **J6 →** N22, or O3 |
| O3 | Oct–Dec 1772 | The office in winter; life in fair copy | E3 |
| **E3** | Dec 23, 1772 | **Ending: The Particle** — a perfectly punctuated memorandum, dated the day of the other Werther's death | — |
| M1 | Jul–Aug 1772 | The mines of —: descent into the earth; the pull of the surface | **J5 →** N21 |
| R1 | Dec 8–14, 1772 | The ride for a pardon; the patron's door at midnight | E4 |
| **E4** | Dec 24, 1772 | **Ending: The Pardon** — commutation won; "You are saved, unfortunate man. Whether we are saved, I know not." Werther leaves Wahlheim alive | — |
| H1 | Dec 24, 1772 | Christmas Eve among the children; the promised gift ("You shall have a gift too, if you behave well") | E5 |
| **E5** | Jan 1, 1773 | **Ending: The Christmas Gift** — the children's New-Year wishes, "and one for Werther"; the house-friend lives | — |
| **E6** | Dec 12, 1772 | **Ending: The Flood** — the plunge taken; a half-page from the editor: only the hat found on the rock | — |

## 2. Forks and joins

### Forks

| fork | node | options (canon first) | consequence |
|------|------|----------------------|-------------|
| F1 | N04 | **Waltz with her** (sets WALTZ) / guard your heart | canon → N05; guard → A1 |
| F2 | A1 | Seek her circle after all / write Wilhelm for the post | → N06 (rejoin) / → A2 |
| F3 | N06 | **Refuse the embassy post** / accept it | canon → N07; accept → A2 |
| F4 | N10 | **Leave in September** / stay at Wahlheim | canon → N11; stay → ST1 |
| F5 | N13 | **She is only your mirror** / look at Miss B— and see *her* (sets BELLA) | flag only; both → N14 |
| F6 | N15 | **Resign in wounded pride** / endure and remain in service / declare yourself to Miss B— | canon → N16; endure → O1; declare: BELLA → L1, else gentle rebuff, inline → N16 |
| F7 | N16 | **Leave in silence** / part from Count C as a friend (sets PATRON) | flag only; both → N17 |
| F8 | N18 | **Yield to the Prince's reasons and drift** / open your heart to him (sets PATRON) / go to the mines | canon & candor → N19; mines → M1 |
| F10 | N22 | **Carry Ossian into the winter** (POET=OSSIAN) / keep to Homer (POET=HOMER) | flag only; both → N23 |
| F11 | N26 | **Accept the note's despair** / ride for a pardon | canon → N27; ride: PATRON → R1 → E4, else the door stays shut, inline → N28 |
| F12 | N27 | **"My hour is not yet come" — turn home** / yield to the abyss | canon → N28; yield: OSSIAN → E6, else rooted to the earth, inline → N28 |
| F13 | N28 | **"Today or never" — defy her** / obey her | canon → N29; obey: HOMER → H1 → E5, else the involuntary consent ("he would pause, seem desirous of returning, but would nevertheless proceed"), inline → N29 |
| F14 | ST3 | Flee at last / remain even now | → ST4 / → ST5 |

Fork at O2 (relapse to Wahlheim → J6, or remain → O3) is listed above in the node table.

### Joins (Markovian merges; forgetting narratively plausible)

| join | edge | plausibility of forgetting |
|------|------|-----------------------------|
| J1 | A1 → N06 | two July weeks in her company erase one guarded evening |
| J2 | A2 → N12 | by late October everyone sits at the same desk; N12 rewritten merge-agnostic (no "arrived yesterday") |
| J3 | ST4 → N19 | "Once more I am a wanderer" fits any road that led here |
| J4 | ST5 → N20 | the Aug 4 letter (the widow's dead child) reads identically for one who stayed |
| J5 | M1 → N21 | September in Wahlheim; the return itself is barely mentioned in the letters |
| J6 | O2 → N22 | October: "Only to gaze upon her dark eyes" — how he got back matters to no one, least of all him |
| J7–J9 | failed attempts at F6 / F11 / F13 (and rooted-fail at F12) merge inline into N16 / N28 / N29 / N28 | each failure is a flag-tinted opening paragraph of the target node, not a separate node |

Goethe's own precedent: the embassy detour of Book II merges back into Wahlheim almost
seamlessly; J4–J6 imitate exactly that gesture.

## 3. Flags (5)

Rule as implemented: **the choice set at every node is identical for every player** — flags
never add or remove visible options, so the graph the player sees stays Markovian. Flags do
two things: (a) tint text (conditional paragraphs/phrases inside nodes), and (b) at exactly
four marked points (F6-declare, F11-ride, F12-yield, F13-obey) decide whether an *attempted*
escape succeeds or falls back to the spine. This outcome-deciding role is a deliberate,
minimal extension of the "flags only tint" rule — declared here for approval — because merges
erase history, and without it every late escape would be equally available to every player,
i.e. trivial. It is also the game's thesis made mechanical: **you may always choose; the
flags decide whether the choice can still be executed.**

| flag | set at | tints | decides |
|------|--------|-------|---------|
| WALTZ | F1 (canon) | depth of every ball-memory: the ribbon (N09), Klopstock echoes, the editor's retrospect, a shadow paragraph in E2 ("and if, some evenings, a waltz heard through a window…") | — |
| SCAR | event, N15 (embassy paths only) | the revived mortification in autumn nodes and the editor's canon recap (Goethe's own line: "the mortification he had suffered at the ambassador's… revived in his memory") | — |
| BELLA | F5 | the rebuff paragraph in N16; autumn regret touches; a face at a window in E3 | outcome of F6-declare |
| PATRON | F7 or F8 | the Count's/Prince's letters in later nodes; warmth in R1/E4 | outcome of F11-ride |
| POET (OSSIAN/HOMER) | F10 (canon = OSSIAN) | Oct–Dec imagery: mists, torrents and ghosts vs. hearth, pease and the suitors of Penelope | outcomes of F12-yield **and** F13-obey |

## 4. Endings (6) and triggers

| id | date | name | voice | trigger |
|----|------|------|-------|---------|
| E1 | Dec 23, 1772 | **The Sorrows** (canon) | editor, Goethe's restraint, near-verbatim | canon choices throughout; reached by default whenever every escape fails or is declined |
| E2 | Jun 16, 1772 | **The Answer** (kitsch, love found) | letters to the last; Werther's overwrought rhetoric weaponized for joy; closing mock-editor footnote: "Here the correspondence ceases; happiness, unlike sorrow, keeps no journal." | BELLA set at F5, then declare at F6 |
| E3 | Dec 23, 1772 | **The Particle** (survival in body, not spirit) | first person that gradually adopts the ambassador's style — loss of self *inside* the first person, the inverse of the Herausgeber move | endure at F6, remain at O2 |
| E4 | Dec 24, 1772 | **The Pardon** (redemption displaced onto the peasant lad, Werther's explicit double — "it is the history of your friend!") | letters; last one from the winter road | PATRON set (F7 or F8), then ride at F11 |
| E5 | Jan 1, 1773 | **The Christmas Gift** (survival inside her orbit, on her terms) | letters; the children's New-Year wish closes it | POET=HOMER at F10, then obey at F13 |
| E6 | Dec 12, 1772 | **The Flood** (the other death — leaving Goethe's path and finding Ossian's waiting) | editor, but only a conjectural half-page: the hat found on the rock (Goethe plants the image himself) | POET=OSSIAN, then yield at F12 |

Herausgeber rule, applied: first person is kept as long as agency is kept. Crossing the point
of no return (F13-defy, or F13-obey failing under OSSIAN) switches to the editor for
N29–N31, which contain **no choices**. Death by water (E6) likewise gets the editor. All
surviving endings (E2–E5) stay in Werther's own hand.

Meaning worth noting: E4 is only reachable by players who went away *and* made a friend there
— the embassy detour, which canon-Werther experienced as pure loss, is precisely what gives
you the power to save the lad in December.

## 5. Fidelity tracking

- Each node is tagged canon / off-canon; each fork records whether the canon option was taken.
- End screen reveals: ending name; **fidelity** = canon nodes visited ÷ 31; the **divergence
  log** (dates where the player's choice left Goethe's); and a verdict line —
  - E1: "You died on Goethe's schedule."
  - E2: "You escaped the novel on {date of first permanent divergence}."
  - E3: "You left the story; the story did not notice."
  - E4: "Goethe's December took a life; you gave one back."
  - E5: "You remained within her orbit, and outside the book."
  - E6: "You left Goethe's path and found the other death waiting."

## 6. Design checks

### 6.1 Reachability — PASS

- No orphans: all 51 nodes lie on a path from N01 (spine by construction; A1/A2 via F1–F3;
  ST1–ST5 via F4/F14; L/O chains via F6; M1 via F8; R1 via F11; H1 via F13; endings as listed).
- No dead ends: every non-ending node has ≥1 outgoing edge; every conditional (attempt)
  outcome has a fallback edge to the spine; E1 is the sink of last resort.
- Every ending attainable — witness paths:
  - **E1**: canon choices at F1, F3, F4, F5, F6, F7, F8, F10, F11, F12, F13.
  - **E2**: canon to N13 → BELLA → canon N14 → declare at F6 → L1 → L2 → E2. (Also reachable
    by the guarded route A1 → A2 → N12 → …)
  - **E3**: canon to N15 → endure → O1 → O2 → O3 → E3.
  - **E4**: canon to N16 → PATRON at F7 → canon to N26 → ride → R1 → E4. (Or PATRON at F8.)
  - **E5**: any Wahlheim-autumn route to N22 → HOMER → canon to N28 → obey → H1 → E5.
  - **E6**: canon to N27 (POET=OSSIAN) → yield → E6.
- Acyclicity: verified — every edge moves the calendar forward (e.g. ST4 Mar–Jun → N19 Jul;
  O2 Sep → N22 Oct; M1 Aug → N21 Sep; R1 Dec 14 → E4 Dec 24).

### 6.2 Canon replication — PASS

A player mimicking Werther makes exactly the choices Werther makes in the novel, and each is
the most Werther-ish reading of its node: waltz (F1), refuse the post (F3 — the Jul 20 letter
verbatim), leave in September (F4), keep Charlotte as the only original (F5), resign in
wounded pride (F6), leave in silence (F7), yield to the Prince and drift (F8), carry Ossian
(F10 — the Oct 12 letter verbatim), accept the note's despair (F11 — he *did* attempt the
defense; that is inside the node for everyone), turn home from the flood (F12 — "my hour is
not yet come"), and "today or never" (F13). This visits N01–N31 in order — all 31 canon
nodes, no invented node — and ends at E1 with the editor's report and the novel's own
closing sentences. Fidelity reveal: 100%, "You died on Goethe's schedule."

### 6.3 Non-triviality — PASS (with the calendar's gravity made explicit)

- **Early exits rejoin.** Guarding your heart at the ball leads to the fountain, where she is
  anyway (J1). The early embassy is the same embassy (J2). The mines give you back (J5). Even
  the official can relapse (J6). Fleeing the wedding puts you on the road that bends to
  Wahlheim (J3).
- **Good escapes need coherent counter-lives.** Minimum deviations from canon, and their
  temporal spread: E2 = 2 deviations (Jan + Mar); E4 = 2 (Apr or Jun + Dec); E5 = 2 (Oct +
  Dec). In each case the first deviation is months before the payoff and looks unrelated —
  the player must live differently, not merely click differently at the end.
- **Single-deviation exits are Pyrrhic by design.** F6-endure escapes the plot in one move but
  into E3, the hollowest ending. F12-yield escapes in one move but into E6, a death. Cheap
  escapes exist; they cost the soul or the body — which is the point.
- **Late escapes fail against a canonical past.** A player who has been Werther all along
  (OSSIAN set) and tries to obey Charlotte on Dec 20 finds the novel's own sentence waiting:
  he pauses, seems desirous of returning, and nevertheless proceeds. Loss of agency arrives
  *before* the loss of first person, exactly on schedule.

## 7. Liberties and small notes (for approval)

1. **Attempt mechanic** (§3): flags decide the outcome of four attempted escapes. Declared
   deviation from the strict "flags only tint" rule; rationale above.
2. **Merge-agnostic rewrites**: N12, N19, N20, N21, N22 will be lightly adapted so they read
   truly for every history that merges into them (e.g. N12 loses "We arrived here yesterday").
3. **N26 voice**: the murder and failed defense, editor-narrated in the novel, will be recast
   as a Werther letter in the manner of his Mar 15 "plain and simple narration," so the
   Herausgeber switch stays reserved for the point of no return.
4. **The ball is unavoidable** (no "skip the ball" option): the inciting event is the game's
   premise; the first real choice is *inside* it (the aunt's warning answered).
5. `werther.txt` still carries the Project Gutenberg license tail (from line ~4079); contrary
   to the build prompt it was not fully stripped. Public domain either way; the game will not
   include it.

## 8. Stage 2 preview (not for approval now)

Single self-contained HTML file; 1771-paper look (laid paper, ink, long-s optional and
probably resisted); goatcounter snippet in `<head>`; lowercase italic "steffen huck" footer
link; GitHub Pages, this repo.

---

## Revision 3: openings and acknowledgments

Every node opening re-anchored for a reader landing on it cold: Werther is named in the
first sentence of nearly every node (and fully introduced in N01 as "a quick pencil, a
pocket Homer, a heart in questionable repair"); the ball node explains the partner, the
aunt, and the cousin before the aunt speaks. And every choice is now acknowledged in the
first line or two of its target node, via the one-node mark mechanism (~60 new
acknowledgment lines, e.g. arriving at the ball from the widow's farm: "Werther said
nothing more of the farm, and carried the lad's picture home unbroken. And midsummer
came."). Exceptions, by design: structural continuations where the whole node is the
consequence, gate failures (already acknowledged), the endgame's bare option, and the
hollow fading pairs deep in the escape corridors. The harness now verifies the wiring both
ways: every choice mark has a matching part in its target, every mark part has a producer.
Also fixes three latent header bugs (WAL, ST3, ST5 showed no date line on some paths).
