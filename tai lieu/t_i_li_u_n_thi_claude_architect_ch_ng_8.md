# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL

## Chương 8: Prompts as Architecture (Prompt Dưới Góc Độ Kiến Trúc)

### I. TÓM TẮT CỐT LÕI (CORE SUMMARY)
Trong môi trường Enterprise, Prompt không phải là một đoạn văn bản để "múa phím". Nó là một **thành phần kiến trúc** thực thụ (có bộ nhớ đệm cache, có phiên bản, có thứ tự và có quy tắc thất bại). 
Thay vì cố gắng "dụ dỗ" model bằng từ ngữ, bạn phải dùng **cấu trúc, vị trí** và **hiểu rõ cơ chế của API** để điều khiển nó.

---

### II. KIẾN THỨC TRỌNG TÂM & BẪY KỸ THUẬT (RẤT DỄ THI)

#### 1. Xử Lý Mâu Thuẫn Trong Prompt (Contradictions)
* 🚨 **Quy tắc vàng:** Khi có 2 lệnh mâu thuẫn trong prompt, cách giải quyết DUY NHẤT đúng là **XÓA BỎ (Remove)** mâu thuẫn đó. 
* *Bẫy (Anti-pattern):* Cố gắng "phân xử" (arbitrate) bằng cách: Thêm lệnh ưu tiên, bôi đậm, hay hạ `temperature`. Việc này giữ lại cả 2 lệnh và giao việc hòa giải cho model (điều mà chính con người còn đang bối rối).

#### 2. Vị Trí và Sự Phân Cách (Position & Separation)
* Nếu model bỏ qua một luật trong prompt dài, đòn bẩy duy nhất là **Vị trí của luật đó** và **Sự phân cách cấu trúc** (ví dụ: bọc trong XML tags `<example>`).
* *Bẫy:* Lặp lại luật nhiều lần, viết HOA, hay chỉnh temperature KHÔNG giải quyết được việc instruction bị kẹt giữa một mớ hỗn độn.

#### 3. Các Thay Đổi Ngầm Theo Phiên Bản Model (Cực Kỳ Quan Trọng)
Đề thi sẽ gài bẫy bằng cách cho bạn một technique cũ áp dụng lên model mới:
* **Opus 4.5 & 4.6:** Rất nhạy cảm với System Prompt. Nếu dùng từ ngữ đe dọa/thúc ép như *"CRITICAL: You MUST use this tool"*, tool sẽ bị kích hoạt **quá mức (overtrigger)**. Hãy dùng ngôn ngữ bình thường.
* **Opus 5 & Tham số `Effort`:** Tham số Effort kiểm soát **lượng suy nghĩ (thinking)**, KHÔNG kiểm soát **độ dài câu trả lời (length)**. Việc hạ `effort` xuống không làm câu trả lời ngắn đi. Muốn ngắn, phải ra lệnh trực tiếp bằng prompt.
* 🚨 **CÚ LỪA PREFILL:** Từ phiên bản **Claude 4.6 và Mythos Preview**, việc mớm lời (Prefill) vào lượt trợ lý (Assistant turn) **KHÔNG CÒN ĐƯỢC HỖ TRỢ** và sẽ trả về lỗi `400 Error`. (Cho dù có tài liệu cũ khuyên dùng, thì API Constraint vẫn là luật cao nhất).

#### 4. Structured Outputs (JSON Schema)
* **Ký tự Hoa/Thường (Capitalisation):** Output trả về Enum KHÔNG được bảo đảm đúng chữ hoa/thường theo schema (ví dụ bạn quy định `Yes` nó có thể trả về `yes`). Hệ thống không coi đó là lỗi.
* *Cách giải quyết:* Compare code ở dạng **case-insensitive** (không phân biệt hoa/thường) và KHÔNG BAO GIỜ đặt 2 giá trị Enum chỉ khác nhau mỗi viết hoa/viết thường.

#### 5. Phòng Chống Prompt Injection (Untrusted Content)
* **Quy tắc:** Mọi dữ liệu từ người dùng/bên thứ 3 (untrusted data) PHẢI được nhét vào trong **Tool result blocks** và được **JSON-encode**. Model được huấn luyện để "cảnh giác" với nội dung trong block này.
* 🚨 **Bẫy:** Đừng bao giờ nhét instruction (mệnh lệnh) CỦA BẠN vào Tool result block, vì model sẽ coi lệnh của bạn là rác/untrusted và lờ nó đi.

