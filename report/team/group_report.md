# Báo cáo nhóm — Day 02 Discovery & Problem Framing

> Bản chung của nhóm, viết trên repo do nhóm trưởng fork. Không copy file này sang repo cá nhân.
> Template chi tiết và prompt mẫu: [docs/01-worksheet.md](../../docs/01-worksheet.md). Bài mẫu: [docs/02-deliverable-example.md](../../docs/02-deliverable-example.md).

## 1. Thông tin nhóm

- Tên nhóm: Nhom3AE
- Thành viên: xem `TEAM.md`
- Candidate problem được chọn (1 câu): Khi backend developer vừa cập nhật code website, cần xác nhận các chức năng cũ vẫn hoạt động đúng trước khi chuyển sang tester, nhằm giảm thời gian kiểm thử lặp lại và hạn chế lỗi hồi quy.
- Quyết định cuối: **Not Yet** — chưa đủ dữ liệu kiểm chứng và chưa xác nhận quyền sử dụng source code với AI; đề xuất pilot nhỏ trên repo mẫu

---

## 2. Hội tụ nhóm (CP3)

### 2.1. Pitch

| # | Người đưa ra | Candidate (Job Story ngắn) | Actor | Bottleneck | Câu hỏi phản biện nhận được (ai hỏi) |
|---:|---|---|---|---|---|
| 1 | Bùi Quang Hiếu | Khi sắp báo tiến độ task backend, muốn biết phần nào đã tự kiểm tra đạt, để không báo hoàn thành quá sớm | Junior Backend Developer; PM dự án | Bước 2: ước lượng và báo PM trước khi self-test đủ; 1 lần trượt khoảng 4 giờ | |
| 2 | Bùi Quang Hiếu | Khi backend lỗi trên môi trường test, muốn xác định request và điều kiện gây lỗi, để tìm đúng nguyên nhân mà không dò code quá lâu | Junior Backend Developer | Bước 3: đọc code khi thiếu log; khoảng 30 phút khi có log, tới 2 giờ khi thiếu log (ước lượng) | |
| 3 | Bùi Quang Hiếu | Khi đến giờ daily report từng dự án, muốn nhớ đúng việc đã làm và phần còn vướng, để PM nhận cập nhật đúng | Junior Backend Developer; PM | Giả thuyết ở bước 1 (nhớ lại việc trong ngày); chưa xác nhận là pain | |
| 4 | Nguyễn Văn Đăng | Khi vừa cập nhật code website, muốn biết chức năng cũ còn chạy đúng, để không chuyển lỗi sang tester | Backend developer; tester và dev liên quan | Bước 3: kiểm thử thủ công 50 phút trong tổng 120 phút/lần, khoảng 3 lần/tuần (theo báo cáo cá nhân) | |
| 5 | Nguyễn Văn Đăng | Khi nhận sửa module người khác viết, muốn hiểu luồng xử lý và phần phụ thuộc, để sửa đúng chỗ | Backend developer; 2 dev khác; người review | Bước 3: đọc luồng xử lý, 50/150 phút mỗi module, 2 lần/tuần | |
| 6 | Nguyễn Văn Đăng | Khi lịch học và lịch làm việc trùng, muốn biết sớm việc nào ưu tiên và cần báo ai, để không trễ deadline | Sinh viên vừa đi làm; đồng nghiệp, nhóm học | Bước 3: trao đổi với người liên quan, 25/90 phút mỗi lần, 2 lần/tháng | |
| 7 | Nguyễn Minh Khôi | Khi khách hàng gửi yêu cầu hỗ trợ về xe, muốn xác định cần trả lời FAQ hay tạo ticket, để khách được xử lý đúng | Khách hàng VinFast; nhân viên chăm sóc khách hàng | Bước phân loại ý định và chọn hành động; chưa có số phút | |
| 8 | Nguyễn Minh Khôi | | | | |
| 9 | Nguyễn Minh Khôi | | | | |

### 2.2. Cluster

