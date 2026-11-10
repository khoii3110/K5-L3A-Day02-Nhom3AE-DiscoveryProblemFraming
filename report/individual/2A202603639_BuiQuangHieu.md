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
| Pitch Problem Card | Nhận phụ trách trình bày 3 card cá nhân: báo tiến độ trước khi self-test đủ, tìm nguyên nhân lỗi ở môi trường test và daily report theo dự án. Chưa ghi nhận buổi pitch thực tế. | Ba card đã có ở mục 3 để trình bày; sau buổi pitch cần ghi câu hỏi phản biện thực nhận và tác động tới lựa chọn nhóm. |
| Phản biện bài của bạn khác | Câu hỏi tôi đã đặt: | |
| Nhận phản biện | Câu hỏi tôi nhận được: | Tôi đã sửa gì: |
| Gom cluster / cây OST | Nhận phụ trách rà soát cách gom candidate và cây OST tại `report/team/group_report.md` mục 2.2–2.3; cần tự kiểm lại với các thành viên trước khi ghi là đóng góp đã thực hiện. | Bản nhóm hiện có 3 cluster và cây OST cho problem kiểm thử hồi quy; chưa có ghi nhận cá nhân về phần Hiếu trực tiếp trình bày/chỉnh sửa. |
| Chọn candidate problem | Nhận phụ trách giải thích bảng chấm điểm và lý do chọn/loại tại `report/team/group_report.md` mục 2.4; chưa có ghi nhận riêng về phần Hiếu trực tiếp chấm hoặc phản biện trong buổi nhóm. | Bảng nhóm ghi candidate #4 của Đăng đạt 34/35 và được nhóm chốt; cần bổ sung đóng góp cụ thể của Hiếu nếu có. |
| Kiểm chứng / research | | |
| Quy trình nhóm | | |
| Problem Statement | Nhận phụ trách đối chiếu Problem Statement v0/v1 tại `report/team/group_report.md` mục 5 và 7 với candidate nhóm chọn; đã yêu cầu thống nhất mốc 120 phút/lần, bottleneck kiểm thử thủ công 50 phút và giữ quyết định Not Yet. Nội dung báo cáo có AI hỗ trợ, cần nhóm tự rà soát và chốt. | v0/v1 hiện giữ cùng bottleneck; bước chọn case chỉ là giả thuyết phụ, không được coi là pain đã kiểm chứng. |
| Mức can thiệp AI | | |
| Quyết định | | |

---

## 5. Dùng AI

| Checkpoint | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai hoặc hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| CP1 Scan | Gợi ý Job Story theo công việc backend và rà soát trùng lặp. | Gợi ý candidate về tìm lỗi môi trường test; Hiếu xác nhận đã gặp. | Gợi ý quên ngữ cảnh chuyển dự án dù Hiếu chưa gặp; gợi ý log work dù Hiếu không muốn theo đuổi. | Bỏ hai ý đó; gộp estimate sai và self-test chưa đủ; giữ #3–#4 ở trạng thái chưa kiểm chứng. |
| CP2 Problem Card | Nhờ phác card và phản biện điểm thiếu bằng chứng. | Nhận ra lần trượt estimate 4 giờ chỉ là một sự kiện, chưa đủ baseline tổng quát. | Bản cập nhật chứa thời gian từng bước chưa rõ nguồn; chưa có target cho các card. | Chốt ước lượng tìm lỗi 30 phút/2 giờ, phân biệt thời gian tìm nguyên nhân với thời gian sửa; cần đo lại từng bước trước khi nộp. |
| CP4 Research | Nhờ AI rà soát phần bằng chứng và research đã có trong báo cáo nhóm; chưa tự mở và kiểm các link nguồn. | Phân biệt lời kể của thành viên với phỏng vấn độc lập, nhận ra chưa có log bấm giờ hoặc phỏng vấn hợp lệ. | Không thể dùng lời kể trong nhóm thay cho phỏng vấn CP4, cũng không thể xem danh sách công cụ là bằng chứng pain đã được xác nhận. | Giữ CP4 ở trạng thái chưa kiểm chứng và kết luận Not Yet; cần tự kiểm link và bổ sung kiểm chứng từ người ngoài nhóm nếu làm tiếp. |
| CP5 Quy trình | Nhờ AI đối chiếu quy trình hiện tại của nhóm với Problem Card của Đăng. | Phát hiện kịch bản 85 phút trong báo cáo nhóm không khớp tổng 120 phút của báo cáo cá nhân. | Bản nháp đã tự phân bổ thời gian từng bước, làm lệch bottleneck được nêu ở CP2. | Yêu cầu giữ 120 phút/lần, trong đó 50 phút là bước kiểm thử thủ công; vẫn ghi rõ các mốc theo lời kể, chưa bấm giờ độc lập. |
| CP5–6 Problem Statement | Nhờ AI rà mâu thuẫn giữa v0 và v1 của nhóm. | Chỉ ra v1 đã chuyển bottleneck từ chạy kiểm thử thủ công sang chọn case dù chưa có bằng chứng. | AI có thể biến giả thuyết phụ thành vấn đề đã được xác nhận. | Yêu cầu v0 và v1 cùng giữ bottleneck kiểm thử thủ công 50/120 phút; chỉ ghi khó chọn case là giả thuyết cần kiểm chứng. |
| CP6 Mức can thiệp / quyết định | Nhờ AI kiểm tra sự nhất quán giữa phương án thử AI, baseline không AI và quyết định cuối. | Làm rõ cần so sánh checklist, Rule/CI và Workflow có AI trước khi kết luận AI có giá trị tăng thêm. | Đề xuất Workflow có thể bị hiểu nhầm là đã đủ điều kiện triển khai dù thiếu phỏng vấn và chưa rõ quyền dùng source code. | Giữ quyết định Not Yet; chỉ xem Workflow có AI là phương án thử trên repo mẫu, không coi là giải pháp đã được chứng minh. |

