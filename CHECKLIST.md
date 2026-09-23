# Checklist — tiêu chí viết một trang sách trên kệ

Nguồn chân lý **duy nhất** cho tiêu chí, dùng chung cho **mọi cuốn** trên kệ. Trạng
thái hoàn tất của từng cuốn nằm ở `<category>/<book-slug>/COMPLETION-<book-slug>.md`.

Giữ file này thuần là *tiêu chí*. Không chép nó vào từng thư mục sách — bản sao sẽ
trôi lệch nhau, đúng như 1.8 MB CSS inline đang trôi.

`book-chapter-author` phản chiếu **Phần I** và in lại nó (đã tick + một dòng bằng
chứng mỗi mục) ở cuối báo cáo mỗi trang.

> **Nguyên tắc trên hết: không bịa — không có tham chiếu thì không cho vào trang.**

---

## Phần 0 — Bố cục kệ

```
bookshelf/
├── index.html              # KỆ: card mỗi cuốn, trong fence BOOKS
├── CHECKLIST.md            # file này
├── <category>/             # thư mục gom nhóm thuần, KHÔNG có index.html
│   └── <book-slug>/        # một cuốn = một site tự chứa, PHẲNG
│       ├── index.html
│       ├── chapter-1-….html …
│       ├── mind-map.html
│       ├── COMPLETION-<book-slug>.md
│       └── src/            # sách gốc — GITIGNORED
```

- **Trang của một cuốn luôn phẳng.** `book-qa` lấy project root = thư mục của chính
  trang đó. Đưa chương vào thư mục con là gãy cổng kiểm.
- **Href nội bộ trong một cuốn là tên file trần.** Href nhiều đoạn chỉ tồn tại ở card
  của kệ.
- Truyền cho agent **đường dẫn tuyệt đối của thư mục cuốn**, không phải gốc kệ.

---

## Phần I — Tiêu chí cho MỘT trang

### A. Hiểu nội dung (research)
- [ ] **A1** · Xác định đúng **thesis** (một câu).
- [ ] **A2** · Rút **2–3 cụm khái niệm** cốt lõi + **ví dụ tác giả thực dùng** + **ngộ nhận** người mới hay mắc.
- [ ] **A3** · Lập bảng **claim → nguồn**: mọi số liệu / trích / ví dụ-gán-tác-giả ghép với một nguồn công khai; **ưu tiên sơ cấp (sách)**, thứ cấp chỉ để đối chiếu.
- [ ] **A4** · Chi tiết **không truy được nguồn → KHÔNG lên trang** (bỏ, hoặc hạ thành diễn giải chung).

### B. Trung thực & trích dẫn — "không bịa"
- [ ] **B1** · Nội dung phản ánh đúng sách; không bịa số liệu / trích / ví dụ.
- [ ] **B2** · Mỗi specific mang **cite `[N]`** trỏ tới mục `ref-list` có `id`; mỗi mục ref-list có link ngoài **thật, đã tự fetch**.
- [ ] **B3** · Nguồn bất đồng → **theo sách ở thân** + ghi chú ở `deep-only`, không âm thầm chọn một phía.
- [ ] **B4** · Footer nêu **nguồn chính (sách)** + disclaimer "bản đọc-cùng, không phải bản dịch" + ghi chú ví dụ "Dễ hiểu" là minh hoạ thêm.
- [ ] **B5** · **Mọi cách sắp xếp do trang tự nghĩ ra phải được công bố là của trang.** Gom chương thành "mạch"/"phần" mà tác giả không đặt → nói rõ ở footer, nếu không một diễn giải sẽ bị đọc thành lời tác giả.
- [ ] **B6** · **Số liệu có hạn sử dụng phải gắn mốc thời gian.** Phiên bản phần mềm, "hiện nay", danh sách maintainer… → viết "tại thời điểm viết trang này" + ngày truy cập trong mục ref. Không nói trơn như chân lý vĩnh viễn.
- [ ] **B7** · **Ngày truy cập cho mọi nguồn sống.** Nguồn định nghĩa/ổn định thì tuỳ, nhưng đồng đều vẫn hơn.

### C. Song ngữ & 3 chế độ đọc
- [ ] **C1** · Mỗi đơn vị prose đủ **4 lớp**: `standard-copy` / `easy-only` (kết bằng "Nhớ nhé: …") / `en-only lang="en"` / (`deep-only` tuỳ chọn).
- [ ] **C2** · Mọi `en-only` mang `lang="en"`; nhãn ngắn dùng `vi-only`+`en-only`; thuật ngữ Anh trong câu Việt bọc `<span lang="en">`.
- [ ] **C3** · Lớp `deep-only` đủ dày (≥ 3 khối) với kind dày.
- [ ] **C4** · VI/EN toggle + 3 mức đọc + dark mode chạy đúng; **localStorage keys giữ nguyên tiền tố của cuốn** (`flow-`, `hlw-`, `ddia-`…). Key là origin-scoped, đổi là mất trạng thái đọc của người dùng.

### D. Scaffold & cấu trúc
- [ ] **D1** · Chép **nguyên văn** `<head>` + toàn bộ `<style>` + `.topbar` + cả 2 `<script>`; chỉ đổi `<title>` / `<meta description>` / `.book-label` / hero `.eyebrow` / `.hero::after`.
- [ ] **D2** · Mỗi `<section>` có **`id` riêng khớp anchor**; không sót `id` của template.
- [ ] **D3** · `chapter-nav` prev/next + footer cross-link theo roster; chương cuối tự disable `nav-next`; **chỉ ghi đúng một file**.
- [ ] **D4** · Diagnostic auto-number bằng **CSS counter**, không đánh số tay.
- [ ] **D5** · **Section-index rail** có mặt: khối `/* SECTION-RAIL:START */…END */` **và** IIFE dựng `.section-rail__list`, chép nguyên văn. Không áp dụng cho kind `map`/`shelf`.
- [ ] **D6** · **Không thêm phụ thuộc runtime mới.** Cuốn nào tự cam kết "no CDN / no webfont" thì tuyệt đối không phá — kiểm cả `@import`, `url()` trỏ ra ngoài, iframe, `fetch(`/`XHR`, không chỉ tên miền CDN.
- [ ] **D7** · **Không thêm biến CSS mới, không màu cứng.** Cần màu nhấn → ánh xạ sang token accent **sẵn có** của chính cuốn đó. Kiểm nền mới **khác** nền body ở **cả hai theme**, nếu không component sẽ tàng hình mà cổng kiểm không bắt được.

