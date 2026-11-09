# Báo cáo cá nhân — 2A202603639_BuiQuangHieu

> Bản nháp CP1–CP2 dựa trên trao đổi với trợ lý AI. Hiếu cần tự kiểm tra lại từng Job Story, quy trình và số liệu trước khi nộp; các mục chưa có bằng chứng không được xem là đã kiểm chứng. Template chi tiết: [docs/01-worksheet.md](../../docs/01-worksheet.md).

## 1. Thông tin học viên

- Họ tên: Bùi Quang Hiếu
- MSSV: 2A202603639
- Email trường (không bắt buộc, repo có thể để public):
- Tên nhóm: Nhom3AE
- Link repo nhóm: https://github.com/khoii3110/K5-L3A-Day02-Nhom3AE-DiscoveryProblemFraming

---

## 2. Scan problem (CP1)

Lăng kính: **Lặp lại** · **Tốn thời gian** · **Cần đọc, tổng hợp nhiều thông tin** · **Pain từ người khác**.

| # | Lăng kính | Job Story: Khi… tôi muốn… để… | Ai chịu ảnh hưởng? | Dấu hiệu thật (thời gian, tần suất, số người, bằng chứng) |
|---:|---|---|---|---|
| 1 | Lặp lại | Khi đến giờ báo cáo công việc hằng ngày cho từng dự án, tôi muốn nhớ đúng việc đã làm và phần còn vướng, để PM nhận được cập nhật đúng trong channel Slack tương ứng. | Hiếu (Junior Backend Developer), PM các dự án | Hiếu cho biết phải gửi daily report cho các dự án đang tham gia; thường nhớ lại việc trong ngày rồi viết. Chưa đo thời gian viết hoặc số dự án/ngày. |
| 2 | Tốn thời gian | Khi sắp báo tiến độ một task backend, tôi muốn biết phần nào đã tự kiểm tra đạt và phần nào chưa, để không báo thời điểm hoàn thành quá sớm. | Hiếu, PM | Một lần gần đây Hiếu báo sẽ xong trong buổi sáng; sau khi self-test chức năng xuất PDF/Word/Excel phải sửa thêm khoảng 4 giờ. |
| 3 | Cần đọc, tổng hợp nhiều thông tin | Khi quay lại một task có yêu cầu từ nhiều nguồn, tôi muốn xác định yêu cầu nào đang có hiệu lực, để triển khai đúng điều đã được thống nhất. | Hiếu; PM hoặc người đưa ra yêu cầu nếu có thay đổi | Một yêu cầu mơ hồ từ khách hàng về dự án yêu cầu phía công ty tự triển khai và sếp thường xuyên bổ sung idea nhưng chỉ qua nói miệng |
| 4 | Cần đọc, tổng hợp nhiều thông tin | Khi chuẩn bị bàn giao code của một task, tôi muốn biết thay đổi trên GitLab đã đáp ứng những tiêu chí nào trong Jira, để không bỏ sót phần việc còn lại. | Hiếu; người review/kiểm thử nếu có bàn giao | 20 phút để kiểm tra lại figma, jira, commit và merge request |
| 5 | Tốn thời gian | Khi backend phát sinh lỗi trên môi trường test, tôi muốn xác định request và điều kiện gây lỗi, để tìm đúng nguyên nhân mà không phải dò code quá lâu. | Hiếu, người kiểm thử, team dự án | Hiếu ước lượng thời gian tìm nguyên nhân khoảng 30 phút nếu có log và có thể tới 2 giờ nếu không có log; chưa có thống kê nhiều lần. |

**Nếu có dùng AI để gợi ý thêm:** Sau khi nêu công việc daily report, lần trượt estimate do self-test và kinh nghiệm tìm lỗi môi trường test, AI gợi ý #3–#4. Bỏ ý quên ngữ cảnh khi chuyển dự án vì chưa gặp; bỏ ý PM hỏi lại % tiến độ vì trùng #2. 

---

## 3. Top 3 Problem Cards + quy trình nháp (CP2)

