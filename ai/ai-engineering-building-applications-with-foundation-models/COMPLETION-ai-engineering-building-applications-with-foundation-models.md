# COMPLETION · AI Engineering: Building Applications with Foundation Models

Bilingual VI/EN book-companion site · 12 pages · audited by `book-fidelity-auditor`

**Source book:** Chip Huyen, *AI Engineering: Building Applications with Foundation Models*,
O'Reilly Media, 1st edition, December 2024 (ISBN 9781098166304).

**Verdict: PASS** — with the caveats recorded below. Re-audited whole-site on 2026-10-27
after a citation rework across all ten chapters; still PASS. See the two re-audit sections at
the end (Chapter 1, then the whole-site ch2–10 round).

## Per-page results

| Page | book-qa | Layer balance | Cites / refs | Nav |
|---|---|---|---|---|
| `index.html` | PASS (cover) | 35 + 20 = 55 ✓ | 1 / 3 | 11 outbound, all resolve |
| `mind-map.html` | PASS (synthesis) | 66 + 55 = 121 ✓ | 24 / 3 | 11 outbound, all resolve |
| `chapter-1-introduction-to-building-ai-applications-with-foundation-models.html` | PASS | 103 + 41 = 144 ✓ | 24 / 26 | index → ch2 |
| `chapter-2-understanding-foundation-models.html` | PASS | 83 + 79 = 162 ✓ | 21 / 21 | ch1 → ch3 |
| `chapter-3-evaluation-methodology.html` | PASS | 105 + 33 = 138 ✓ | 17 / 17 | ch2 → ch4 |
| `chapter-4-evaluate-ai-systems.html` | PASS | 91 + 38 = 129 ✓ | 23 / 25 | ch3 → ch5 |
| `chapter-5-prompt-engineering.html` | PASS | 91 + 34 = 125 ✓ | 15 / 15 | ch4 → ch6 |
| `chapter-6-rag-and-agents.html` | PASS | 87 + 37 = 124 ✓ | 14 / 14 | ch5 → ch7 |
| `chapter-7-finetuning.html` | PASS | 92 + 32 = 124 ✓ | 20 / 20 | ch6 → ch8 |
| `chapter-8-dataset-engineering.html` | PASS | 81 + 38 = 119 ✓ | 19 / 19 | ch7 → ch9 |
| `chapter-9-inference-optimization.html` | PASS | 116 + 32 = 148 ✓ | 26 / 26 | ch8 → ch10 |
| `chapter-10-ai-engineering-architecture-and-user-feedback.html` | PASS | 79 + 52 = 131 ✓ | 13 / 13 | ch9 → end of series |

Layer balance is the identity `standard-copy + vi-only == en-only`. It holds exactly on all
twelve pages. Every `en-only` element carries `lang="en"` — zero violations site-wide. The
per-chapter gap between `standard-copy` and `easy-only` is accounted for by `deep-only`
containers, which have no easy-mode twin by design.

## Site level

- **book-qa:** 12 / 12 PASS.
- **Links:** 51 internal `.html` hrefs, every target present on disk. Zero dead local links.
- **Anchors:** zero dangling `#id` across all twelve pages.
- **Citations:** every inline `<span class="cite"><a href="#ref-N">` resolves to an
  `<li id="ref-N">` carrying an external `https://` link. After the 2026-10-27 rework only
  **4** uncited ref entries remain — the author-page / `aie-book`-repo further-reading pair in
  ch1 and ch4; every other chapter wired or dropped that pair, so cites == refs there.
- **arXiv verification:** 105 arXiv refs site-wide at the first audit (the 2026-10-27 rework
  added ~15 more across ch3–ch8; see the whole-site re-audit section). Verified by fetching
  `<meta name="citation_title">` from `arxiv.org/abs/<id>` and matching it against the
  ref-list text — an HTTP-200 existence check would not catch a citation pointing at the
  wrong real paper. The main session checked ~99; the auditor independently re-checked 15,
  including the five whose author surnames appear nowhere in the book's own prose
  (Hoffmann/Chinchilla 2203.15556, Tan/Cappy 2311.06720, Raheja/CoEdIT 2305.09857,
  Chiang/Chatbot Arena 2403.04132, Liang/HELM 2211.09110). All matched on title and first
  author.
