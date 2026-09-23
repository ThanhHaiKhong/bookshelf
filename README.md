# bookshelf

Kệ sách đọc-cùng — mỗi cuốn là một site companion song ngữ (VI/EN) tự chứa, không
framework, một trang HTML mỗi chương. Trang `index.html` gốc là **kệ**: card link
tới từng cuốn, nhóm theo chủ đề.

A read-along bookshelf — each book is a self-contained bilingual (VI/EN) companion
site (no framework, one HTML page per chapter). The root `index.html` is the
**shelf**, grouping every book by topic.

## Cấu trúc / Layout

```
bookshelf/
├── index.html                      # KỆ: card mỗi cuốn, nhóm theo chủ đề
├── README.md
├── .gitignore                      # src/ *.pdf *.epub — chặn sách gốc
│
├── systems/                        # nhóm chủ đề = thư mục thuần, KHÔNG có index.html
│   └── <book-slug>/                # mỗi cuốn = 1 site tự chứa
├── mind/
│   └── <book-slug>/
├── ai/
│   └── <book-slug>/
└── essays/                         # bài lẻ, không phải sách — không qua book-qa
```

Mỗi cuốn, **luôn phẳng**:

```
<book-slug>/
├── index.html                      # bìa cuốn (book-cover-curator sở hữu)
├── chapter-1-….html …              # một trang mỗi chương
├── mind-map.html                   # tổng hợp toàn cuốn (tuỳ chọn)
├── COMPLETION-<book-slug>.md        # báo cáo hoàn tất (auditor PASS)
└── src/                            # sách gốc — GITIGNORED, không bao giờ commit
```

## Luật cấu trúc / Structural rules

1. **Mọi trang của một cuốn là anh em phẳng của `index.html`.** Không bao giờ có
   thư mục con chứa `.html`. `book-qa` lấy project root = thư mục của chính trang
   đó, nên lồng sâu hơn là gãy cổng kiểm.
2. **Mọi href nội bộ trong một cuốn là tên file trần** (`href="chapter-2-….html"`).
   Href nhiều đoạn chỉ tồn tại ở **card của kệ**.
3. **`src/` là nơi duy nhất chứa sách gốc, và nó bị gitignore.** Sách gốc có bản
   quyền: không commit, không publish. `.gitignore` phải có trước commit đầu tiên —
   nó không gỡ được file đã staged.
4. **Nhóm chủ đề là thư mục thuần**, không có `index.html` riêng. Chỉ có **một**
   trang kệ, ở gốc.
5. **Slug thống nhất**: tên thư mục == hậu tố `COMPLETION-<slug>.md`.

## Tiêu chí / Criteria

Tiêu chí viết một trang nằm ở **[`CHECKLIST.md`](CHECKLIST.md)** — **một bản duy nhất
cho cả kệ**, không chép vào từng thư mục sách (bản sao sẽ trôi lệch). Nó cũng ghi lại
những bẫy đã mắc phải, để khỏi mắc lại.

## Quy trình mỗi cuốn / Per-book pipeline

`book-chapter-author` (song song, một chương một file) → `book-cover-curator`
(tuần tự, tích hợp bìa + nav trong cuốn) → `book-fidelity-auditor` (read-only,
done-gate).

Truyền cho agent **đường dẫn tuyệt đối tới thư mục cuốn** (`<category>/<book-slug>/`),
không phải gốc kệ.

**Xong nghĩa là:** auditor trả PASS → viết `COMPLETION-<slug>.md` → card của cuốn
xuất hiện trong khối `BOOKS` của kệ.

**Luật tối cao: "không bịa"** — mọi số liệu/trích/ví dụ đích danh phải có cite `[N]`
trỏ tới nguồn ngoài thật. Không có tham chiếu thì không lên trang.

## Kệ và fence / The shelf and its fences

Card nằm giữa `<!-- BOOKS:START -->` và `<!-- BOOKS:END -->`. Mỗi card lại nằm
trong fence riêng của nó:

```html
<!-- BOOK:<slug>:START -->
<a class="book" href="<category>/<slug>/index.html"> … </a>
<!-- BOOK:<slug>:END -->
```

`book-cover-curator` chỉ được sửa fence `BOOK:<slug>` của đúng cuốn nó vừa tích
hợp. Thứ tự card, tiêu đề nhóm và prose của kệ thuộc main session.

Khối `BOOKS` **chính là** manifest — không có `books.json` song song, vì hai nguồn
sự thật sẽ lệch nhau. Thay vào đó nó được **máy kiểm**: `book-qa index.html
--kind shelf` xác nhận hai chiều — mọi card resolve tới một cuốn có thật, **và**
mọi thư mục cuốn đều có card.

## Đọc / Read

GitHub Pages: <https://thanhhaikhong.github.io/bookshelf/>