### Bảng chọn top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---:|---|---|---|
| 1 | Báo tiến độ trước khi self-test đủ (#2) | Có một lần trượt estimate khoảng 4 giờ sau self-test; phạm vi là thời điểm báo hoàn thành task. | Thứ tự thao tác và thời gian từng bước chưa được xác nhận; chưa rõ tác động cụ thể tới kế hoạch của PM. |
| 2 | Tìm nguyên nhân lỗi trên môi trường test (#5) | Hiếu đã gặp; ước lượng tìm nguyên nhân khoảng 30 phút khi có log, tới 2 giờ khi thiếu log. | Chưa đo từng bước hay so sánh nhiều lỗi tương đương; phải thử cách lấy/ghi log trước. |
| 3 | Daily report theo dự án (#1) | Hiếu thực sự viết cập nhật hằng ngày và gửi PM vào channel Slack của từng dự án. | Chưa có bằng chứng viết report là pain riêng, ngoài lần trượt estimate đã tính ở #2. |

### Problem Card #1 — Báo tiến độ trước khi self-test đủ

| Trường | Nội dung |
|---|---|
| Job Story | Khi sắp báo tiến độ một task backend, tôi muốn biết phần nào đã tự kiểm tra đạt và phần nào chưa, để không báo thời điểm hoàn thành quá sớm. |
| Actor | Hiếu, Junior Backend Developer báo tiến độ task backend cho PM của dự án qua Slack; chưa xác minh PM dùng dự báo này để ra quyết định gì. |
| Thời điểm / bối cảnh | Khi Hiếu báo task sẽ hoàn thành trong buổi sáng, trước khi tự kiểm tra kỹ các màn liên quan. |
| Quy trình hiện tại  | 1. Dev chức năng theo yêu cầu · 2. Ước lượng và báo PM sẽ xong trong buổi sáng · 3. Self-test các màn liên quan và phát hiện lỗi · 4. Sửa lỗi.|
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 2: đánh giá phần việc còn lại trước khi self-test đủ; bản cập nhật ghi khoảng 10 phút nhưng chưa rõ đã bấm giờ hay chỉ ước lượng. Bốn giờ sau self-test là thời gian trượt estimate, không phải thời gian của bước 2. |
| Impact (nếu không giải thì sao) | Nhiều lần báo sẽ xong nhưng không hoàn thành đúng kế hoạch có thể khiến PM estimate trượt. |
| Success metric (baseline → target) | Baseline ban đầu chỉ có 1 lần trượt khoảng 4 giờ; chưa đủ để đặt target đáng tin cậy. Với các task tiếp theo, ghi thời điểm đã hẹn, thời điểm hoàn thành và phần chưa self-test lúc báo; tính số task trượt hẹn và số giờ trượt, rồi mới chốt target. |
| Phương án không dùng AI | Thử checklist các màn/trường hợp phải self-test và ghi rõ phần chưa kiểm trước khi báo giờ hoàn thành; so sánh số task trượt hẹn trước/sau. Chưa biết checklist đã đủ hay chưa. |
| Giả thuyết về AI (nếu có) | AI tạo checklist cả dev và test cùng thời gian estimate để đánh giá cho chính xác khối lượng công việc |
| Cảm nhận nhanh | Workflow|

Quy trình nháp của lần đã kể (thời gian mỗi bước chưa được xác nhận; dấu ? là ước lượng chưa rõ nguồn):

```text
[1 Làm chức năng xuất PDF/Word/Excel: chưa đo]
→ [2 Ước lượng + báo PM xong trong buổi sáng: 10 phút?] ← BƯỚC CẦN KIỂM CHỨNG
→ [3 Self-test các màn, phát hiện lỗi: 30 phút?]
→ [4 Sửa lỗi: chưa đo riêng; hoàn thành trễ khoảng 4 giờ so với dự báo]
```

### Problem Card #2 — Tìm nguyên nhân lỗi trên môi trường test

| Trường | Nội dung |
|---|---|
| Job Story | Khi backend phát sinh lỗi trên môi trường test, tôi muốn xác định request và điều kiện gây lỗi, để tìm đúng nguyên nhân mà không phải dò code quá lâu. |
| Actor | Hiếu, Junior Backend Developer trực tiếp điều tra lỗi backend trên môi trường test; chưa xác minh người nào chờ kết quả. |
| Thời điểm / bối cảnh | Khi Hiếu gặp lỗi backend trên môi trường test, đặc biệt trường hợp không có log để tra cứu. |
| Quy trình hiện tại | 1. Gặp lỗi trên môi trường test · 2. Kiểm tra có log không · 3. Nếu có log thì đọc log, nếu không thì đọc code · 4. Xác định nguyên nhân. Chưa xác nhận cách tái hiện lỗi hoặc bước sửa/kiểm lại nên không tính vào thời gian tìm nguyên nhân. |
| Bottleneck (bước nào, mất bao nhiêu phút) | Bước 3: đọc code để lần dấu vết khi thiếu log; chưa đo riêng bước này. Toàn bộ quá trình tìm nguyên nhân ước lượng khoảng 30 phút khi có log và tới 2 giờ khi không có log. |
| Impact (nếu không giải thì sao) | Theo ước lượng, trường hợp thiếu log có thể tốn thêm tới khoảng 1 giờ 30 phút so với trường hợp có log; hai tình huống chưa được so sánh trên lỗi tương đương. |
| Success metric (baseline → target) | Baseline tham khảo: ước lượng khoảng 30 phút khi có log, tới 2 giờ khi không có log. Chưa có target đã kiểm chứng; đo từ lúc bắt đầu điều tra tới lúc xác định nguyên nhân cho từng lỗi, ghi có/không có log và loại lỗi; chỉ đặt target sau khi có nhiều mẫu. |
| Phương án không dùng AI | Thử đảm bảo log cần thiết có thể truy cập ở môi trường test và ghi lại request/điều kiện tái hiện; đo xem thời gian điều tra có giảm không. Cần xem chính sách ghi log dữ liệu dự án. |
| Giả thuyết về AI (nếu có) | Chưa có bằng chứng cần AI; vấn đề thiếu log có thể cần sửa quy trình/khả năng quan sát trước. |
| Cảm nhận nhanh | Rule đảm bảo ghi log đầy đủ rõ ràng để dễ bắt lỗi và sửa hơn. |

Quy trình nháp hiện tại:

```text
[1 Gặp lỗi trên môi trường test: chưa đo] → [2 Kiểm tra có log: chưa đo]
→ [3 Có log: đọc log / thiếu log: đọc code: chưa đo] ← BƯỚC NGHẼN KHI THIẾU LOG
→ [4 Xác định nguyên nhân: chưa đo]
Tổng thời gian tìm nguyên nhân theo ước lượng: có log khoảng 30 phút; thiếu log có thể tới 2 giờ.
```

### Problem Card #3 — Daily report cho PM theo dự án

| Trường | Nội dung |
|---|---|
| Job Story | Khi đến giờ báo cáo công việc hằng ngày cho từng dự án, tôi muốn nhớ đúng việc đã làm và phần còn vướng, để PM nhận được cập nhật đúng trong channel Slack tương ứng. |
| Actor | Hiếu, Junior Backend Developer viết daily report cho PM trong channel Slack của từng dự án mình tham gia. |
| Thời điểm / bối cảnh | Khi đến giờ cập nhật công việc trong ngày theo từng dự án. |
| Quy trình hiện tại (3–7 bước) | Nháp tối thiểu theo lời Hiếu: 1. Nhớ lại việc đã làm trong ngày · 2. Viết nội dung cho từng dự án · 3. Gửi vào channel Slack tương ứng. Chưa có bằng chứng Hiếu đối chiếu Jira/GitLab trước khi gửi. |
| Bottleneck (bước nào, mất bao nhiêu phút) | Giả thuyết ở bước 1 (nhớ lại việc trong ngày); bản cập nhật ghi 5 phút nhưng chưa xác nhận đã đo. Chưa biết bước này có thực sự gây chậm/sai không; không lấy lần trượt estimate của Card #1 làm bằng chứng cho card này. |
| Impact (nếu không giải thì sao) | Chưa ghi nhận report sai, PM phải hỏi lại hoặc mất nhiều thời gian; có thể chỉ là công việc thường ngày chứ chưa phải pain đáng giải. |
| Success metric (baseline → target) | Chưa có baseline đáng tin cậy hoặc target; bấm giờ riêng bước nhớ lại và toàn bộ report trong những ngày tiếp theo, ghi số lần phải sửa/đính chính, rồi mới chọn target nếu phát hiện pain. |
| Phương án không dùng AI | Chỉ nếu đo được pain: thử mẫu cập nhật ngắn theo dự án; so sánh thời gian và số lần đính chính trước/sau. |
| Giả thuyết về AI (nếu có) | Thêm một generate report dựa trên work trên jira hoặc commit/pull request |
| Cảm nhận nhanh | No AI |

Quy trình nháp hiện tại:

```text
[1 Nhớ việc trong ngày: 5 phút?] ← BƯỚC NGHẼN GIẢ THUYẾT
→ [2 Viết update theo dự án: 10 phút]
→ [3 Gửi vào channel Slack tương ứng: 5 phút]
Chưa có bằng chứng bước 1 làm report chậm hoặc sai.
```

### Card muốn pitch nhất

- Card số: #1 (đề xuất để Hiếu tự quyết sau khi đối chiếu nhóm).
- Vì sao: có một sự kiện cụ thể trượt estimate khoảng 4 giờ sau self-test; không phải vì mất thời gian viết daily report.
- Câu hỏi muốn nhóm phản biện: “Nếu liệt kê phần chưa self-test trước khi báo PM thì đã đủ giảm trượt estimate, hay còn nguyên nhân nào khác?”

### AI đã phản biện card thế nào

| Điểm yếu AI chỉ ra | Đồng ý? | Đã sửa gì |
|---|---|---|
| Lúc đầu tách “estimate sai” và “self-test chưa đủ” thành hai problem dù cùng một chuỗi nguyên nhân–hậu quả. | Hiếu đồng ý gộp. | Gộp thành CP1 #2 và Card #1; không nhân đôi một bằng chứng 4 giờ. |
| “Viết daily report” có thể không phải bottleneck; lần trượt estimate xảy ra vì self-test phát hiện lỗi sau khi đã báo. | Cần kiểm chứng thêm. | Tách daily report thành Card #3 và không gán 4 giờ trượt estimate cho thời gian viết báo cáo. |

---

## 4. Tôi đã tham gia phần nào (CP3 → CP7)

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng tới bài nhóm |
|---|---|---|
| Pitch Problem Card | | |
| Phản biện bài của bạn khác | Câu hỏi tôi đã đặt: | |
| Nhận phản biện | Câu hỏi tôi nhận được: | Tôi đã sửa gì: |
| Gom cluster / cây OST | | |
| Chọn candidate problem | | |
| Kiểm chứng / research | | |
| Quy trình nhóm | | |
| Problem Statement | | |
| Mức can thiệp AI | | |
| Quyết định | | |

---

## 5. Dùng AI

| Checkpoint | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai hoặc hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| CP1 Scan | Gợi ý Job Story theo công việc backend và rà soát trùng lặp. | Gợi ý candidate về tìm lỗi môi trường test; Hiếu xác nhận đã gặp. | Gợi ý quên ngữ cảnh chuyển dự án dù Hiếu chưa gặp; gợi ý log work dù Hiếu không muốn theo đuổi. | Bỏ hai ý đó; gộp estimate sai và self-test chưa đủ; giữ #3–#4 ở trạng thái chưa kiểm chứng. |
| CP2 Problem Card | Nhờ phác card và phản biện điểm thiếu bằng chứng. | Nhận ra lần trượt estimate 4 giờ chỉ là một sự kiện, chưa đủ baseline tổng quát. | Bản cập nhật chứa thời gian từng bước chưa rõ nguồn; chưa có target cho các card. | Chốt ước lượng tìm lỗi 30 phút/2 giờ, phân biệt thời gian tìm nguyên nhân với thời gian sửa; cần đo lại từng bước trước khi nộp. |
| CP4 Research | | | | |
| CP5 Quy trình | | | | |
| CP5–6 Problem Statement | | | | |
| CP6 Mức can thiệp / quyết định | | | | |

---

## 6. Reflection (CP7)

Trả lời bằng trải nghiệm thật của bạn, tối thiểu 200 từ cho các câu 6.1–6.6 (không tính 6.7, câu này được chấm riêng ở tiêu chí C5). **Không dùng AI để viết thay.**

**6.1. Tôi học được gì khi nghe top 3 problems của các bạn khác?**

**6.2. Nhóm có lúc nào bị "solution-first" (nghĩ giải pháp trước khi hiểu vấn đề) không? Lúc đó nhóm nhận ra và xử lý thế nào?**

**6.3. Tôi có đổi ý sau khi bị phản biện không? Kể một lần cụ thể.**

**6.4. Kết quả kiểm chứng (phỏng vấn/survey/research) có làm tôi bất ngờ không? Điều gì?**

**6.5. Điều khó nhất khi viết Problem Statement là gì?**

**6.6. Nếu làm lại, tôi sẽ đổi gì? Tôi sẽ phản biện nhóm mạnh hơn ở điểm nào?**

**6.7. Hiểu bài:** giải thích bằng 5–8 câu, không nhìn tài liệu, chuỗi *problem → quy trình → metric → boundary → mức can thiệp AI → quyết định* của bài nhóm mình.

---

## 7. Tài liệu tham khảo

-