- **Non-arXiv URLs:** 200, except `oreilly.com/library/view/…` which returns 403 to curl —
  bot-blocking, not a broken link.
- **Modes / namespace:** all twelve pages carry the three reading modes (`quick` / `easy` /
  `deep`), `STORAGE_KEY = "aie-reading-mode"`, `LANG_KEY = "aie-lang"`, and the anti-FOUC
  reader in `<head>`. Hero tags: `AI ENGINEERING` (cover), `AI ENGINEERING / MAP` (mind map),
  `AI ENGINEERING / 01`…`/ 10` (chapters).

## Faithfulness

The book's own text was staged to `src/book-text/` (`ch01.html`–`ch10.html`, `preface01.html`,
`toc01.html`) and given to every authoring agent as its primary source, so specifics are
greppable back to the book rather than written from recollection.

Auditor sample: 67 numeric specifics (6–9 per chapter), ~110 author-surname attributions, and
~60 English quoted phrases, all checked against `src/book-text/`. Every content-bearing
specific resolved to its own chapter's source. Zero unsourced, invented, or mis-cited
specifics found. Tables reproduced exactly, including ch9's Table 9-1 MFU row (175B/V100
21.3%, 4096 TPUv3 32.5%, 2240 A100 30.2%, 6144 TPUv4 46.2%) and ch10's Table 10-1
(3702/26.54%, 2260/16.20%, 137/0.99%).

Contested and derived figures are preserved rather than smoothed: ch2 keeps the Villalobos
2022-vs-2024 caption mismatch and the Schulman/InstructGPT RLHF contradiction as the book has
them; ch3 records that LangChain's live page does not contain the 58% figure attributed to it;
ch4 marks the HELM $80k–$100k range as the author's derivation from $38,000 plus 19,500
GPU-hours at $2.15–$3.18/hr. Sources that could not be reached carry book-attribution with no
invented URL: as of the ch1 citation rework these are the Washington Post C4 interactive in ch2
and McKinsey in ch1 — ch1's McKinsey now carries its real URL (ref-16) but is bot-blocked to
every fetch route tried, so its figure stays book-attributed and flagged below. Duolingo in ch1
is no longer in this list: it is now cited (ref-22) and verified live.

## Defect found and fixed

`chapter-8-dataset-engineering.html` ref-15 named Perez et al., "Discovering Language Model
Behaviors with Model-Written Evaluations" but linked `arxiv.org/abs/2212.09689`, whose actual
`citation_title` is "Unnatural Instructions: Tuning Language Models with (Almost) No Human
Labor". The ID exists, so an HTTP-200 check passed it; only title-matching caught it. Corrected
to `2212.09251`. The underlying claim was confirmed sound against `src/book-text/ch08.html`
before the fix. Verified: `2212.09689` → 0 occurrences, `2212.09251` → 2.

## Caveats travelling with this PASS

1. **Curator-region assertion not independently verified.** The directory is not a git
   repository, so the auditor had no baseline and declined to record a check it did not run.
   The main session took a byte-for-byte snapshot to `/tmp/pre_curator/` before the curator
   ran; `cmp` against it showed only `index.html` changed (52 lines), with all eleven content
   pages byte-identical. That is main-session evidence, not a second pair of eyes.
2. **Faithfulness is spot-checked, not exhaustive.** The sample above is broad across ten
   dense chapters, but it is a sample.

## Non-blocking notes

- `chapter-5-prompt-engineering.html` renders the next-arrow left of its label (`▶ Chương sau`)
  where the other nine render it right (`Chương sau ▶`). Purely visual; NAV-fence region.
- `book-qa` reports a title collision on ch9 only when ch9 is passed as its own template — an
  artifact of template choice, not a page defect.

