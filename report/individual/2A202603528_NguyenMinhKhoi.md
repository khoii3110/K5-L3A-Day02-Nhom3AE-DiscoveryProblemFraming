# BÁO CÁO CÁ NHÂN

##  Thông tin học viên

- Họ tên: Nguyễn Minh Khôi
- MSSV:2A202603528
- Email trường (không bắt buộc, repo có thể để public): 26ai.khoinm2@vinuni.edu.vn
- Tên nhóm: Nhom3AE
- Link repo nhóm: https://github.com/khoii3110/K5-L3A-Day02-Nhom3AE-DiscoveryProblemFraming/tree/main

# CP1 — Scan vấn đề (Discover)

## 1. Bối cảnh

- **Vai trò:** Người học/lập trình viên đang thực hành xây dựng AI Tool Calling Agent bằng Python.
- **Bài toán đang làm:** Xây dựng agent hỗ trợ khách hàng VinFast, có khả năng trả lời câu hỏi thường gặp và tạo ticket khi khách hàng báo sự cố cần xử lý.
- **Phạm vi quan sát:** Quy trình xử lý yêu cầu hỗ trợ trong bài lab; chưa đại diện cho toàn bộ quy trình chăm sóc khách hàng thực tế của VinFast.

## 2. Problem được chọn

| Trường | Nội dung |
|---|---|
| **Lăng kính** | Cần đọc, phân loại và xử lý thông tin |
| **Job Story** | Khi khách hàng gửi một yêu cầu hỗ trợ về xe, tôi muốn xác định đúng yêu cầu đó chỉ cần được giải đáp bằng thông tin có sẵn hay cần tạo ticket cho nhân viên hỗ trợ, để khách hàng nhận được đúng cách xử lý mà không phải thực hiện lại nhiều lần. |
| **Actor** | Khách hàng VinFast gửi yêu cầu hỗ trợ; nhân viên chăm sóc khách hàng là người tiếp nhận và xử lý các trường hợp cần can thiệp. |
| **Bối cảnh cụ thể** | Khách hàng có thể hỏi chính sách bảo hành pin xe điện hoặc mô tả lỗi nghiêm trọng như hệ thống ADAS trên VF 8. Hai loại yêu cầu này cần cách xử lý khác nhau: câu hỏi FAQ có thể trả lời trực tiếp; sự cố cần ghi nhận thông tin và tạo ticket. |
| **Quy trình hiện tại trong bài lab** | 1. Nhận nội dung khách hàng gửi. 2. Đọc và xác định ý định. 3. Phân biệt câu hỏi kiến thức với yêu cầu cần xử lý. 4. Nếu là FAQ, tra cứu thông tin và trả lời. 5. Nếu là sự cố cần hỗ trợ, thu thập thông tin và gọi tool tạo ticket. 6. Trả kết quả cho khách hàng. |
| **Bước nghẽn / rủi ro** | Phân loại sai ý định hoặc chọn sai hành động: gọi tool khi chỉ cần trả lời FAQ, hoặc không tạo ticket khi khách hàng báo sự cố cần xử lý. |
| **Impact** | Phân loại sai có thể khiến khách hàng không nhận được câu trả lời phù hợp, ticket bị tạo không cần thiết hoặc sự cố không được chuyển tới bộ phận xử lý. |
| **Dấu hiệu có thể quan sát** | Trong bài lab có ít nhất hai tình huống kiểm thử khác loại: (1) hỏi thời hạn bảo hành pin — cần trả lời FAQ, không gọi tool; (2) báo lỗi ADAS nghiêm trọng trên VF 8 — cần tạo ticket. Kết quả được kiểm tra qua `status`, `iterations`, nội dung phản hồi và số lần tool được gọi. |
| **Metric đề xuất** | Tỷ lệ phân loại đúng trên bộ test; tỷ lệ gọi tool đúng; tỷ lệ bỏ sót yêu cầu cần tạo ticket; tỷ lệ gọi tool thừa với câu hỏi FAQ. |
| **Phương án không dùng AI** | Dùng bộ quy tắc/keyword cố định để phân loại FAQ và sự cố. Cách này phù hợp với các intent ít và rõ ràng, nhưng có thể kém linh hoạt khi khách hàng diễn đạt đa dạng. |
| **Giả thuyết về AI** | LLM phân tích ngữ cảnh và ý định của khách hàng, sau đó chọn trả lời trực tiếp hoặc gọi tool phù hợp. |
| **Cảm nhận ban đầu** | Workflow có LLM phân loại ý định và chọn hành động; chưa có căn cứ để cần Agent tự do lập kế hoạch nhiều bước. |

## 3. Quy trình hiện tại — bản nháp