---

## 6. Reflection (CP7)

Trả lời bằng trải nghiệm thật của bạn, tối thiểu 200 từ cho các câu 6.1–6.6 (không tính 6.7, câu này được chấm riêng ở tiêu chí C5). **Không dùng AI để viết thay.**

**6.1. Tôi học được gì khi nghe top 3 problems của các bạn khác?**
Cần chọn vấn đề có ví dụ thực tế thay vì chỉ chọn ý tưởng nghe hay.
**6.2. Nhóm có lúc nào bị "solution-first" (nghĩ giải pháp trước khi hiểu vấn đề) không? Lúc đó nhóm nhận ra và xử lý thế nào?**
Sau khi xem xét, nhóm nhận thấy cần hiểu rõ quy trình kiểm thử hiện tại và xem các công cụ thông thường đã giải quyết được đến đâu.
**6.3. Tôi có đổi ý sau khi bị phản biện không? Kể một lần cụ thể.**
Ban đầu tôi nghĩ cần AI hỗ trợ ước lượng, nhưng sau khi xem xét lại, checklist kiểm thử cũng có thể giúp tránh báo hoàn thành quá sớm.
**6.4. Kết quả kiểm chứng (phỏng vấn/survey/research) có làm tôi bất ngờ không? Điều gì?**
Nhóm vẫn cần kiểm chứng xem AI có thực sự giúp tiết kiệm thời gian hơn không.
**6.5. Điều khó nhất khi viết Problem Statement là gì?**
Khó nhất là xác định đúng vấn đề chính và đưa ra số liệu cụ thể. Nhóm có một số ước lượng về thời gian, nhưng chưa đủ dữ liệu thực tế để khẳng định mức độ ảnh hưởng.
**6.6. Nếu làm lại, tôi sẽ đổi gì? Tôi sẽ phản biện nhóm mạnh hơn ở điểm nào?**
Ghi lại thời gian làm việc và kiểm thử ngay từ đầu.
Hỏi thêm developer hoặc tester về những lỗi thường gặp.
Phản biện kỹ hơn xem vấn đề có thật sự cần AI hay chỉ cần cải thiện quy trình.
**6.7. Hiểu bài:** giải thích bằng 5–8 câu, không nhìn tài liệu, chuỗi *problem → quy trình → metric → boundary → mức can thiệp AI → quyết định* của bài nhóm mình.
Bạn có thể tự viết 5–8 câu theo mạch sau:

Problem: Kiểm tra chức năng cũ sau khi sửa code mất nhiều thời gian.

Quy trình: Developer sửa code, tự kiểm thử rồi bàn giao cho tester.

Metric: Thời gian kiểm thử và số lỗi bị bỏ sót.

Boundary: AI chỉ hỗ trợ gợi ý test case, developer vẫn kiểm tra và quyết định.

Mức can thiệp: Workflow kết hợp công cụ kiểm thử tự động và AI.

Quyết định: Not Yet vì chưa có đủ bằng chứng cho thấy AI hiệu quả hơn cách kiểm thử thông thường.

---

## 7. Tài liệu tham khảo

- [Worksheet — hướng dẫn từng checkpoint](../../docs/01-worksheet.md): format Job Story, Problem Card và phản biện.
- [Bài làm mẫu](../../docs/02-deliverable-example.md): tham khảo cách trình bày CP1–CP2, không sao chép số liệu.
- [Báo cáo nhóm](../team/group_report.md): đối chiếu candidate #4, quy trình, Problem Statement và quyết định Not Yet.
- [Báo cáo cá nhân của Nguyễn Văn Đăng](2A202603371_NguyenVanDang.md): nguồn nội bộ của mốc 120 phút/lần và bước kiểm thử 50 phút; chưa phải kiểm chứng độc lập.