## Open judgment call, ruled not a defect

`index.html` `#how-to-read`, the "Đầy đủ" info-block: the Vietnamese heading describes the deep
reading mode while the English heading reads "Shared preferences". The four English headings
form their own coherent sequence (Vietnamese · 3 modes / English · standard / Shared
preferences / Where to start), each with body copy matching its own heading, and the two
languages are never visible simultaneously. Inherited from the scaffold site's documented
pattern. Not a mistranslation; does not block PASS.

## Chapter 1 citation re-audit (2026-10-27)

Chapter 1 previously routed 130 of 148 `<span class="cite">` anchors to ref-1 (the book itself).
The rework split every third-party figure off ref-1 onto its own `[N]`, lifting the chapter from
12 to 26 ref entries (24 now cited; ref-2 and ref-3 stay as further-reading). Diff touched only
the prose + ref-list region — `<style>`, `<script>`, and the `NAV:START…NAV:END` fences are
byte-unchanged, so `book-cover-curator` had nothing to integrate (roster and neighbours are
unchanged). New prose: masked-vs-autoregressive with the completion-machine metaphor, the
product-first order in AI-vs-full-stack (ref-26), and the Oct-2023 Executive Order / IP risks
under Maintenance. Layer identity still holds exactly: `standard-copy` 103 + `vi-only` 41 ==
`en-only` 144. `book-qa`: PASS.

Three figures lost their hard numbers because no live primary source could be found, rather than
keep a borrowed cite — now hedged and attributed to the book via ref-1: Salesforce's "74%",
Gartner's "7% business continuity", and GDPR's "$9B".

The 14 new refs (ref-13 → ref-26) were checked live. Core figures — no divergence found:

| ref | Source | Live check |
|---|---|---|
| 13 Goldman Sachs | $100B US / $200B global by 2025 | MATCH (verbatim) |
| 14 FactSet | ≈⅓ of S&P 500 cite AI, Q2 2023, highest in 10+ yrs | MATCH (177/500 = 35.4%; "at least 2010") |
| 15 WallStreetZen | 4.6% vs 2.4% stock move | MATCH (verbatim) |
| 16 McKinsey | 2× docs / 25–50% code productivity | **BOT-BLOCKED — not independently verified** |
| 17 TechCrunch | Magic $320M | MATCH |
| 18 TechCrunch | Anysphere $60M | MATCH |
| 19 Sacra | Midjourney ≈$200M ARR (estimate) | MATCH on figure + "estimate"; "late 2023 / 1.5 yrs old" is book-attributed, not on Sacra |
| 20 The Information | Copilot >$100M ARR | MATCH on figure (public headline); "two years after launch" behind paywall, book-attributed |
| 21 CNBC | Chegg stock fell on ChatGPT | MATCH (−48.41%) |
| 22 Duolingo | 4 course-creation stages, personalisation gains most | MATCH ("This is where AI shines!") |
| 23 NewsGuard | 393 ads / 141 brands | MATCH (exact) |
| 24 Fortune Business Insights | IDP $12.81B by 2030, 32.9% CAGR | MATCH (verbatim, via Yahoo syndication) |
| 25 a16z | internal-facing apps shipped faster | MATCH |
| 26 Latent Space | "The Rise of the AI Engineer" (Shawn Wang, 2023) | Title + date (2023-06-30) MATCH; author byline now shows only "Latent Space" — Shawn Wang attribution is book-faithful, not confirmed by the live byline |

Net: 13 of 14 new refs have their core figure confirmed against the live source. ref-16 (McKinsey)
is bot-blocked to WebFetch, mcp-fetch, r.jina.ai, and an archive.org snapshot (rate-limited); its
figure stays book-attributed and is flagged here rather than silently treated as verified. The
secondary details on ref-19/20/26 are the book's own framing (greppable in `src/book-text/ch01`),
carried through faithfully, not auditor-invented.

## Whole-site citation re-audit — chapters 2–10 (2026-10-27)