#### 6. Cơ Chế Prompt Caching (Rất hay ra bài tập tình huống)
Caching tiết kiệm chi phí rất lớn, nhưng rất dễ vỡ.
* **Thứ tự Caching:** `Tools` $\rightarrow$ `System` $\rightarrow$ `Messages`.
  * *Hệ quả (Bẫy thi):* Chỉ cần bạn đổi 1 dấu phẩy trong khai báo Tool, **TOÀN BỘ CACHE bị vỡ** (kể cả System và Messages phía sau).
* **Vị trí Breakpoint:** Cache băm (hash) toàn bộ nội dung *cộng dồn* từ đầu đến breakpoint. Nếu bạn để một cái biến (như Timestamp, Request ID) ở đầu System Prompt $\rightarrow$ Toàn bộ cache bị vô hiệu hóa.
* **Thời gian sống (Lifetime):** Mặc định **5 phút** (miễn phí refresh khi dùng lại). Có thể mua gói **1 giờ** với giá input viết cache gấp đôi (2x base input price) $\rightarrow$ Chỉ dùng khi các request cách nhau > 5 phút và prefix cực lớn.
* **Diagnostic Cache Miss (Bắt mạch lỗi cache):** Nếu cache tịt (read tokens = 0) mà không hiểu tại sao. Hãy truyền `previous_response_id` vào request mới. 
  * Trường `diagnostics`: Báo cho biết request đã thay đổi ở đâu.
  * Trường `usage`: Báo cache hit hay không.

#### 7. Đóng Gói Prompt (Agent Skills)
* **Versioning (Phiên bản):** Khi đưa lên Production, BẮT BUỘC phải ghim (pin) cứng version. Nếu để `latest`, bất kỳ ai up file mới lên sẽ lập tức làm thay đổi Agent đang chạy thật.
* **Snapshot, Không phải Delta:** Khi up version mới, phải upload **Toàn bộ** các file. Những file bị quên sẽ không được copy từ version cũ sang. (Đó là lỗi mất dữ liệu, không phải tính năng).

---

### III. CHEAT SHEET: NHẬN DIỆN BẪY ĐỀ THI CHƯƠNG 8

| Khi tình huống đề cập... (Scenario says) | Đáp án đúng thường là... (Answer is usually) | Bẫy thường gặp... (Trap is usually) |
| :--- | :--- | :--- |
| Có 2 lệnh mâu thuẫn nhau trong 1 prompt | **Viết lại để xóa bỏ 1 lệnh** (chỉ giữ 1). | Đặt quy tắc ưu tiên, bôi đậm, hạ temperature (Cả 2 lệnh vẫn tồn tại). |
| Model 4.5/4.6 gọi một Tool quá nhiều lần | **Giảm bớt từ ngữ mạnh bạo** (Must, Critical) thành ngôn ngữ thường. | Bôi đậm thêm lệnh (sẽ càng làm lỗi nặng hơn). |
| Cần giảm độ dài câu trả lời trên Opus 5 | **Viết thẳng yêu cầu độ dài** vào prompt. | Hạ tham số `effort` (Tham số này chỉ chỉnh độ sâu suy nghĩ). |
| Đề xuất Prefill cho Model 4.6 hoặc Mythos | **Báo lỗi 400 (Không khả dụng)**. | Làm theo vì nghĩ giúp ép format tốt hơn. |
| Enum value trả về sai chữ hoa/chữ thường | **Compare case-insensitively** trong code. | Cố gắng ép schema phải chính xác tuyệt đối. |
| Xử lý dữ liệu không đáng tin (Untrusted content) | Bỏ vào **Tool result blocks (JSON-encoded)** + Khai báo trong System. | Bỏ vào System prompt hoặc User text bình thường. |
| Bạn chỉnh sửa Tool Definitions (Danh sách tool) | **Toàn bộ Cache bị xóa sạch**. | Tin rằng System Cache và Message Cache vẫn sống. |
| System Prompt có gắn Timestamp / Request ID | Chuyển dữ liệu động đó **ra sau Breakpoint** (Vào User message). | Để nó trên đầu và làm hỏng toàn bộ bộ nhớ Cache. |
| Cache miss im lặng (không biết vì sao) | Dùng `previous_response_id` để đọc **first divergence** (điểm sai lệch đầu tiên). | Chỉ biết ngồi đoán vì số token read = 0. |
| Triển khai Skills cho Agent lên Production | **Ghim cứng Version (Pinned version)**. | Để version unpinned hoặc `latest` (ai upload cũng làm thay đổi hệ thống). |
| Upload Skill version mới | Upload **Full toàn bộ file**. | Tưởng là bản Delta nên chỉ upload file bị sửa. |

---

💡 **Thói quen ăn điểm:** Luôn đọc luồng Request từ **Vị trí Số 0 (Đầu tiên) trở đi** để tìm xem chỗ nào thay đổi đầu tiên. Vị trí đó chính là nơi Cache bị bẻ gãy!