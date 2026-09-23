# COMPLETION — How Linux Works (bilingual VI/EN companion)

**Site:** `/Users/thanhhaikhong/Documents/research/how-linux-works/`
**Book:** Brian Ward, *How Linux Works: What Every Superuser Should Know*, 3rd ed.,
No Starch Press, 2021 (ISBN 978-1-7185-0040-2)
**Audited:** 2026-09-22 · read-only verification by `book-fidelity-auditor`
**QA helper:** `book-qa` (shared gate, on `$PATH`)

## Verdict

# ✅ PASS (qualified)

All 18 content pages pass the shared `book-qa` gate. **0 dead local links,
0 dangling anchors, 0 unresolved cites** across **4,803 citations / 440
references**; every reference entry carries a live external link; bilingual
layers complete and 100% `lang`-tagged; scaffold and page ranges uniform and
correct. The faithfulness spot-check surfaced **nothing unsourced, mis-cited or
contradicted**.

Qualified by five findings (below). None blocks.

## Site

| | |
|---|---|
| Pages | `index.html` + 17 chapter pages |
| Total size | ~3 MB |
| Citations | 4,803 inline, resolving to 440 references |
| Reading modes | Dễ hiểu · Chuẩn · Đầy đủ |
| Languages | VI · EN (every `en-only` element `lang`-tagged) |
| Runtime deps | none — no CDN, no webfont, nothing fetched at runtime |

## Per-page results

| Page | book-qa | Pages | Cites/Refs | Faithfulness sample |
|---|---|---|---|---|
| `index.html` | ✅ | — | 2 refs | `OL29462444M` verified = correct book; 17/17 cover cards resolve |
| ch1 · The Big Picture | ✅ | 1–10 | 134 / 11 | "most of the real action … happens in user space" verbatim |
| ch2 · Basic Commands | ✅ | 11–46 | 262 / 22 | "preliminary material … flip through" verbatim |
| ch3 · Devices | ✅ | 47–67 | 392 / 26 | "a very simplistic scheme" verbatim |
| ch4 · Disks and Filesystems | ✅ | 69–115 | 279 / 36 | block sizes 1024/4096/8192 all in slice |
| ch5 · Kernel Boots | ✅ | 117–135 | 216 / 18 | MBR 441-vs-440/446 drift quarantined in aside; Ward's 441 kept in body |
| ch6 · User Space Starts | ✅ | 137–165 | 329 / 24 | "standard implementation of init is systemd" verbatim |
| ch7 · System Configuration | ✅ | 167–198 | 450 / 29 | "Usernames exist only in user space" verbatim |
| ch8 · Processes and Resources | ✅ | 199–222 | 312 / 24 | vmstat 320,416KB / 3,027,000KB match p. 212 exactly |
| ch9 · Network Configuration | ✅ | 223–268 | 402 / 37 | IPv6 "32 bytes" book error quarantined; RFC 4291 fetched and confirms 128-bit / eight 16-bit groups |
| ch10 · Network Applications | ✅ | 269–290 | 301 / 38 | `sshd_config(5)` + OpenSSH release notes fetched; PermitRootLogin and DSA-removal drifts marked beyond Ward; `OL9290835M` = correct Stevens vol. 1 3rd ed. |
| ch11 · Shell Scripts | ✅ | 291–313 | 277 / 16 | `test(1)` `-a`/`-o` cited to man page + POSIX, not to Ward |
| ch12 · File Transfer and Sharing | ✅ | 315–334 | 235 / 21 | kernel FUSE doc + `nmbd(8)` fetched, verbatim; bwlimit unit divergence flagged two-source |
| ch13 · User Environments | ✅ | 335–345 | 140 / 16 | `/etc/bash.bashrc` correctly identified as Debian-family patch, upstream bash doc cited against it |
| ch14 · Desktop and Printing | ✅ | 347–362 | 306 / 32 | GNOME 49 Xorg removal + CUPS driver deprecation both labelled beyond the 2021 text |
| ch15 · Development Tools | ✅ | 363–383 | 324 / 26 | further-reading list verbatim |
| ch16 · Compiling from C Source | ✅ | 385–400 | 215 / 24 | GNU claims verified from the autoconf-2.72 tarball (host-blocked): DESTDIR, install-strip, prefix default, VPATH, config.cache |
| ch17 · Virtualization | ✅ | 401–418 | 225 / 38 | Intel VT article fetched, verbatim; Podman `pasta`/`netavark` drift labelled "Ngoài bản văn"; `OL26472336W` = Smith & Nair, recommended by Ward |

## Navigation

Curator sweep: **17/17 neighbours resolve, 0 demoted, 0 edits.** Chain walked in
canonical 1→17 order — each `nav-prev`/`nav-next` points at the correct sibling,
across both NAV fences per page. Chapter 1's `nav-prev` and chapter 17's
`nav-next` are live `index.html` links (house convention at a series boundary).

## Findings that did not rise to FAIL

1. **Curator-region assertion NOT RUN.** The directory is not a git repository,
   so no baseline diff exists. The *outcome* of nav integration was verified;
   its *provenance* was not — it cannot be confirmed that edits stayed inside
   `NAV:START…NAV:END`. Treat as unverified, not passed. Fix for a next wave:
   `git init` and commit the authoring output before the curator runs.

2. **6 of 11 `www.gnu.org` citations are content-unverified.** The host is
   blocked at sandbox level (`gcc.gnu.org` and `ftp.gnu.org` return 200 from the
   same shell; `www.gnu.org/` root times out; WebFetch and `web.archive.org`
   also unavailable). Five were verified by downloading `autoconf-2.72.tar.gz`
   from `ftp.gnu.org` and reading the shipped manuals — all verbatim. The
   remaining six are canonical, well-formed GNU URLs on an unreachable host,
   assessed as live-but-unread rather than dead.

3. **`nostarch.com/howlinuxworks3` (403) never independently content-confirmed.**
   Cited once as `index.html#ref-2`, a publisher resource link rather than claim
   support. Bot-blocked to both curl and WebFetch.

4. **One orphan reference:** `index.html#ref-2` is listed but never cited
   inline — the site's only reference with no inbound cite. A resource pointer,
   not an unsupported claim.

5. **Faithfulness is a spot-check, not exhaustive.** Sample: 412
   author-attributed sentences (252 attribution-bearing blocks re-checked at
   block level), 127 English quoted phrases, 45 numeric specifics, 12 claims
   traced line-by-line to `src/chapters/*.txt`, 7 external sources fetched and
   read for *support* rather than existence, and all 6 OpenLibrary IDs resolved
   via API. Meaningful against ~4,800 cites, not a full pass over them.

**Recorded non-findings:** the 3 attribution-bearing blocks lacking a cite
(ch14 ×1, ch15 ×2) are all self-check questions inside `question-list`, which
owe no citation. There is **no survivor of the wrong-book citation class** — all
6 OpenLibrary IDs resolve to the correct titles and editions.