Nhóm có **3 thành viên** và hiện ghi nhận **7 candidate có mô tả** (#1–#7); hai dòng #8–#9 của Nguyễn Minh Khôi chưa có nội dung nên **không tự bổ sung** hoặc đưa vào chấm điểm. Nhóm gom theo **bản chất nhu cầu/bottleneck**:

| Cluster | Các candidate | Pattern chung |
|---|---|---|
| **A — Kiểm chứng chất lượng trước bàn giao** | **#1** (Hiếu: self-test trước khi báo hoàn thành); **#4** (Đăng: kiểm tra chức năng cũ sau khi sửa code) | Cần xác nhận phần việc thực sự đạt yêu cầu trước khi báo tiến độ hoặc giao cho người tiếp theo; dễ bỏ sót lỗi nếu kiểm thủ công/thiếu tiêu chí rõ. |
| **B — Hiểu hệ thống và truy tìm nguyên nhân** | **#2** (Hiếu: tìm request/điều kiện gây lỗi); **#5** (Đăng: đọc luồng module do người khác viết) | Phải lần theo code, log và các phụ thuộc để nắm ngữ cảnh; mất thời gian khi thông tin phân tán hoặc thiếu. |
| **C — Phân loại ưu tiên và điều phối công việc** | **#3** (Hiếu: daily report); **#6** (Đăng: xử lý trùng lịch học/làm); **#7** (Khôi: phân loại yêu cầu hỗ trợ xe) | Phải tổng hợp tình huống để xác định thông tin, mức ưu tiên hoặc bước xử lý tiếp theo. Các actor khác nhau nên cluster này còn rộng, cần thu hẹp nếu được chọn. |

**Đại diện nhóm chốt đưa vào shortlist (mỗi cluster 1 problem):** A → **#4** (kiểm thử chức năng cũ); B → **#5** (hiểu module người khác viết); C → **#6** (xử lý lịch học/làm trùng). Tiêu chí chọn đại diện là độ rõ của quy trình và dấu hiệu thời gian; chưa có câu hỏi phản biện được ghi trong bảng pitch.

### 2.3. Opportunity Solution Tree rút gọn

Tree tập trung vào **outcome của problem đang dẫn đầu ở cluster A** (không đưa cả ba nhóm nhu cầu không liên quan vào một outcome). Nhánh là pain/opportunity, chưa phải giải pháp:

```text
OUTCOME: Giảm thời gian backend developer kiểm chứng các chức năng bị ảnh hưởng
         sau khi sửa code, đồng thời hạn chế lỗi hồi quy chuyển sang tester.
├── Opportunity A: Khó xác định chức năng/luồng cũ nào có thể bị ảnh hưởng
│                    bởi thay đổi mới.
├── Opportunity B: Phải kiểm thử lại từng chức năng thủ công, mất 50 phút trong tổng 120 phút/lần
│                    (ước lượng được ghi nhận trong pitch #4).
└── Opportunity C: Thiếu bằng chứng kiểm thử đủ rõ trước khi bàn giao,
                     dễ bỏ sót lỗi hoặc phải kiểm tra lại.
```

**Những ý gạch bỏ vì là solution đội lốt opportunity (ví dụ phản biện, không phải lời pitch thực tế của thành viên):**

- ✗ “Dùng AI tự sinh test case” → giải pháp; opportunity thực sự là *khó bao phủ các luồng bị ảnh hưởng*.
- ✗ “Xây agent chạy toàn bộ regression test” → giải pháp; opportunity thực sự là *kiểm thử hồi quy lặp lại và tốn thời gian*.

### 2.4. Chấm điểm shortlist (1–5)

Chấm **3 problem đại diện cho 3 cluster**, mỗi tiêu chí tối đa 5 điểm, **tổng tối đa 35**; trọng số bằng nhau. Điểm là **kết quả nhóm chốt từ pitch hiện có**, không được hiểu là kết quả khảo sát hoặc đo thực nghiệm. Mốc 120 phút/lần và tần suất 3 lần/tuần là thông tin người đề xuất ghi trong báo cáo cá nhân, chưa có log xác minh.

| Candidate | Actor rõ | Quy trình rõ | Pain có bằng chứng | Impact đo được | Vừa sức lab | So sánh được No AI/Rule/Workflow/Agent | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| **A — #4: Kiểm tra chức năng cũ sau khi sửa code** | 5 | 5 | 4 | 5 | 5 | 5 | 5 | **34** |
| **B — #5: Hiểu luồng module người khác viết** | 5 | 5 | 4 | 5 | 4 | 4 | 5 | **32** |
| **C — #6: Xử lý trùng lịch học và làm việc** | 5 | 4 | 3 | 3 | 5 | 3 | 4 | **27** |

**Giải thích điểm quan trọng:**

- **#4 (34/35):** Backend developer và tester là actor cụ thể; điểm nghẽn là bước kiểm thử thủ công (**50 phút trong tổng 120 phút/lần, khoảng 3 lần/tuần** theo báo cáo cá nhân của Đăng). Có thể đo thời gian, số ca kiểm thử, tỷ lệ lỗi lọt sang tester. Phạm vi lab có thể giới hạn ở một module và so sánh checklist thủ công (**No AI**), điều kiện/quy tắc xác định test (**Rule**), pipeline kiểm thử (**Workflow**) và tác nhân tự lập kế hoạch kiểm thử (**Agent**). **Pain = 4**, không phải 5, vì chưa có nhật ký đo hoặc dữ liệu bug thực tế để đối chiếu.
- **#5 (32/35):** Luồng đọc hiểu module rõ, có ước lượng **50–150 phút/module, 2 lần/tuần**. Tuy nhiên khó kiểm chứng “hiểu đúng luồng” chỉ bằng thời gian, và việc tiếp cận đầy đủ source code/phụ thuộc có thể khiến pilot khó hơn. **Vừa sức lab = 4**.
- **#6 (27/35):** Actor và bối cảnh cụ thể, nhưng chỉ khoảng **2 lần/tháng**; ảnh hưởng thực tế lên deadline chưa được xác minh. Có thể cải thiện bằng lịch chung + quy tắc ưu tiên mà **không cần AI**, nên khả năng chứng minh giá trị thêm của Agent thấp hơn. **Pain = 3; so sánh 4 mức = 3**.

**Candidate được chọn:** **#4 — Khi vừa cập nhật code website, backend developer muốn xác nhận các chức năng cũ vẫn chạy đúng trước khi chuyển sang tester.** (Người đề xuất: **Nguyễn Văn Đăng**, cluster A; **34/35 điểm**.)

**Vì sao chọn:** Đây là problem có tổng điểm cao nhất; quy trình lặp lại thường xuyên, bottleneck và đơn vị đo tương đối rõ, sát chuyên môn backend của nhóm. Có thể thử nghiệm quy mô nhỏ, đo **thời gian kiểm tra hồi quy** và **số lỗi bị bỏ sót**, rồi mới quyết định có cần AI hay chỉ cần checklist/automation test. Chọn *problem*, chưa mặc định phải xây Agent.

**Vì sao loại các candidate còn lại:** **#5** đứng thứ hai (32/35), cũng đáng làm nhưng tiêu chí “hiểu đúng code” và phụ thuộc của module khó đo/kiểm soát hơn trong một lab ngắn. **#6** (27/35) có tần suất thấp và rất có thể giải quyết đủ tốt bằng lịch chung, checklist và rule ưu tiên. Các candidate **#1–#3, #7** vẫn được giữ trong cluster để tham chiếu nhưng **chưa vào shortlist** do đã chọn một đại diện/cluster; #8–#9 chưa có dữ liệu để đánh giá.


---

## 3. Kiểm chứng + research giải pháp đã có (CP4)

> **Trạng thái bằng chứng (09/11/2026):** CP3 ghi nhận mô tả và ước lượng của người đề xuất #4 (**120 phút/lần, gồm 50 phút kiểm thử thủ công; khoảng 3 lần/tuần**), **chưa có log bấm giờ, lịch sử bug, phỏng vấn được ghi âm/ghi chép hoặc pilot thực tế**. CP4 phân biệt rõ **tín hiệu sẵn có**, **research nguồn ngoài**, và **đề xuất kiểm chứng**. Không xem câu trả lời mẫu hoặc mục tiêu kỳ vọng là dữ liệu đã thu thập.

### 3.1. Assumption Map

Quy ước: **Quan trọng** = mức tác động nếu giả định sai (5 là cao nhất); **Đã có bằng chứng** = độ mạnh của bằng chứng hiện có (1 là chưa xác thực, 5 là đo/kiểm nhiều lần). Điểm là đánh giá ban đầu của bản báo cáo, cần nhóm thống nhất lại.

| # | Giả định | Loại (Value / Usability / Feasibility / Viability) | Quan trọng (1–5) | Đã có bằng chứng (1–5) | Kiểm chứng trước? |
|---:|---|---|---:|---:|---|
| 1 | Tự kiểm tra hồi quy sau sửa code mất khoảng 120 phút/lần (bước kiểm thử thủ công 50 phút) và lặp lại khoảng 3 lần/tuần | Value | 5 | 2 | **Có — bấm giờ** |
| 2 | Ngoài 50 phút kiểm thử thủ công, bước xác định luồng và chuẩn bị case cũng có thể gây bỏ sót luồng quan trọng | Value | 5 | 1 | **Có — quan sát quy trình** |
| 3 | Backend developer cần gợi ý test có giải thích và vẫn muốn tự duyệt trước khi bàn giao | Usability | 4 | 1 | **Có — phỏng vấn/thử prototype** |
| 4 | Có thể lấy được diff/PR, danh sách API, test hiện có và kết quả chạy test cho một module nhỏ | Feasibility | 5 | 2 | **Có — kiểm kê dữ liệu** |
| 5 | Checklist + automation test hiện có chưa đủ giúp xác định đầy đủ các case bị ảnh hưởng | Value | 5 | 1 | **Có — làm baseline No AI** |
| 6 | Việc sử dụng source code, log và dữ liệu kiểm thử với mô hình AI được phép theo chính sách bảo mật | Viability | 5 | 1 | **Có — hỏi người phụ trách** |

**Giả định ưu tiên kiểm chứng:** **#1** (thời gian của bottleneck kiểm thử thủ công), rồi **#2, #5** (giả thuyết phụ về chọn case và giá trị tăng thêm của AI); đồng thời chặn triển khai với mã nguồn thật cho đến khi xác nhận **#6**. Nếu #5 sai, nhóm nên chọn Rule/automation *không AI* thay vì cố đưa AI vào.

### 3.2. Kiểm chứng

**Cách đã dùng đến thời điểm viết:** rà soát nội dung pitch ở CP3 và nghiên cứu tài liệu công cụ công khai. **Chưa thực hiện** phỏng vấn mới, survey hoặc phân tích log/ticket thực tế trong thông tin nhóm cung cấp.

**Kịch bản kiểm chứng đề xuất (chưa thực hiện):**

1. **Quan sát 3–5 lần sửa code** trên cùng một module backend: ghi phút dành cho (a) đọc diff/nhận diện ảnh hưởng, (b) chuẩn bị case/dữ liệu, (c) chạy test, (d) phân tích lỗi, (e) tổng hợp bàn giao. Lưu phiên bản commit và độ phức tạp thay đổi để đối chiếu.
2. **Phỏng vấn tối thiểu 2 backend developer và 1 tester ngoài nhóm:** hỏi lần gần nhất phát sinh lỗi hồi quy, cách chọn case, case từng bỏ sót và checklist có sẵn; không hỏi dẫn dắt kiểu “có muốn dùng AI không?”. Lời kể của Đăng là nguồn nội bộ, không tính là phỏng vấn CP4.
3. **Baseline có đối chứng:** lấy 5 thay đổi nhỏ hoặc 5 diff giả lập có đáp án chuẩn; so sánh **checklist/automation hiện có** với **workflow có AI gợi ý**, cùng thời gian chuẩn bị và cùng tập tình huống. Người đánh giá không xem nhãn của phương án trước khi chấm độ bao phủ.
4. **Kiểm kê điều kiện triển khai:** có PR/diff, test suite, API contract, environment và quyền dùng mã nguồn không; nếu không được phép chia sẻ code, chỉ thử bằng repository mẫu/dữ liệu giả lập.

**Interview snapshot:** Chưa có buổi phỏng vấn hợp lệ để ghi snapshot. Dữ liệu hiện có chỉ là trải nghiệm do thành viên nhóm tự mô tả; không tính người trong nhóm vào mẫu phỏng vấn CP4.

**Tổng hợp tín hiệu hiện có:**

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác / giới hạn |
|---|---:|---|---|
| Báo cáo cá nhân của Đăng và pitch nội bộ #4 | 1 người đề xuất, chưa phải phỏng vấn độc lập | Nêu tổng thời gian 120 phút/lần, trong đó 50 phút kiểm thử thủ công; khoảng 3 lần/tuần | Chưa bấm giờ độc lập, chưa có dữ liệu lỗi lọt sang tester |
| Tài liệu pytest, Playwright, GitHub Actions | 3 nhóm tài liệu công cụ | Automation test và CI giải quyết được phần lớn thao tác chạy case lặp lại | Chứng minh khả năng công cụ, **không** chứng minh pain của nhóm hay hiệu quả AI |
| Phỏng vấn / log bug / pilot trực tiếp | **0** | Chưa có | Chưa đủ căn cứ để kết luận AI mang lại lợi ích vượt baseline No AI |

**Nhóm đã sửa problem thế nào sau bước rà soát bằng chứng và research:**

- **Trước:** “Kiểm tra toàn bộ chức năng cũ sau khi sửa code” — phạm vi rộng, dễ hiểu nhầm phải tự động hóa toàn bộ hệ thống.
- **Bản làm việc sau research (chờ xác minh thực địa):** “Khi một PR thay đổi **một module/API backend**, developer cần **kiểm thử lại các chức năng cũ bị ảnh hưởng**, trước khi bàn giao cho tester, để giảm thời gian kiểm thử thủ công mà không bỏ sót lỗi hồi quy.”
- **Phân định:** *chạy test thủ công* vẫn là bottleneck đã nêu trong pitch (50 phút/lần); *nhận diện nguy cơ và đề xuất case còn thiếu* chỉ là giả thuyết phụ cần kiểm chứng. Ưu tiên automation cho test đã biết, không mặc định AI cần thiết.

### 3.3. Research giải pháp đã có

| Công cụ / case / pattern | Link | Giải bước nào trong quy trình? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| **Playwright (API testing / codegen)** | https://playwright.dev/docs/api-testing ; https://playwright.dev/docs/codegen | Tạo/chạy bài test UI hoặc API; ghi lại thao tác để tạo test UI | Test có assertion rõ; có thể chạy lặp lại khi sửa code | Codegen ghi thao tác, không tự chứng minh đã bao phủ hết tác động gián tiếp từ PR | Dùng để **thực thi/ghi nhận bằng chứng test**, không dùng AI để “tự tuyên bố đạt” |
| **pytest** | https://pytest.org/en/latest/how-to/parametrize.html | Chạy test có tham số, fixture và assertions | Phù hợp thử nghiệm backend Python nhỏ, dễ tạo bộ test có expected output | Chỉ bảo vệ trường hợp đã được thiết kế; với dự án Java cần JUnit thay thế | Tách **đề xuất tình huống** khỏi **assertion xác minh**; chọn framework theo stack thật |
| **GitHub Actions (CI)** | https://docs.github.com/en/actions/tutorials/build-and-test-code/python | Chạy test tự động và lưu kết quả theo lần thay đổi | Quy trình lặp lại, tái hiện được, kết hợp với report coverage | CI không tự quyết định đầy đủ các luồng liên quan; môi trường test thiếu ổn định gây test flaky | Dùng CI/runner sẵn có cho phần Rule/Workflow trước khi thêm AI |
| **Qodo Cover (AI test generation)** | https://github.com/qodo-ai/qodo-cover ; https://github.com/qodo-ai/qodo-cover/blob/main/docs/features.md | Gợi ý/sinh thêm test theo code và phần thiếu coverage | Có hướng tiếp cận sinh test hướng vào diff/coverage | Test sinh ra vẫn phải review; pass/coverage tăng không đồng nghĩa phát hiện đúng lỗi nghiệp vụ; cần kiểm tra điều khoản/giới hạn | **Không nên tự xây agent sinh test từ đầu** trước khi so sánh công cụ có sẵn và baseline |

**Kết luận research:** Công cụ chạy test và CI có thể giải quyết bottleneck **kiểm thử thủ công**; việc *chọn đúng test và tìm case còn thiếu* chỉ là giả thuyết phụ. Phương án đáng kiểm là **Rule chạy test đã biết → AI đề xuất case rủi ro (nếu cần) → developer duyệt → automation chạy case bổ sung → tester nhận evidence**. Nếu checklist + CI đã đủ tốt, không dùng AI. Các đường dẫn trên là tài liệu sản phẩm, **không phải bằng chứng nhóm đã cài/đo hiệu quả**.

---

## 4. Quy trình trước/sau (CP5)

> Thời gian từng bước lấy từ báo cáo cá nhân của Đăng: **10 + 20 + 50 + 25 + 15 = 120 phút/lần**, khoảng **3 lần/tuần** theo lời kể. Chưa có log bấm giờ hoặc kiểm chứng độc lập; pilot cần đo lại.

### 4.1. Quy trình hiện tại

```text
HIỆN TẠI — 120 phút/lần theo báo cáo cá nhân (chưa bấm giờ độc lập)
[1. Xác định các chức năng cần kiểm tra: 10']
  → [2. Chuẩn bị dữ liệu và môi trường: 20']
  → [3. Kiểm thử từng chức năng thủ công: 50']  ← BOTTLENECK
  → [4. Ghi nhận vấn đề phát hiện: 25']
  → [5. Kiểm tra lại và tổng hợp kết quả: 15']
```

| Bước | Actor | Input | Output | Thời gian / tần suất | Ghi chú |
|---:|---|---|---|---|---|
| 1 | Backend developer | Code vừa cập nhật, mô tả chức năng | Danh sách chức năng cần kiểm | **10'/lần theo Đăng** | Cần xác nhận cách xác định luồng bị ảnh hưởng |
| 2 | Backend developer | Danh sách chức năng, dữ liệu/môi trường test | Dữ liệu và môi trường sẵn sàng | **20'/lần theo Đăng** | Chưa kiểm chứng độc lập |
| 3 | Backend developer | Chức năng cần kiểm, dữ liệu test | Kết quả kiểm thử từng chức năng | **50'/lần theo Đăng** | Bottleneck: kiểm thử thủ công lặp lại |
| 4 | Backend developer | Kết quả kiểm thử | Vấn đề được ghi nhận | **25'/lần theo Đăng** | Chưa có số liệu lỗi thực tế |
| 5 | Backend developer | Vấn đề đã ghi nhận, kết quả kiểm thử | Kết quả kiểm tra lại và bản tổng hợp | **15'/lần theo Đăng** | Chưa xác nhận thời gian bàn giao riêng |

**Bottleneck chính:** Bước 3, kiểm thử thủ công chức năng cũ, chiếm **50/120 phút** theo báo cáo cá nhân của Đăng. Việc xác định luồng/case ở bước 1–2 có gây bỏ sót hay không vẫn là giả thuyết phụ. Tần suất theo lời kể khoảng **3 lần/tuần**, chưa đo độc lập.

### 4.2. Quy trình tương lai

**Thiết kế đề xuất cho một module/API nhỏ**, không coi là kết quả pilot:

```text
TƯƠNG LAI — WORKFLOW CÓ ĐIỂM AI HỖ TRỢ (mục tiêu minh họa <=45 phút)
[1. Lấy diff + chạy test có sẵn theo mapping: 5']  ← RULE / AUTOMATION
    → [2. Phân tích diff, đề xuất luồng rủi ro + case thiếu: 3']  ← AI, CHỈ GỢI Ý
    → [3. Developer kiểm đề xuất, chọn/sửa case, đặt expected output: 12'] ← CON NGƯỜI
    → [4. Chạy test được duyệt, lưu pass/fail/log: 15'] ← AUTOMATION + RULE
    → [5. Developer kiểm lỗi và xác nhận evidence: 7'] ← CON NGƯỜI
    → [6. Developer bàn giao tester kèm danh sách case/chưa kiểm: 3'] ← CON NGƯỜI

BOUNDARY: AI không tự sửa code sản phẩm, không tạo dữ liệu thật,
          không dùng credential production, không bỏ qua test thất bại,
          không tự phê duyệt PR hoặc tự bàn giao.
FALLBACK: AI đề xuất sai/không truy được nguồn → bỏ đề xuất AI,
          chạy test suite + checklist đã duyệt; developer quyết định.
```

**Chi tiết điểm AI:** Input được phép gồm diff, API contract, mô tả hành vi và bộ test mẫu **đã được khử dữ liệu nhạy cảm**. Output là bảng *đường code thay đổi → hành vi có thể bị ảnh hưởng → test gợi ý → lý do → bằng chứng tham chiếu*. AI không tạo “pass/fail”; kết quả chỉ được công nhận khi công cụ chạy test với expected result do người xác nhận. Nếu bản thân bộ test có lỗi hoặc môi trường không ổn định, người kiểm tra phải phân loại thay vì để AI kết luận.

### 4.3. Before / after

| Chỉ số | Trước | Sau (kỳ vọng) | Ghi chú |
|---|---:|---:|---|
| Số bước | 5 | 6 | Tách riêng bước gợi ý của AI và bước người duyệt để minh bạch |
| Tổng thời gian | **120'/lần theo Đăng, chưa đo độc lập** | **45'/lần** (mục tiêu thử nghiệm, tổng 5+3+12+15+7+3) | Không tuyên bố đã giảm thời gian; cần so với baseline có CI **không AI** |
| Số bước thủ công | 5/5 theo quy trình Đăng mô tả | 3/6 bước có người xác nhận/chỉnh sửa | Bước 1, 2, 4 được công cụ hỗ trợ; vẫn cần giám sát |
| Bottleneck chính | **Bước 3: kiểm thử thủ công (50'/120')** | Chạy test bằng automation; developer vẫn duyệt case và kiểm kết quả | Chọn case khó có thể là pain phụ, chưa được kiểm chứng; nếu đã có suite tốt thì lợi ích thêm có thể nhỏ |
| Rủi ro mới phát sinh | Bỏ sót luồng; evidence thiếu thống nhất | AI bịa luồng/expected result; quá tin AI; lộ mã nguồn; test flaky | Khống chế bằng review, sandbox, logging, fallback |

**Nguyên tắc so sánh công bằng:** luôn đo 3 phiên bản trên cùng tập thay đổi: **A — checklist thủ công**, **B — Rule + automation + CI (không AI)**, **C — B + AI đề xuất case**. Giá trị AI = phần tăng thêm của C so với B (không được quy toàn bộ mức giảm của A→C cho AI).

---

## 5. Problem Statement v0 (CP5)

| Trường | Nội dung |
|---|---|
| **Actor** | Backend developer vừa sửa một module/API của website; tester là người nhận kết quả bàn giao |
| **Quy trình** | Xác định chức năng cần kiểm → chuẩn bị dữ liệu/môi trường → kiểm thử thủ công → ghi nhận vấn đề → kiểm tra lại, tổng hợp trước bàn giao tester |
| **Bottleneck** | **Bước 3: kiểm thử từng chức năng thủ công mất 50 phút trong tổng 120 phút/lần**, khoảng 3 lần/tuần theo báo cáo cá nhân của Đăng; chưa đo độc lập |
| **Impact** | Tốn thời gian tự kiểm thử trước bàn giao, nguy cơ bỏ sót lỗi hồi quy; **chưa có số bug lọt sang tester**. Khoảng **360 phút/tuần** là phép nhân 120 phút × 3 lần theo lời kể, không phải thời gian đã bấm giờ |
| **Success Metric** (baseline → target, cách đo) | Baseline tham khảo **120 phút/lần** (trong đó bước 3 là **50 phút**) → mục tiêu thử **≤45 phút/lần** cho toàn quy trình; bấm giờ từng bước trên 5 PR/tình huống tương đương, đo thêm số case quan trọng bị bỏ sót và lỗi lọt sang tester; điều chỉnh target sau khi có baseline thực đo |
| **Boundary** (AI không được làm gì; khi nào cần con người kiểm tra — HITL) | AI chỉ gợi ý ảnh hưởng và test case; developer xác nhận expected output, duyệt case, đọc báo cáo và quyết định bàn giao; không tự sửa code, không tự ký duyệt, không gửi code/secret trái phép |

**Phản biện từ AI (chưa phải phản biện thật của nhóm khác):** “Tự động chạy test bằng CI đã giảm thời gian; làm sao chứng minh tác dụng *riêng* của AI?” **Đồng ý.** Bổ sung baseline **B — CI/Rule không AI**, đo khả năng tìm case bị thiếu và chất lượng gợi ý, không chỉ tốc độ. Phản biện thứ hai: “Mục tiêu ≤45 phút là đặt trước, chưa có đo thực tế” — **đồng ý**, ghi đây là mục tiêu cần điều chỉnh sau quan sát.

---

## 6. Mức can thiệp AI (CP6)

### 6.1. Ma trận độ mơ hồ × độ phức tạp

**Ô đề xuất: Mơ hồ trung bình × Phức tạp trung bình** (đối với pilot **một module/API**).

**Vì sao:** Bottleneck đã ghi nhận là **chạy test thủ công**: bước này ít mơ hồ, có thể ưu tiên Rule/automation. Việc suy luận từ diff đến hành vi gián tiếp cần kiểm thêm có độ mơ hồ trung bình nhưng mới là **giả thuyết phụ**; pilot một module có nhiều nguồn (diff, contract, test, kết quả) và các bước định sẵn. Vì vậy chỉ **đề xuất thử** Workflow với một bước AI để kiểm tra giá trị tăng thêm; agent tự trị chưa có lý do thuyết phục.

### 6.2. So sánh 4 mức

| Mức | Phương án cho bài của nhóm | Đủ khi nào | Rủi ro | Chọn? |
|---|---|---|---|---|
| **No AI** (sửa quy trình) | Checklist hồi quy theo module, tiêu chí bàn giao, bắt buộc đính kèm evidence | Ít API, thay đổi có phạm vi rõ, vấn đề chủ yếu là thiếu kỷ luật kiểm thử | Bảo trì checklist thủ công; dễ thiếu case mới | **Baseline A** |
| **Rule** | Mapping file/API → test suite; chạy test tự động, assertion và coverage cố định | Case đủ rõ, dependency mapping tương đối ổn định | Mapping cũ, coverage cao nhưng thiếu kiểm thử nghiệp vụ | **Baseline B — nền tảng** |
| **Workflow** | Rule lấy diff/chạy case → AI đề xuất luồng/case còn thiếu → developer duyệt → test runner thực thi → tổng hợp evidence | Rule làm phần xác định; AI chỉ bổ sung trường hợp không hiển nhiên và con người review được | Gợi ý sai/hallucination; rò rỉ source; tốn chi phí review | **Phương án C đề xuất pilot** |
| **Agent** | Tác nhân tự khám phá code, tự quyết định tool/test, tự sửa hoặc lặp test nhiều vòng | Chỉ cân nhắc khi có nhánh xử lý không dự đoán trước được, đủ logging, quyền và sandbox | Quyền rộng, khó dự đoán, có thể sửa sai và làm sai lệch evidence | **Không chọn** |

**Mức chọn để thử nghiệm:** **Workflow (Rule + AI ở một bước + Human-in-the-loop)**; **chưa khẳng định cần AI cho triển khai thật**.

**Vì sao chưa chốt mức đơn giản hơn:** Bottleneck kiểm thử thủ công có thể được xử lý bằng checklist và Rule/CI. Chỉ thử thêm C để kiểm chứng giả thuyết *mapping và case hiện có có điểm mù khi code thay đổi*; **chưa có dữ liệu chứng minh điểm mù này trong dự án thực**. Nếu C không cải thiện chất lượng so với B (Rule + CI không AI), nhóm **chốt không AI**.

### 6.3. AI Canvas rút gọn

| Thành phần | Nội dung |
|---|---|
| **Prediction** — AI dự đoán / tạo ra gì? | Danh sách module/luồng có thể bị ảnh hưởng bởi PR, test case nên bổ sung và mức ưu tiên, kèm tham chiếu tới diff/contract (không tự tuyên bố pass) |
| **Judgment** — con người cân nhắc, quyết định gì? | Developer xác nhận phạm vi ảnh hưởng, expected output, tính hợp lý và ưu tiên từng case; tester có quyền phản hồi thiếu case |
| **Action** — hành động cuối cùng là gì, ai làm? | Developer chọn/sửa case; runner chạy test; developer duyệt báo cáo và bàn giao, tester tiếp tục test độc lập |
| **Outcome** — đo kết quả bằng gì? | Phút/PR; tỷ lệ luồng quan trọng được bao phủ; số case hợp lệ bổ sung so với baseline B; false-positive; số lỗi lọt sang tester |
| **Input** — AI cần dữ liệu đầu vào gì mỗi lần chạy? Có sẵn không? | Diff/PR, tên module, API contract, test suite cũ, mô tả nghiệp vụ; **chưa xác nhận nhóm có đủ dữ liệu và quyền truy cập**; dùng repo mẫu ở pilot |
| **Feedback** — lấy phản hồi ở đâu để cải thiện? | Case developer chấp nhận/từ chối kèm lý do; false positive khi review; lỗi tester phát hiện mà gợi ý bỏ sót; report CI |

### 6.4. Hai câu hỏi của Google PAIR

- **Augment hay automate?** **Đề xuất augment** ở khâu chọn case và nhận diện ảnh hưởng; **automate bằng quy tắc** cho bước chạy test đã biết. Đây là lựa chọn thiết kế **chưa được người dùng phỏng vấn xác nhận**. Cần hỏi developer họ có muốn duyệt từng case hay chỉ nhận báo cáo tổng hợp.
- **AI sai kiểu nào tệ hơn — báo nhầm hay bỏ sót?** **Bỏ sót** luồng hồi quy quan trọng tệ hơn vì lỗi có thể lọt đến tester hoặc sản phẩm. Báo nhầm gây tốn thời gian review nhưng thường có thể loại bỏ trước khi chạy. Do đó giữ **minimum test suite bắt buộc không phụ thuộc AI**, đánh dấu case chưa kiểm và tuyệt đối không coi “AI không đề xuất” là bằng chứng an toàn.

---

## 7. Problem Statement v1 + tiêu chí đánh giá (CP6)

| Trường | Nội dung |
|---|---|
| **Actor** | Backend developer phụ trách **một PR sửa module/API backend**, có tester nhận bàn giao; chỉ áp dụng trong repo/module có test suite và môi trường thử nghiệm |
| **Quy trình** | Đọc diff → chạy minimum regression suite bằng rule → nhận AI gợi ý luồng/case → developer duyệt và bổ sung → chạy test → kiểm evidence → bàn giao tester |
| **Bottleneck** | **Kiểm thử thủ công chức năng cũ: 50 phút trong tổng 120 phút/lần theo Đăng**. Khó chọn case bị ảnh hưởng là giả thuyết phụ, chưa được xác minh là bottleneck |
| **Impact** | Theo lời kể, tự kiểm thử mất **120 phút/lần, khoảng 3 lần/tuần**; chưa có log bấm giờ hay số bug lọt sang tester xác thực |
| **Success Metric** (baseline → target, cách đo) | **Thời gian**: baseline tham khảo **120'/lần (bước kiểm thử thủ công 50')** → mục tiêu thử **≤45'/lần** cho toàn quy trình; đo từng bước trên 5 thay đổi tương đương cho A/B/C. **Chất lượng**: bao phủ **≥90% luồng rủi ro quan trọng** trong gold set, **không bỏ sót lỗi nghiêm trọng**; **giá trị tăng thêm của AI**: C có ít nhất 1 case hợp lệ có ý nghĩa so với B mà không vượt ngân sách thời gian. Tất cả là **ngưỡng đề xuất, chưa đo** |
| **Boundary** | AI chỉ đề xuất và giải thích; không tự sửa source, không đẩy code, không tự phê duyệt PR hoặc bàn giao, không bỏ qua test fail; không gửi source/log chứa secret lên dịch vụ ngoài nếu chưa được phép |
| **AI intervention point** | Sau khi thu được diff + minimum suite, **trước bước developer chọn các case hồi quy bổ sung** |
| **Mức chọn** | **Workflow (pilot, có AI một bước)**; baseline bắt buộc **No AI** và **Rule/CI không AI** |
| **Rủi ro & người kiểm tra** | Hallucination case/expected output → backend developer duyệt; thiếu coverage → tester đối chiếu gold cases; lộ dữ liệu → người quản lý repo duyệt phạm vi; flaky test → developer phân loại fail và chạy lại theo quy tắc |

