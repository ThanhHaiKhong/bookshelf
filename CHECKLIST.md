# Checklist — đọc & viết một chương (bộ Flow)

Nguồn chân lý cho **tiêu chí** (Phần I–III). Báo cáo trạng thái hoàn tất của bộ nằm ở file riêng **[`COMPLETION-flow.md`](COMPLETION-flow.md)**. Agent `book-chapter-author` phản chiếu **Phần I** và phải in lại nó (đã tick + một dòng bằng chứng mỗi mục) ở cuối mỗi chương. Chép các ô `- [ ]` xuống khi bắt tay một chương mới, tick dần, và dán bản đã tick vào báo cáo khi xong.

Nguyên tắc trên hết của người dùng: **không bịa — không có tham chiếu thì không cho vào trang.**

---

## Phần I — Tiêu chí cho MỘT chương (agent thực hiện + tự kiểm)

### A. Hiểu chương (research)
- [ ] **A1** · Xác định đúng **thesis** của chương (một câu).
- [ ] **A2** · Rút **2–3 cụm khái niệm** cốt lõi + **ví dụ tác giả thực dùng** + **ngộ nhận** người mới hay mắc.
- [ ] **A3** · Lập bảng **claim → nguồn**: mọi số liệu / trích / ví dụ-gán-tác-giả ghép với một nguồn công khai; **ưu tiên sơ cấp (sách)**, thứ cấp chỉ để đối chiếu.
- [ ] **A4** · Chi tiết **không truy được nguồn → KHÔNG lên trang** (bỏ, hoặc hạ thành diễn giải chung).

### B. Trung thực & trích dẫn — "không bịa"
- [ ] **B1** · Nội dung phản ánh đúng sách; không bịa số liệu / trích / ví dụ.
- [ ] **B2** · Mỗi specific mang **cite nội tuyến `[N]`** trỏ tới mục `ref-list` có `id`; ref-list có ≥1 link ngoài.
- [ ] **B3** · Nguồn bất đồng về con số (vd 8-vs-9 thành tố) → **theo sách ở thân** + ghi chú ở `deep-only`, không âm thầm chọn một phía.
- [ ] **B4** · Footer nêu **nguồn chính (sách)** + disclaimer "đây là bản đọc-cùng, không phải bản dịch" + ghi chú ví dụ "Dễ hiểu" là minh hoạ thêm.

### C. Song ngữ & 3 chế độ đọc
- [ ] **C1** · Mỗi đơn vị prose đủ **4 lớp**: `standard-copy` / `easy-only` (kết bằng "Nhớ nhé: …") / `en-only lang="en"` / (`deep-only` tuỳ chọn).
- [ ] **C2** · Mọi `en-only` mang `lang="en"`; nhãn ngắn dùng `vi-only`+`en-only`; thuật ngữ Anh trong câu Việt bọc `<span lang="en">`.
- [ ] **C3** · Lớp `deep-only` đủ dày (≥ 3 khối).
- [ ] **C4** · VI/EN toggle + 3 mức đọc (Dễ hiểu / Tóm tắt / Đầy đủ) + dark mode chạy đúng; localStorage keys khớp template (`flow-reading-mode`, `flow-lang`).

### D. Scaffold & cấu trúc
- [ ] **D1** · Chép **nguyên văn** `<head>` + toàn bộ `<style>` + `.topbar` + cả 2 `<script>`; chỉ đổi `<title>` / `<meta description>` / `.book-label` / hero `.eyebrow` / `.hero::after` = `"FLOW / 0N"`.
- [ ] **D2** · Mỗi `<section>` có **`id` riêng khớp anchor** trong `chapter-path`; **không sót `id` template** (pleasure / components / autotelic …).
- [ ] **D3** · `chapter-nav` prev/next + footer cross-link theo roster; **chương cuối tự disable `nav-next`**; **chỉ ghi đúng 1 file**, không đụng cover/chương khác.
- [ ] **D4** · Diagnostic auto-number bằng **CSS counter** — không đánh số tay.
- [ ] **D5** · **Section-index rail** (thanh mục lục cuộn theo, ghim mép trái) có mặt: khối CSS `/* SECTION-RAIL:START */…END */` **và** IIFE dựng `.section-rail__list` chép **nguyên văn**; mỗi `<section>` giữ `id` riêng + heading có tiêu đề để rail không trỏ hụt.

### E. Cổng QA khách quan
- [ ] **E1** · **Faithfulness self-audit** trước QA: quét mọi số/trích/ví dụ-gán-tác-giả → xác nhận có `[N]` resolve về ref-list; sửa/bỏ cái nào trượt.
- [ ] **E2** · `book-qa <file> <template> --kind chapter` → **`ALL CHECKS PASS`** (xem Phần III).

> Cổng E (E1–E2) giờ là **spec của `book-fidelity-auditor`** khi quét toàn site — read-only, chạy `book-qa` cho mọi trang rồi gác "không bịa"; `COMPLETION-flow.md ✅` chỉ hợp lệ khi auditor trả PASS.