### E. Cổng QA
- [ ] **E1** · **Faithfulness self-audit** trước QA: quét mọi specific → xác nhận có `[N]` resolve; sửa/bỏ cái trượt.
- [ ] **E2** · `book-qa <file> <template>` → **`ALL CHECKS PASS`**.
- [ ] **E3** · Mọi ref được cite ít nhất một lần (**không ref mồ côi**) và mọi cite trỏ tới ref có thật (**không cite gãy**). `book-qa` **không** bắt ref mồ côi — phải tự đếm.

> Cổng E là spec của `book-fidelity-auditor` khi quét toàn site. `COMPLETION ✅` chỉ
> hợp lệ khi auditor trả PASS.

---

## Phần II — Tích hợp (spec của `book-cover-curator`, chạy tuần tự sau wave authoring)

- [ ] **S1** · Promote `nav-next` / footer đang "sắp có" khi hàng xóm đã tồn tại trên đĩa.
- [ ] **S2** · Integrity chéo: mọi link giữa các trang resolve trên đĩa.
- [ ] **S3** · Cover: lật card chương thành link sống; cập nhật dòng result + intro; gắn `.mindmap-banner` khi có `mind-map.html`.
- [ ] **S4** · **Card của cuốn trên kệ**: nếu thư mục cha có `index.html` chứa `<!-- BOOKS:START -->`, đảm bảo cuốn này có fence `<!-- BOOK:<slug>:START … END -->`. Chỉ sửa fence của chính mình.
- [ ] **S5** · QA sweep lại mọi trang vừa đổi.
- [ ] **S6** · `git diff --stat -- .` — **phải scope `-- .`**. Trong repo chung nhiều cuốn, lệnh trần báo cả repo và sửa song song ở cuốn khác sẽ hiện thành "rò rỉ" giả.

---

## Phần III — Lệnh kiểm

```bash
book-qa chapter-N-….html <chương-đầy-đủ-nhất>.html --kind chapter
book-qa mind-map.html          # auto-detect: map
book-qa index.html             # auto-detect: cover (hoặc shelf nếu có BOOKS sentinel)
```

| kind | Dùng cho | Khác biệt |
|---|---|---|
| `chapter` | `chapter-N-*.html` | Đủ bộ check |
| `part-group` | trang Phần (sách chia phần, không chia chương) | Như chapter nhưng bỏ check số-chương và nav-model |
| `synthesis` | `glossary*` | Bỏ check số chương; giữ song ngữ + ref-list |
| `map` | `mind-map*` | Canvas tương tác: bỏ lớp prose, ref-list, section-rail. `href="#"` là placeholder JS, không tính là anchor gãy |
| `cover` | `index.html` của một cuốn | Chỉ well-formed + anchor + song ngữ |
| `shelf` | `index.html` có `<!-- BOOKS:START -->` | Kiểm khối BOOKS **hai chiều**: sách trên đĩa mà thiếu card → fail; card trỏ sách đã xoá → fail |

> **Giới hạn của `book-qa`:** nó chỉ ép **proxy cấu trúc**. Nó **không** xác minh
> "mọi khẳng định đều đúng sách & có nguồn", **không** bắt ref mồ côi, **không** kiểm
> màu, và **không** kiểm anchor trỏ sang trang khác. Những phần đó nằm ở kỷ luật
> A3/A4/B1–B7 và ở `book-fidelity-auditor`.

---

## Phần IV — Bẫy đã mắc phải (đọc trước khi lặp lại)

Bốn lỗi thật, đã xảy ra trên kệ này:

1. **Đổi tên file mà chỉ sửa `href="..."`.** Mind-map dựng link trong **JS** từ hằng
   số tên file → 42 link chết lúc chạy, trong khi bộ quét chỉ đọc `href=` báo "0 gãy".
   → Quét link phải bắt **mọi chuỗi `"*.html"`**, kể cả trong `<script>`.

2. **Đổi `id` của một section mà không tra ai đang trỏ tới.** `book-qa` chỉ kiểm anchor
   **trong cùng trang**, nên 5 link chéo gãy im lặng.
   → Đổi `id` thì grep toàn cuốn tìm `#<id-cũ>` trước.

3. **Kiểm dải trang bằng cách đọc trang đầu/cuối rồi suy ra.** Không thấy ranh giới
   chương ở giữa → quy nhầm 5 trang cho sai chương, mà vẫn ghi "đã kiểm chứng".
   → Đọc **running head từng trang**, đừng nội suy.

4. **Đọc file khi agent đang ghi dở rồi kết luận về sản phẩm cuối.**
   → Chỉ đo sau khi agent báo xong; số liệu nhảy bậc thang là dấu hiệu đang ghi.

Và một quy ước: **link 403/405 vì chặn bot** thì giữ, kèm `<em>` **ngoài** thẻ `<a>`
ghi rõ host nào chặn và mã trả về — để người verify phân biệt được với link chết. Kiểm
bằng UA trình duyệt thật + `host` trước khi kết luận là chặn bot.
