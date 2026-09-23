# COMPLETION — Thinking in Systems (bạn đồng hành song ngữ VI/EN)

**Site:** `bookshelf/mind/thinking-in-system/`
**Sách:** Donella H. Meadows, *Thinking in Systems: A Primer*, Chelsea Green Publishing, 2008
**Audit:** 2026-09-23 · kiểm read-only bởi `book-fidelity-auditor`
**Phạm vi PASS:** verdict được ra **trước** khi đổi đích link nguồn (xem *Nguồn* và *Ghi chú về trình tự*)
**QA helper:** `book-qa` (cổng dùng chung, trên `$PATH`)

## Verdict
# ✅ PASS

Đây là lần đầu cuốn này qua audit. Trước đó nó không có COMPLETION **vì chưa từng
đạt** — cả 5 trang fail `book-qa`, và không một khẳng định nào có nguồn.

## Site

| | |
|---|---|
| Trang | `index.html` (bìa) · 3 trang phần · `mind-map.html` |
| Cấu trúc | **ba PHẦN, không phải chương** — `part-group`, đúng với sách |
| Trích dẫn | 155 `[N]` inline → 18 mục ref-list, 0 mồ côi, 0 gãy |
| Chế độ đọc | Dễ hiểu · Chuẩn · Đầy đủ |
| Ngôn ngữ | VI · EN |
| localStorage | `systems-lang` · `systems-reading-mode` |

## Kết quả từng trang

| Trang | kind | book-qa | Link/anchor | Cites/refs | Ghi chú |
|---|---|---|---|---|---|
| `index.html` | cover | ✅ | ✅ | — | Khôi phục section-rail (2 hunk thuần thêm) |
| `part-1-system-structure-and-behavior.html` | part-group | ✅ | ✅ | 94 / 7 | Phần 1 — stock, flow, vòng phản hồi, trễ |
| `part-2-systems-and-us.html` | part-group | ✅ | ✅ | 18 / 6 | Phần 2 — bất ngờ, duy lý giới hạn, 8 bẫy hệ thống |
| `part-3-creating-change.html` | part-group | ✅ | ✅ | 43 / 5 | Phần 3 — 12 điểm đòn bẩy, 15 chỉ dẫn |
| `mind-map.html` | map | ✅ | ✅ | — | Bản đồ tương tác; 42 link dựng bằng JS |

## Đã sửa trong đợt này

1. **Đổi tên 3 trang phần** — tên cũ sắp sai thứ tự (Phần 1/2/3 ra alphabet 2/3/1).
   Giờ là `part-1-` / `part-2-` / `part-3-`. Cố ý **không** dùng `chapter-N`:
   Meadows có ba *phần*, không phải ba chương.
2. **Khôi phục section-index rail** trên bìa và cả ba trang phần, copy verbatim từ
   `mind/flow/chapter-5-the-body-in-flow.html` (cùng design system).
3. **Trích dẫn, từ con số 0** — mọi số liệu, trích dẫn trực tiếp và ví dụ đích danh
   Meadows giờ mang `[N]` resolve tới ref-list có link ngoài thật.
4. **Sửa link bản đồ** — mind-map dựng href trong JS từ ba hằng số vẫn giữ tên file
   **trước** khi đổi tên: 42 link chết lúc chạy. Kèm 5 link trỏ `#chapter-7` đã bị
   đổi thành `#living`. Bộ quét link chỉ đọc `href=` không thấy được lỗi này.

## Nguồn

Nguồn chính là **chính cuốn sách**, ghi đầy đủ thư mục (tác giả, nhan đề, NXB, năm,
tên chương). Link trỏ tới **Internet Archive — bản mượn có kiểm soát** (hợp pháp, ổn
định) và trang NXB Chelsea Green.

Trước đó 117/155 trích dẫn (75%) treo vào **một** bản PDF toàn văn trên server
`research.fit.edu` — vừa là vấn đề bản quyền khi trang công khai trỏ tới bản sao đầy
đủ của sách đang bán, vừa là điểm chết đơn lẻ. Đã thay toàn bộ.

### Ghi chú về trình tự — đọc kỹ chỗ này

Auditor chạy và ra verdict PASS **khi trang còn trỏ vào bản PDF `research.fit.edu`**.
Việc đổi đích link sang Internet Archive + Chelsea Green diễn ra **sau đó**, nên
auditor **chưa từng nhìn thấy** các link hiện có trên trang.