---

## Phần II — Tích hợp toàn site (spec của `book-cover-curator`, chạy tuần tự sau wave authoring)
- [ ] **S1** · Promote các ô `nav-next` / footer đang "sắp có" khi chương hàng xóm đã tồn tại trên đĩa.
- [ ] **S2** · Integrity chéo: mọi link `chapter-*.html` giữa các trang resolve trên đĩa; không lồng `<a>`.
- [ ] **S3** · Cover `index.html`: lật card chương thành link sống (`mark live`); cập nhật dòng "result" + đoạn intro.
- [ ] **S4** · QA sweep lại toàn bộ chương vừa đổi → tất cả `ALL CHECKS PASS`.

---

## Phần III — Cách kiểm & lệnh tham chiếu

QA là **một helper dùng chung trên `$PATH`** — `book-qa` (deploy từ `nix-config` cạnh các wrapper Swift). Không còn trích block Python từ agent ra file tạm; cả ba agent `book-*` đều gọi cùng một binary này (không nhúng bản sao).

```bash
# một chương (template = chương đầy đủ nhất, thường Ch3)
book-qa chapter-N-...html chapter-3-enjoyment-and-the-quality-of-life.html --kind chapter

# trang tổng hợp (mind-map / glossary) — auto-detect kind theo tên file nếu bỏ cờ
book-qa mind-map.html --kind synthesis

# cover
book-qa index.html --kind cover
```

**Cờ `--kind`** (auto-detect theo tên file khi bỏ trống: `chapter-N-*`→chapter, `index.html`→cover, `mind-map*`/`glossary*`→synthesis, còn lại→part-group):

| kind | Dùng cho | Khác biệt |
|---|---|---|
| `chapter` | `chapter-N-*.html` | Đủ bộ check (hành vi cũ, không hồi quy) |
| `synthesis` | `mind-map.html`, `glossary.html` | Bỏ check số-chương-từ-tên-file + check nav-model; giữ well-formed/anchor/cite/song ngữ/ref-list; "không bịa" hiểu theo *no-new-figures* |
| `part-group` | trang Part (bộ khác, vd thinking-in-system) | Như synthesis nhưng giữ đủ tầng faithfulness (trang Part dày specifics) |
| `cover` | `index.html` | Chỉ well-formed + anchor + song ngữ; không ép nav/ref-list |

**Các kiểm tra tự động** (chạy có điều kiện theo `--kind`) — phải sạch mới in `ALL CHECKS PASS`:

1. HTML well-formed: không lỗi lồng thẻ (mọi kind).
2. Không thẻ hở tại EOF (mọi kind).
3. Mọi anchor `href="#…"` (gồm cả `chapter-path` **và** cite `#ref-N`) có `id` khớp → đây cũng là check **cite → ref** (mọi kind).
4. Mọi `en-only` có `lang="en"` (mọi kind).
5–7. Đếm `standard-copy` / `easy-only` / `en-only` — lớp song ngữ không được mỏng (mọi kind).
8. Đúng **một** khối `chapter-nav`, có đủ cell `nav-prev` **và** `nav-next` (chỉ `chapter`).
9. localStorage keys khớp template (chỉ khi truyền template).
10. `<title>` của template **không** còn sót (chỉ khi truyền template).
11. Link file nội bộ resolve trên đĩa — **trừ** link `*.html` giữa các trang (integrity chéo là việc của curator/auditor).
12. Số chương nhất quán: `N` suy từ tên file khớp đuôi `.hero::after` (`FLOW / 0N`) + `.book-label` (chỉ `chapter`).
13. `deep-only` xuất hiện ≥ 3 (chỉ `chapter` + `part-group` — trang dày).
14. Có ≥ 1 link tham chiếu ngoài `<a href="https?://…">` (mọi kind trừ `cover`).
15. Có ≥ 1 mục ref-list `id="ref-N"` để cite phân giải (mọi kind trừ `cover`).

> Ghi chú giới hạn: `book-qa` chỉ ép **proxy cấu trúc**. Nó **không** tự xác minh ngữ nghĩa "mọi khẳng định đều đúng sách & có nguồn" — phần đó nằm ở kỷ luật A3/A4/B1–B4 + spot-check của `book-fidelity-auditor` (WebFetch claim đáng ngờ).

---

## Phần IV — Báo cáo hoàn tất

Trạng thái hoàn tất của bộ (mốc "tham chiếu khi hoàn tất") được tách ra file riêng: **[`COMPLETION-flow.md`](COMPLETION-flow.md)** — bảng 10/10 chương (QA · scaffold · faithfulness · nav), trạng thái site-level, caveat, và lệnh tái tạo. Giữ `CHECKLIST.md` này thuần là *tiêu chí* (Phần I–III); báo cáo trạng thái sống ở file completion.