**Thay đổi so với v0 và lý do:**

| Trường | v0 | v1 | Vì sao đổi |
|---|---|---|---|
| Phạm vi | Sửa một module/API website, kiểm chức năng cũ | Chỉ **một PR, một module/API**, có suite và môi trường test | Tránh bài toán kiểm thử toàn hệ thống quá rộng với 3 người |
| Bottleneck | Chạy kiểm thử thủ công 50' trong tổng 120' | **Giữ nguyên** bước kiểm thử thủ công; tách việc chọn case thành giả thuyết phụ để thử riêng | CI/Rule có thể giải bước nghẽn; chưa chắc AI cần thiết |
| Success Metric | Thời gian <=45' và số case lỗi lọt tester | Thêm **coverage gold cases**, chất lượng case và chênh lệch C so với B | Không được tính lợi ích của automation thường thành lợi ích AI; tránh chạy nhanh nhưng bỏ sót lỗi |
| Boundary | AI chỉ gợi ý, developer duyệt | Giới hạn dữ liệu được phép dùng, test suite bắt buộc, không phê duyệt/bàn giao tự động | Kiểm soát bảo mật và nguy cơ tin nhầm đầu ra AI |

**Tiêu chí đánh giá đầu ra AI (pilot 5 diff/test scenarios, đánh giá độc lập bởi người trong nhóm):**

