# COMPLETION — Linux Kernel in a Nutshell (bilingual VI/EN companion)

**Verdict: PASS** — issued by `book-fidelity-auditor` (read-only), 2026-09-22.
Gate: `book-qa` at `/Users/thanhhaikhong/.config/bin/book-qa`.
Source: Greg Kroah-Hartman, *Linux Kernel in a Nutshell*, O'Reilly, 2006 (kernel 2.6 era).
Free edition: <http://www.kroah.com/lkn/> (CC BY-SA 2.5).

## Site

12 pages · ~1.45 MB · `index.html` + `chapter-1` … `chapter-11`.
Part I (ch 1–6) Building the Kernel · Part II (ch 7–8) Major Customizations ·
Part III (ch 9–11) Kernel Reference · Part IV (Appendices A & B) deliberately NOT
authored, shown on the cover as "sắp có".

| Page | book-qa | cites→refs | Faithfulness spot-check |
|---|---|---|---|
| `index.html` | PASS (cover) | 0→0 | 11 cards live; Part IV "sắp có" matches disk |
| ch1 Introduction | PASS | 113→11 | "secret goal" quote verified in PDF p. ix |
| ch2 Requirements | PASS | 228→9 | all 13 minimum tool versions match the book verbatim |
| ch3 Retrieving Source | PASS | 141→10 | "Do NOT use the /usr/src/linux area!" verbatim, attributed to docs not the book |
| ch4 Configuring & Building | PASS | 203→13 | "almost two thousand different configuration options" verbatim (book p. 17) |
| ch5 Installing & Booting | PASS | 190→15 | book's own `include/linux/autoconf.h` reported; two unsourceable claims correctly dropped |
| ch6 Upgrading | PASS | 200→14 | commit `911a91c39cab` verbatim; lftp 2872/7901 bytes match PDF |
| ch7 Customizing | PASS | 214→17 | `make localmodconfig` explicitly marked NOT Kroah-Hartman's |
| ch8 Config Recipes | PASS | 342→26 | 4 LKDDB symbol lifetimes spot-checked, all exact |
| ch9 Boot Parameters | PASS | 529→23 | `ref-17` dated baseline independently confirmed (7.3.0-rc4) |
| ch10 Build Commands | PASS | 249→17 | all 4 book-error claims confirmed against the PDF |
| ch11 Config Options | PASS | 274→24 | LWN 32,468 / 6.16 / 2025-09-10 all verbatim; `SCSI_SATA` claim holds |

## Site-level

- **12/12 pass `book-qa`.**
- **2,683 cites → 179 refs · zero dangling · zero unused.** 179/179 refs carry a
  resolving external link (ch9 refs 2–16 are explicit `Sđd.` ibids of the linked ref-1).
- Zero dead internal links; zero dangling in-page anchors.
- Zero `en-only` elements missing `lang="en"` across all 12 pages.
- Bilingual `standard-copy`/`easy-only` layers balanced on every page.

## ch9 absence / rename audit (live fetch, 2026-09-22)

docs.kernel.org independently reports **7.3.0-rc4**, matching `ref-17` exactly.
Confirmed ABSENT: `notsc`, `kstack`, `elevator`, `acpi_serialize`, `selinux_compat_net`.
Confirmed RENAMED: `rcutree.blimit`, `scsi_mod.max_luns`, `usbcore.nousb`.
Also confirmed: `selinux=` now defaults to 1 (a genuine flip from book p. 110,
correctly reported); control files moved to `/sys/fs/selinux/`.

## Caveats attached to the PASS (not blocking)

1. **Curator-region assertion: NOT RUN.** The directory is not a git repository, so
   there is no baseline to diff nav integration against. The auditor could not certify
   that curator edits stayed inside the NAV fences. Chapter mtimes all predate
   `index.html`, which is circumstantial evidence only — not a diff.
2. **Faithfulness is a spot-check, not exhaustive.** ~120 specifics sampled across 12
   pages; **31 confirmed by fetching the external source or extracting the source PDF**
   rather than trusting the page's own ref text. A mechanical sweep for present-tense
   currency claims cited only to the 2006 book surfaced 18 candidates — all 18 resolved
   as heuristic false positives.
3. **ch10 `ref-17`** attributes the namespace.pl patch to Jacob Keller (correct), but the
   URL lands on Masahiro Yamada's reply quoting it in full. The 11122 figure is accurate
   either way. Cosmetic.

## Methodological caution (both errors occurred within this one audit)

A mechanical match treated as evidence without reading its surroundings failed in
**both directions** here:

- **False positive avoided:** a naive substring grep hits `notsc` inside
  `notscdeadline` and `kstack` inside `randomize_kstack_offset`, and would have
  wrongly contradicted a correct page. Context showed the page right.
- **False negative created:** a bare-class regex found no rule for `nav-prev` /
  `surprise-connection` and was read as "unstyled". The styling lives on the companion
  class (`.nav-cell`, `.signal`); these are intentionally unstyled marker classes.
  The team lead compounded this by recording an invented rationale ("styled via
  compound selectors") in the audit brief as verified fact. The auditor overturned it.
- Same shape in `.easy-only` checking: a naive 400-character lookback wrongly flags 5
  blocks; a proper enclosure walk puts **41/41 inside `.equation`**, as designed.

## Known-and-justified, independently confirmed by the auditor

- **Section folding is presentational only** — ch9 carries all 22 `Nhóm N` labels;
  every ch8 (7) and ch10 (9) group name appears in the body. Coverage complete.
- **Repeated section ids across pages** — zero intra-page duplicates; 10 cross-page
  repeats, all harmless since anchors resolve within their own page.
- **`.easy-only` without the "Nhớ nhé:" closer** — 41 blocks, 41/41 inside `.equation`.
- **ch9 link ratio** — 8 linked refs + 15 explicit `Sđd.` ibids; zero refs that are neither.

## Faithfulness highlights ("không bịa")

- **Book errors caught and cited AS the book's own** — ch9 `lpg=n` (for `lpj`) and
  `rhash_entries` printing its format as `dhash_entries=n`; ch10 a duplicated row in
  Table 10-4, `arch/i396` in Table 10-8, and `INSTALL_MODULE_PATH` vs `INSTALL_MOD_PATH`.
  The `dhash_entries` case is load-bearing: it is a real, still-existing parameter for a
  different cache, so copying it verbatim yields silence rather than an error.
- **Claims dropped as unsourceable** — ch5 dropped `include/generated/autoconf.h` and
  "systemd-boot"; ch10 presented the `tags`/`TAGS` distinction as "what the book does
  not say"; ch7 marked `make localmodconfig` as not the author's.
- **Time-bound facts dated, not modernised** — GRUB Legacy named as such alongside
  GRUB 2; ketchup stated unmaintained with dated evidence; ten `CONFIG_*` symbol
  histories cited individually; `SCSI_SATA` noted as gone before the book shipped.