The same citation rework done for ch1 was applied to ch2–10, one `book-chapter-author` per
chapter in three waves of three, then verified whole-site by `book-fidelity-auditor`. Each
chapter split its third-party figures off ref-1 onto their own live `[N]`, wired or dropped the
author-page/repo orphan pair, and filled a few gaps against its source chapter. Every diff is
confined to prose + ref-list — `<head>`, `<style>`, both `<script>`s, the `NAV:START…NAV:END`
fences and the section-rail are byte-identical in all nine chapters (git-diff confirmed). No
chapters were added or removed, so `book-cover-curator` had nothing to integrate (roster, cover
cards and nav chain unchanged). The per-page table above carries the new layer-balance and
cite/ref counts; the identity `standard-copy + vi-only == en-only` holds on all twelve pages.

New external refs added per chapter (all fetched live unless flagged bot-blocked):

| Ch | New refs | Notes |
|---|---|---|
| 2 | Yennie Jun (token tax), OpenAssistant/LAION, Sorscher | +wired the 2 previously-orphan refs; SemiAnalysis power + LinkedIn YAML kept book-attributed (unverifiable) |
| 3 | Chatbot Arena/LMSYS, Balduzzi/DeepMind, Freitag/WMT23, Llama 2, Terence Tao | Tao verified via the book's own oreil.ly link → Mathstodon ActivityPub |
| 4 | TechRadar/Samsung, CIO Dive/Zoom, a16z, Chen et al., DeBERTa card | TechRadar flagged member-wall; StarCoder 8% and HELM $80k–$100k kept book-attributed/derived |
| 5 | GoDaddy, HELM, DSPy, Promptbreeder | B5 disclosed (book's 7 best-practices grouped into 4 habits); dropped 2 orphan refs; Microsoft-2023 kept book-attributed |
| 6 | BM25/Robertson, FAISS, CLIP | +new "RAG beyond text" card (text-to-SQL/CLIP); wired orphan ref-11 |
| 7 | Apple on-device, InstructGPT, Garimella, Code Llama | +bias-mitigation & long-context deep blocks; wired orphan ref-2/ref-3; Character.AI INT8 kept book-attributed (source removed line) |
| 8 | Peng (GPT-4 instruct), Sorscher, Kern | re-verified ref-15 arXiv id (2212.09251, once wrong); +data-centric framing; Databricks/LinkedIn kept book-attributed |
| 9 | NVIDIA H100, EIA | +Table 9-2 (FLOP/s by precision) +Kernels/compilers section; EIA 10,791 kWh vs book's rounded 10,000 noted in place |
| 10 | TechRadar/Samsung, Voiceflow, Business Insider/Uber, NPR/X, MDPI/Stray | wired orphan ref-2/ref-3; BI (Uber) and MDPI (Stray) bot-blocked → `<em>`-flagged; Liu 2020 paywalled → book-attributed |

**Auditor's independent sweep:** 12/12 `book-qa` PASS (cross-chapter templates — a chapter is
never its own template, which is what produced the false ch9 "PROBLEMS" earlier); zero dead
`.html` links, zero dangling `#anchor`s, zero broken cites, zero newly-orphaned refs. 27
specifics spot-checked across the nine chapters (14 arXiv title/author matches, 13 non-arXiv
content/reachability checks including the bot-blocked ones); zero invented or mis-cited
specifics. The bot-blocked refs carry honest `<em>` host/code notes and are not treated as
independently verified; MDPI/Stray's title+author were additionally confirmed via Crossref
despite the 403.

**Still carried book-attributed (no live third-party source found, kept on ref-1 rather than a
borrowed cite):** SemiAnalysis data-center power and LinkedIn YAML (ch2), Microsoft-2023 few-shot
(ch5), Character.AI INT8 (ch7), Databricks 20/60% and LinkedIn annotation (ch8), Liu 2020 (ch10).
These are the book's own reported figures, flagged here rather than silently treated as
externally verified.
