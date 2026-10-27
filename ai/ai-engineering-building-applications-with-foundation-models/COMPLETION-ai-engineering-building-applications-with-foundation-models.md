# COMPLETION · AI Engineering: Building Applications with Foundation Models

Bilingual VI/EN book-companion site · 12 pages · audited by `book-fidelity-auditor`

**Source book:** Chip Huyen, *AI Engineering: Building Applications with Foundation Models*,
O'Reilly Media, 1st edition, December 2024 (ISBN 9781098166304).

**Verdict: PASS** — with the caveats recorded below. Chapter 1 was re-audited on
2026-10-27 after a citation rework; still PASS. See "Chapter 1 citation re-audit" at the end.

## Per-page results

| Page | book-qa | Layer balance | Cites / refs | Nav |
|---|---|---|---|---|
| `index.html` | PASS (cover) | 35 + 20 = 55 ✓ | 1 / 3 | 11 outbound, all resolve |
| `mind-map.html` | PASS (synthesis) | 66 + 55 = 121 ✓ | 24 / 3 | 11 outbound, all resolve |
| `chapter-1-introduction-to-building-ai-applications-with-foundation-models.html` | PASS | 103 + 41 = 144 ✓ | 24 / 26 | index → ch2 |
| `chapter-2-understanding-foundation-models.html` | PASS | 88 + 79 = 167 ✓ | 16 / 18 | ch1 → ch3 |
| `chapter-3-evaluation-methodology.html` | PASS | 110 + 33 = 143 ✓ | 13 / 13 | ch2 → ch4 |
| `chapter-4-evaluate-ai-systems.html` | PASS | 95 + 38 = 133 ✓ | 18 / 20 | ch3 → ch5 |
| `chapter-5-prompt-engineering.html` | PASS | 95 + 34 = 129 ✓ | 11 / 13 | ch4 → ch6 |
| `chapter-6-rag-and-agents.html` | PASS | 88 + 36 = 124 ✓ | 10 / 11 | ch5 → ch7 |
| `chapter-7-finetuning.html` | PASS | 96 + 32 = 128 ✓ | 14 / 16 | ch6 → ch8 |
| `chapter-8-dataset-engineering.html` | PASS | 85 + 38 = 123 ✓ | 16 / 18 | ch7 → ch9 |
| `chapter-9-inference-optimization.html` | PASS | 121 + 32 = 153 ✓ | 24 / 24 | ch8 → ch10 |
| `chapter-10-ai-engineering-architecture-and-user-feedback.html` | PASS | 83 + 52 = 135 ✓ | 6 / 8 | ch9 → end of series |

Layer balance is the identity `standard-copy + vi-only == en-only`. It holds exactly on all
twelve pages. Every `en-only` element carries `lang="en"` — zero violations site-wide. The
per-chapter gap between `standard-copy` and `easy-only` is accounted for by `deep-only`
containers, which have no easy-mode twin by design.

## Site level

- **book-qa:** 12 / 12 PASS.
- **Links:** 51 internal `.html` hrefs, every target present on disk. Zero dead local links.
- **Anchors:** zero dangling `#id` across all twelve pages.
- **Citations:** every inline `<span class="cite"><a href="#ref-N">` resolves to an
  `<li id="ref-N">` carrying an external `https://` link. 18 uncited ref entries (the author's
  page, the `aie-book` repo) are further-reading by design.
- **arXiv verification:** 105 arXiv refs site-wide. Verified by fetching
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