| # | Tiêu chí | Đạt khi | Không đạt khi |
|---:|---|---|---|
| 1 | **Liên quan thay đổi** | Mọi case được nhận đều liên hệ được với dòng diff/API contract/hành vi đã mô tả | Case không liên quan, bịa API/hành vi hoặc không chỉ ra nguồn |
| 2 | **Không bỏ sót nguy cơ quan trọng** | >=90% luồng rủi ro quan trọng trong gold cases được đề xuất hoặc có trong minimum suite | Thiếu trên 10% hoặc thiếu một case nghiêm trọng bắt buộc |
| 3 | **Testable và đúng expected result** | Case có precondition, input, steps, expected result; expected được developer xác nhận và chạy lặp lại được | Case mơ hồ, assertion không kiểm được hoặc expected result sai |
| 4 | **Tỷ lệ gợi ý hữu ích** | >=70% case AI đề xuất được developer chấp nhận sau review (trên tập pilot nhỏ) | Nhiều false-positive khiến developer phải viết lại phần lớn |
| 5 | **Giá trị tăng thêm so với Rule** | Phương án C phát hiện ít nhất 1 case rủi ro có giá trị mà B bỏ sót và đạt ngân sách thời gian đã đặt | C chỉ lặp lại case B đã có hoặc tăng chi phí review không tương xứng |