```text
[Khách hàng gửi yêu cầu]
          |
          v
[Agent đọc nội dung]
          |
          v
[Phân loại ý định]
     /          \
    /            \
   v              v
[FAQ]        [Báo sự cố]
   |              |
   v              v
[Tra cứu       [Thu thập thông tin]
kiến thức]        |
   |              v
   |          [Gọi tool tạo ticket]
   |              |
   v              v
[Trả lời khách hàng]
```

## 4. Cách đo trong bài lab

| Test case | Kết quả mong đợi | Chỉ số cần kiểm tra |
|---|---|---|
| “Chính sách bảo hành pin xe điện VinFast kéo dài bao lâu?” | Agent trả lời từ FAQ, không gọi tool | `status = completed`, số lần gọi tool = 0, câu trả lời có thông tin bảo hành |
| “Tôi tên Lê Minh Khoa, xe VF 8 của tôi bị lỗi hệ thống ADAS. Đây là vấn đề nghiêm trọng, cần xử lý gấp.” | Agent tạo ticket và phản hồi kết quả | `status = completed`, tool tạo ticket được gọi đúng một lần, thông tin khách hàng/sự cố được truyền đúng |


# CP2 — Problem Card và quy trình nháp (Discover)

## 1. Problem Card

### PROBLEM CARD #1 — Phân loại yêu cầu khách hàng và chọn hành động xử lý

| Trường | Nội dung |
|---|---|
| **Job Story** | Khi khách hàng gửi một yêu cầu hỗ trợ về xe, tôi muốn xác định đúng yêu cầu đó chỉ cần được giải đáp bằng thông tin có sẵn hay cần tạo ticket cho nhân viên hỗ trợ, để khách hàng nhận được đúng cách xử lý. |
| **Actor chịu ảnh hưởng** | Khách hàng VinFast; nhân viên chăm sóc khách hàng tiếp nhận các trường hợp cần xử lý. |
| **Quy trình** | Nhận yêu cầu → đọc nội dung → phân loại FAQ/sự cố → trả lời FAQ hoặc tạo ticket → phản hồi khách hàng. |
| **Bước nghẽn** | Phân loại ý định và quyết định có gọi tool hay không. |
| **Thời gian** | Chưa có dữ liệu vận hành để xác định thời gian xử lý trung bình. Trong phạm vi lab, đo thời gian từ lúc gửi input đến khi agent trả kết quả; ghi riêng thời gian xử lý và số vòng lặp. |
| **Impact** | Gọi tool thừa làm phát sinh ticket không cần thiết; bỏ sót tool tạo ticket khiến sự cố không được chuyển xử lý; trả lời FAQ sai làm giảm độ tin cậy. |
| **Đo thành công** | Tăng tỷ lệ phân loại đúng; giảm gọi tool thừa; không bỏ sót tình huống cần tạo ticket. |
| **Cảm nhận ban đầu** | Workflow có LLM phân loại intent, kết hợp rule kiểm tra điều kiện gọi tool và người phụ trách xử lý ticket. |

## 2. Quy trình hiện tại chi tiết

```text
(1) Khách hàng gửi yêu cầu
        |
        v
(2) Agent nhận và đọc nội dung
        |
        v
(3) Xác định intent
        |
        +-----------------------------+
        |                             |
        v                             v
(4A) Câu hỏi FAQ                 (4B) Báo sự cố
        |                             |
        v                             v
(5A) Tra cứu thông tin           (5B) Trích xuất tên,
        |                            mô tả lỗi, mức độ ưu tiên
        v                             |
(6A) Soạn câu trả lời                 v
        |                        (6B) Gọi submit_support_ticket
        |                             |
        +--------------+--------------+
                       |
                       v
              (7) Phản hồi khách hàng
```

## 3. Điểm nghẽn và giả thuyết

**Điểm nghẽn chính:** Agent phải phân biệt yêu cầu cung cấp thông tin với yêu cầu cần hành động. Việc nhận diện từ khóa đơn thuần có thể không đủ khi khách hàng diễn đạt gián tiếp, dùng nhiều ý trong cùng một câu hoặc mô tả mức độ nghiêm trọng không rõ ràng.

**Giả thuyết cần kiểm chứng:**

1. LLM có thể phân loại intent dựa trên ngữ cảnh tốt hơn một bộ keyword cố định.
2. Bộ rule có thể kiểm tra các điều kiện rõ ràng như thông tin khách hàng, loại tool và mức ưu tiên.
3. Chỉ cần workflow có các bước cố định; chưa cần Agent tự quyết định và lặp nhiều bước.
4. Mọi hành động tạo ticket phải dựa trên kết quả tool thực tế, không được suy diễn rằng ticket đã được tạo thành công.

## 4. Metric và cách kiểm thử