Điều này **không** làm PASS mất hiệu lực, vì thứ auditor kiểm là *nội dung*: nó mở
văn bản sách thật và đối chiếu từng khẳng định với đúng chương. Nội dung, số hiệu
`[N]`, và ánh xạ khẳng định → chương đều **không đổi** trong lần thay link; chỉ URL
đích đổi, và vẫn là cùng một cuốn sách.

Phần **chưa** qua mắt auditor và do main session tự kiểm:
- `archive.org/details/thinkinginsystem0000mead` → HTTP 200, xác nhận đúng cuốn
  (Meadows, Donella H.)
- `chelseagreen.com` → 403 + trang thử thách Cloudflare "Just a moment…" kể cả với
  UA trình duyệt thật; DNS phân giải bình thường → chặn bot, không phải link chết
- Toàn bộ link ngoài còn lại của cuốn → 200
- `book-qa` 5/5 PASS; 155 marker / 18 ref, 0 mồ côi, 0 gãy — sau khi thay link

Muốn PASS phủ luôn bộ link hiện tại thì cần một lượt audit nữa.

Nguồn bổ trợ: Hardin 1968 (*Science* 162, no. 3859: 1243–1248, qua math.uchicago.edu),
Stanford Encyclopedia of Philosophy (bounded rationality), hai bài luận gốc trên
donellameadows.org, trang NXB Chicago cho Kuhn.

Trích đoạn chương do Đại học Southampton host (Phần 2, ref-2/3/4) **cũng đã được
thay** bằng cùng bộ link bền. Số trang giữ nguyên vì đã **tự kiểm chứng** bằng
`pdftotext` trên chính ba file PDF đó trước khi bỏ link, đọc số trang in trên trang
đầu/cuối:

| Ref | Chương | Trang ghi | Kiểm chứng |
|---|---|---|---|
| 2 | 3 — Why Systems Work So Well | 75–90 | 17 trang PDF, trang cuối in số 91 → 75–91, trong đó tr. 91 là trang mở Chương 4 ⇒ **75–90 đúng** |
| 3 | 4 — Why Systems Surprise Us | 95–110 | trang đầu in 95, trang cuối in 110 ⇒ **đúng** |
| 4 | 5 — System Traps | 111–141 | 31 trang PDF, trang cuối in 141 ⇒ 141−31+1 = **111 đúng** |

Đáng ghi nhận: tên file PDF của Southampton **không khớp** số trang in (ví dụ file
`…-112-127.pdf` thực chất là tr. 95–110). Agent viết Phần 2 đã ghi đúng theo số
trang in chứ không theo tên file — kiểm lại thấy chính xác cả ba.

**Bot-blocked:** `chelseagreen.com` trả 403 kèm trang thử thách Cloudflare
"Just a moment…" cho cả fetcher lẫn UA trình duyệt thật; tên miền phân giải bình
thường. Đã đánh dấu bằng `<em>` ngay trong ref-list theo quy ước của kệ — link bị
chặn bot, **không phải** link chết.

## Kiểm faithfulness (auditor, mẫu — không vét cạn)

Đối chiếu trực tiếp với văn bản sách: luận điểm cấu trúc-sinh-hành-vi, ví dụ bãi xe
(stock/flow), ngụ ngôn thợ đồng hồ Hora/Tempus (đúng Chương 3), dao động do trễ ở
đội tàu cá (Chương 2), quy tắc 70. Trích dẫn Hardin/Simon ở Phần 2 chính xác.
Thang 12 điểm đòn bẩy ở Phần 3 theo đúng thứ tự và cách gọi của **bản sách 2008**,
và nói rõ chỗ bài luận 1997 khác — **không trộn hai bản**.

**Không phát hiện khẳng định bịa hay trích sai nguồn.**

## Tồn đọng (không chặn PASS)

- Phần 1 có 3 nguồn Wikipedia chống lưng cho định nghĩa mà chính sách đã nói —
  nguồn yếu nhất trang; nguồn gốc sẽ mạnh hơn. Auditor xếp "đáng xem lại ở đợt sau".
- Hardin 1968 vẫn trỏ tới bản PDF do math.uchicago.edu host. Đây là **một bài báo
  đơn lẻ từ 1968**, không phải bản sao nguyên cuốn sách đang bán, và là đường dẫn
  phổ biến nhất để đọc bài này — rủi ro khác hẳn trường hợp PDF toàn văn đã bỏ.
  Giữ nguyên có chủ đích.