**Định nghĩa đo:** `coverage_important = số luồng quan trọng được test / tổng số luồng quan trọng trong gold set`; `acceptance_rate = số gợi ý được chấp nhận / tổng gợi ý` (không dùng khi mẫu số bằng 0); `time = từ mở diff đến lúc hoàn tất evidence, không cộng thời gian chờ công việc khác`. Người chấm gold set nên thống nhất tiêu chí **trước** khi xem đầu ra AI.

---

## 8. Quyết định (CP6)

### 8.1. Bốn rủi ro

| Rủi ro | Câu hỏi | Mức độ rủi ro (Thấp = an toàn / TB / Cao = nguy hiểm) | Lý do / bằng chứng |
|---|---|---|---|
| **Value** | Người dùng có thật sự cần và sẽ dùng không? | **Cao (chưa xác thực)** | Mới có 1 pitch với thời gian ước lượng; chưa chứng minh AI hơn Rule/CI và chưa có dữ liệu bug lọt tester |
| **Usability** | Người dùng có dùng được, có hiểu và sửa được đầu ra của AI không? | **Trung bình** | Developer quen test case nhưng chưa kiểm được họ có muốn đọc/duyệt gợi ý AI và tốn bao nhiêu phút |
| **Feasibility** | Có đủ dữ liệu, công cụ, kỹ năng để làm không? | **Trung bình** | Có sẵn framework test/CI và công cụ gợi ý test; chưa kiểm repo, quality của suite, API contract và môi trường |
| **Viability** | Có hợp chi phí, pháp lý, quy định tổ chức không? Ai vận hành? | **Cao (chưa xác thực)** | Chưa có xác nhận quyền dùng source/log với AI; nếu dùng mã nguồn nội bộ thì đây là điều kiện chặn, không phải rủi ro có thể bỏ qua |