| Metric | Cách tính / kiểm tra |
|---|---|
| **Intent accuracy** | Số input được phân loại đúng / tổng số input có nhãn chuẩn. |
| **Tool precision** | Số lần gọi tool đúng / tổng số lần gọi tool. |
| **Tool recall** | Số yêu cầu cần gọi tool được xử lý bằng tool / tổng số yêu cầu thực sự cần gọi tool. |
| **Unnecessary tool-call rate** | Số FAQ bị gọi tool / tổng số FAQ. |
| **Missed ticket rate** | Số yêu cầu cần tạo ticket nhưng không gọi tool / tổng số yêu cầu cần tạo ticket. |
| **Execution success rate** | Số lần tool thực thi thành công / tổng số lần gọi tool. |

Không tự đặt baseline hoặc target khi chưa chạy bộ test đủ lớn. Hai test case mẫu chỉ xác nhận hai luồng cơ bản, chưa đủ để đánh giá độ chính xác tổng quát.

## 5. Phản biện Problem Card

| Câu hỏi phản biện | Đánh giá hiện tại |
|---|---|
| Actor đã đủ cụ thể chưa? | Khá cụ thể trong bối cảnh lab: khách hàng gửi yêu cầu và nhân viên hỗ trợ tiếp nhận ticket. Cần xác minh vai trò thực tế trong quy trình VinFast nếu mở rộng ra ngoài lab. |
| Quy trình có quan sát được không? | Có thể quan sát qua input, trace, tool call và final answer của agent. |
| Bottleneck có phải một bước cụ thể không? | Có: phân loại intent và chọn hành động. |
| Metric có đo được không? | Đo được trên bộ test có nhãn chuẩn; chưa có dữ liệu khách hàng thật. |
| Rule có thể giải quyết đủ không? | Có thể với intent rõ và ít biến thể; cần thử trên câu diễn đạt đa dạng trước khi kết luận. |
| Có đang nhảy sang AI quá sớm không? | Có rủi ro. Cần so sánh keyword/rule baseline với LLM workflow trên cùng bộ test. |

## 6. Kết luận CP2

Problem Card tập trung vào một vấn đề duy nhất: **phân loại đúng yêu cầu khách hàng để chọn giữa trả lời FAQ và tạo ticket**.

Hướng thử nghiệm phù hợp là so sánh ba phương án trên cùng bộ test:

- **No AI:** Nhân viên đọc và xử lý thủ công theo hướng dẫn.
- **Rule:** Dùng keyword/điều kiện cố định để phân loại và chọn tool.
- **Workflow có LLM:** LLM phân tích intent; rule xác thực điều kiện; tool chỉ được gọi khi phù hợp.

Chưa có căn cứ chọn Agent tự chủ vì quy trình và các hành động cần thực hiện đã xác định trước.

---

# CP7 — Reflection cá nhân

**6.1. Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Mỗi vấn đề có nhiều góc nhìn và cần đánh giá dựa trên mức độ ảnh hưởng, tần suất và bằng chứng thực tế.

**6.2. Nhóm có lúc nào bị solution-first không?**

Có. Nhóm ban đầu nghĩ ngay đến Chatbot hoặc Agent. Sau đó, chúng tôi tập trung xác định pain point trước khi chọn giải pháp.

**6.3. Tôi có đổi ý sau khi bị phản biện không?**

Có. Ban đầu tôi nghĩ cần Agent, nhưng sau khi phân tích, tôi nhận thấy LLM kết hợp rule có thể xử lý workflow cố định đơn giản và hiệu quả hơn.

**6.4. Kết quả kiểm chứng có làm tôi bất ngờ không?**

Có. FAQ và lỗi ADAS cần hai hướng xử lý khác nhau dù đều dùng ngôn ngữ tự nhiên. Tuy nhiên, hai test case chưa đủ để đánh giá thực tế.

**6.5. Điều khó nhất khi viết Problem Statement là gì?**

Khó nhất là xác định đúng vấn đề và chọn metric cụ thể thay vì những mục tiêu chung chung như cải thiện trải nghiệm.

**6.6. Nếu làm lại, tôi sẽ đổi gì?**

Tôi sẽ tìm hiểu người dùng kỹ hơn, bổ sung test case và phản biện mạnh hơn về bằng chứng, bottleneck và sự cần thiết của AI.

**6.7. Hiểu bài**

Nhóm giải quyết bài toán phân loại yêu cầu hỗ trợ VinFast thành FAQ và sự cố cần tạo ticket. Workflow gồm phân loại intent và chọn hướng xử lý. Metric chính gồm Intent Accuracy, Tool Precision và Tool Recall. Giải pháp dự kiến kết hợp LLM và rule. Tuy nhiên, cần kiểm thử và so sánh với rule-based trước khi kết luận hiệu quả.