### 8.2. Kết luận

**Quyết định: Not Yet — chỉ Go cho nghiên cứu/pilot trên repo mẫu hoặc dữ liệu đã được phép; chưa Go triển khai AI trên code nội bộ.**

**Lý do:** Candidate có điểm CP3 tốt nhưng chứng cứ thực địa mới có một pitch; công cụ No AI/Rule hiện có có thể đã giải quyết phần lớn pain. Chưa xác minh được AI tăng coverage so với CI thuần, và chưa rõ quyền sử dụng mã nguồn. Theo tinh thần bài mẫu, research có thể khiến nhóm **đổi mức can thiệp hoặc không dùng AI** nếu kết quả kiểm chứng không ủng hộ.

**Nếu Go — pilot nhỏ nhất (sau khi giải quyết các điều kiện):**

1. Chọn **1 module backend mẫu**, tạo **5 PR/diff nhỏ** gồm thay đổi thông thường, edge case và dependency gián tiếp; nhóm tự lập gold set luồng rủi ro/expected result **trước** khi xem output AI.
2. Chạy 3 phương án **A checklist**, **B checklist + test runner/CI**, **C = B + AI gợi ý case**; giữ cùng input, chấm **thời gian, coverage, case có ích, false-positive, lỗi bỏ sót**.
3. Phân vai **3 người**: (i) chuẩn bị diff/gold set (không chấm output AI), (ii) dựng baseline runner/CI và ghi giờ, (iii) thử AI và ghi case gợi ý; **đổi người review chéo** để hạn chế thiên lệch, ghi vai trò thực tế sau khi nhóm đồng ý.
4. Developer luôn duyệt và chỉnh test; tester/đồng đội đối chiếu gold set; không auto-merge, không sửa production, không cần quyền repo nội bộ để chạy pilot giả lập.

**Nếu Not Yet — cần kiểm chứng gì trước:**

- **Value:** bấm giờ 3–5 lần sửa code thật hoặc tương đương, hỏi 2 developer + 1 tester ngoài nhóm; xác định pain đã nêu ở bước chạy test thủ công có lặp lại không, và việc chọn case có phải pain phụ đáng giải không.
- **Feasibility:** kiểm kê diff, contract, test, CI, quyền đọc; tái tạo 5 PR nhỏ trong repo mẫu, tạo gold set trước khi đánh giá.
- **Viability:** xin phép người quản lý repo về phạm vi dữ liệu và công cụ được phép; nếu không được phép, tuyệt đối không tải code nội bộ lên mô hình ngoài.
- **Quyết định sau pilot:** chỉ cân nhắc Go nếu C có thêm case quan trọng so với B, không bỏ sót case nghiêm trọng, đạt ngưỡng thời gian/coverage, không vi phạm chính sách. Nếu B bằng hoặc hơn C, chọn **Rule/CI không AI**.

**Nếu No-Go — nên làm gì thay AI:** chuẩn hóa checklist hồi quy theo module; gắn test với thay đổi API; tự động chạy test + báo cáo qua CI; yêu cầu developer đính kèm evidence trước bàn giao.

**Ngưỡng dừng / quay về:**

- Không có quyền sử dụng dữ liệu với AI → **dừng phương án C**, chỉ dùng repo mẫu hoặc B (No AI/Rule).
- Trong 5 tình huống pilot, AI bỏ sót **bất kỳ luồng nghiêm trọng** nào mà baseline/đáp án chuẩn có, hoặc tạo expected result sai không được phát hiện trong review → tạm dừng dùng C để hỗ trợ bàn giao, điều chỉnh bước kiểm.
- C không thêm case giá trị nào so với B **hoặc** thời gian review khiến tổng thời gian C > B → **chọn B**, không tiếp tục xây AI Agent.

---

## 9. Hạn chế và hướng tiếp theo

- Bằng chứng pain hiện tại dựa trên báo cáo cá nhân của Đăng và pitch CP3; **không có phỏng vấn độc lập, lịch sử bug hoặc log thời gian đã xác thực**. Tổng 120 phút (trong đó kiểm thử thủ công 50 phút) là lời kể chưa đo độc lập; target 45 phút là giả thuyết, không phải kết quả thực nghiệm.
- Research về công cụ chứng minh giải pháp **có tồn tại**, không chứng minh chúng phù hợp ngay với stack/module thực tế của nhóm. Cần chọn framework theo stack thật (ví dụ JUnit cho Java) và kiểm tra quyền truy cập code.
- Để tránh thiên lệch, cần gold set đánh giá trước, các case quan trọng được xác định độc lập, và đối chứng **CI không AI**. Với 5 diff, kết luận chỉ có ý nghĩa định hướng, chưa đủ khái quát hóa.
- Sau khi kiểm chứng, cập nhật Assumption Map, Snapshot, điểm Value/Viability, baseline thực đo và quyết định Go/Not Yet/No-Go. Nếu CI không AI đủ tốt, đó là một kết luận hợp lệ, không cần ép bài thành Agent.

## 10. Tài liệu tham khảo

1. **Nguồn nội bộ:** `report/individual/2A202603371_NguyenVanDang.md`, mục **2–3** (120 phút/lần, 50 phút ở bước kiểm thử thủ công, khoảng 3 lần/tuần); `group_report.md`, mục **2.1 Pitch #4**, **2.2–2.4 CP3** (điểm shortlist nhóm đã chốt, không phải kiểm chứng độc lập).
2. **Bài mẫu:** `docs/02-deliverable-example.md`, mục CP4–CP6 (tham khảo cách trình bày assumption map, so sánh 4 mức, decision gate; không sao chép tình huống/số liệu mẫu).
3. **Playwright — API testing:** https://playwright.dev/docs/api-testing (kiểm thử REST API và assertions).
4. **Playwright — Test generator:** https://playwright.dev/docs/codegen (record thao tác và tạo test UI).
5. **pytest — Parametrizing test functions:** https://pytest.org/en/latest/how-to/parametrize.html (test theo bộ input/expected result).
6. **GitHub Docs — Building and testing Python:** https://docs.github.com/en/actions/tutorials/build-and-test-code/python (chạy test trong CI).
7. **Qodo Cover — repository:** https://github.com/qodo-ai/qodo-cover (công cụ sinh test với AI).
8. **Qodo Cover — diff-based coverage:** https://github.com/qodo-ai/qodo-cover/blob/main/docs/features.md (mô tả hướng sinh test theo thay đổi).
