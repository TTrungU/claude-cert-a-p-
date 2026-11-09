# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL
## Chương 3: Sizing, Scoping, and the Feasibility Verdict (Định Cỡ, Định Phạm Vi & Phán Quyết Tính Khả Thi)

---

### I. TÓM TẮT CỐT LÕI (CORE SUMMARY)
Chương này giải quyết 2 sai lầm chí mạng ngay từ đầu dự án:
1. **Dự án này có đáng làm không?** Phải xác định đúng loại "Giá trị" (Value Pillar) mà doanh nghiệp thực sự thu được, chứ không chỉ hô hào chung chung.
2. **Dự án này có khả thi không?** Đây là bài toán số học (tính toán dung lượng, chi phí, giới hạn API) có thể làm xong trong một buổi chiều. Đừng biến nó thành một sự mơ hồ chờ đến lúc Discovery mới giải quyết.

---

### II. GIẢI THÍCH CHI TIẾT CÁC KIẾN THỨC TRỌNG TÂM

#### 1. Ba Phán Quyết Tính Khả Thi (Three Feasibility Verdicts)
Phán quyết khả thi là **một tài liệu bằng văn bản (written deliverable)**, được đưa ra **trước khi** dự án bắt đầu. Có 3 kết quả:
* **Yes:** Khả thi hoàn toàn với các ràng buộc hiện tại.
* **Yes, if (Khả thi nếu...):** Chỉ khả thi khi có thứ gì đó thay đổi (ví dụ nới lỏng ràng buộc). **Điều kiện bài thi:** Chữ "if" này phải được ghi lại bằng văn bản và có người chịu trách nhiệm (owner), nếu không nó sẽ tự động bị hiểu nhầm thành "Yes" sau vài cuộc họp.
* **No (Không khả thi):** Không thể làm được và ràng buộc cũng không thể thay đổi.
  * *Mẹo làm bài:* Đáp án đúng cho một phán quyết "No" là bạn phải **nêu rõ điều kiện nào cần thay đổi** để biến nó thành "Yes". Một chữ "No" không kèm điều kiện chỉ là một "ý kiến", không phải là kết quả kỹ thuật.

#### 2. Định Cỡ Là Bài Toán Số Học (Sizing Is Arithmetic) - *PHẢI THUỘC SỐ LIỆU*
Trước khi viết dòng code nào, bạn phải tính xong 4 con số sau. Đề thi sẽ hỏi trực tiếp các thông số kỹ thuật này:

1. **Dung lượng 1 lần xử lý (Context Windows):**
   * Giới hạn Token: **1M tokens** ở một số model, **200k tokens** ở các model khác.
   * Giới hạn File: Tối đa **600 hình ảnh/trang PDF** cho model 1M, và **100 hình ảnh/trang PDF** cho model 200k.
   * *Hệ quả:* Nếu 1 tác vụ không nhét vừa các giới hạn này, việc sửa Prompt là VÔ DỤNG. Phải **thiết kế lại** (dùng Retrieval/RAG hoặc phân rã Decomposition).
2. **Đếm Token (Token Counting):**
   * Dùng **Token counting endpoint** để đo số lượng input token thực tế (gồm cả system prompt, tools, file) **trước khi gửi đi** với chi phí inference bằng **0**. 
   * *Tuyệt đối KHÔNG ước lượng bằng mắt.*
3. **Chi phí (Cost):**
   * Token đầu vào (Input) và Token đầu ra (Output) **được tính giá riêng biệt (priced separately)**.
   * Tác vụ "đọc 50 trang viết 1 câu" có bài toán kinh tế khác hoàn toàn "đọc 1 câu viết 50 trang". Không bao giờ dùng một con số chi phí "trung bình/request".
4. **Đồng bộ hay Bất đồng bộ (Synchronous vs. Asynchronous):**
   * Dùng **Batch processing (bất đồng bộ)** giảm được **50% chi phí**, hầu hết các batch chạy xong **trong < 1 giờ**.
   * Nếu user không cần kết quả phản hồi tức thì, dùng Batch API là một quyết định sinh lời.

> ⏳ **Con số thứ 5 (Thời hạn Model):** 
> * Anthropic sẽ báo trước **ít nhất 60 ngày (60 days notice)** trước khi ngừng hỗ trợ (retire) một model đang public. Sau ngày đó, mọi request gửi tới model cũ sẽ báo lỗi.
> * *Hệ quả:* Mọi thiết kế ghim cứng vào 1 model đều có "hạn sử dụng". Bạn phải lên kế hoạch **Migration path (lộ trình di chuyển model)** ngay từ đầu.

#### 3. Cam Kết Hiệu Năng (SLA) Là Cổng Loại Trừ (Elimination Gate)
* **Bản chất SLA:** Khi đề bài đưa ra một cam kết hiệu năng (ví dụ: độ trễ tối đa 2s) và **có hình phạt/hậu quả nếu vi phạm** (consequence attached), đó là một **SLA**.
* **Nguyên tắc thiết kế:** SLA là một **Cổng loại trừ (Filter applied first)**. Nghĩa là bạn gạch bỏ ngay lập tức bất kỳ thiết kế nào không đạt SLA, rồi mới lấy các thiết kế còn lại mang đi so sánh xem cái nào Rẻ hơn, Tốt hơn.
* **Cạm bẫy (Anti-pattern):** Đem SLA đi "cộng điểm trung bình" bù trừ với Chi phí/Chất lượng, hoặc hi vọng "làm xong rồi tuning sẽ đạt SLA sau". Sai lầm này sẽ tạo ra một hệ thống rẻ, chất lượng, nhưng vi phạm cam kết cốt lõi.

#### 4. Năm Trụ Cột Giá Trị Kinh Doanh (The 5 Value Pillars)
Đây là phần cực kỳ dễ nhầm lẫn. Bạn phải dùng **Bài Test Mẫu Số (Denominator Test)** để phân loại.

| Trụ Cột Giá Trị | Bản chất | Bài Test Mẫu Số (Dấu hiệu nhận biết) |
| :--- | :--- | :--- |
| **1. Efficiency (Hiệu suất)** | Làm việc cũ tốn ít thời gian/tiền bạc hơn. | Đo trên **mỗi đơn vị công việc (per unit of work)**. *VD: Từ 4h/hợp đồng xuống 40p/hợp đồng.* |
| **2. Productivity (Năng suất)** | Cùng nhóm người đó làm ra nhiều hơn. | Đo theo **sản lượng trên mỗi người (output per person)**. *VD: Xử lý 30 đơn/ngày/người lên 90 đơn.* |
| **3. Transformation (Chuyển đổi)** | Làm được việc mà **trước đây không thể làm**. | Sinh ra **một năng lực mới hoàn toàn** (ở bất kỳ mức giá nào). |
| **4. Cost (Chi phí)** | Tổng chi tiêu thay đổi. | Tổng số tiền tiêu hao (gồm cả tiền nuôi hệ thống AI mới). |
| **5. Performance SLA** | Cam kết có gắn liền hậu quả/chế tài. | Có con số cụ thể, và hỏi rõ "Phải đền gì nếu vi phạm?". |

* 🚨 **2 LƯU Ý SỐNG CÒN CHO BÀI THI:**
  1. Cắt giảm nhân sự (Eliminating a role) là **Efficiency**, KHÔNG phải Transformation (vì không sinh ra năng lực gì mới).
  2. Thời gian được tiết kiệm **CHƯA CHẮC** là giá trị tạo ra: Nếu thời gian làm mỗi tài liệu giảm, nhưng tổng lượng đầu ra của doanh nghiệp đứng yên $\rightarrow$ Đó là **Unrealised productivity (Năng suất chưa được hiện thực hóa)**. AI không sai, quy trình quanh AI sai.

#### 5. Nghĩa Vụ Vòng Đời Dự Án (Lifecycle & Handoff)
* **Quy tắc tiêu thụ:** Một tài liệu/đầu ra của giai đoạn này chỉ có thực nếu **giai đoạn sau mở ra và dùng nó (consumes it)**. Các thứ như: Slide báo cáo tiến độ, Lịch sử dự án, Quyết định nội bộ... chỉ mang tính "nghi lễ" (ceremonial), không có tác dụng với hệ thống.
* **Giai đoạn Bàn Giao (Handoff):** Xong khi đội nhận hệ thống tự chạy, tự sửa lỗi, tự chẩn đoán được mà không cần hỏi người tạo ra nó. Yêu cầu đúng 3 thứ:
  1. **Design rationale:** Lý luận thiết kế (Tại sao lại làm thế này).
  2. **Operating procedures:** Quy trình vận hành.
  3. **Runnable set of checks:** Bộ kiểm thử chạy được ngay.
  *(Tuyệt đối KHÔNG chọn: Timeline, Project history, Decision logs).*
* **Giai đoạn Giám sát (Monitoring):** Là quét hệ thống **theo lịch định kỳ**, chạy lại **bộ test được bù đắp từ traffic thật**, và dùng nó để **chặn/cho phép (gate) các thay đổi**.
  *(Sai lầm: Hành động mù quáng theo ngày tháng, theo vendor release model mới, hoặc thụ động chờ khách hàng chửi mới sửa).*

#### 6. Tinh Chỉnh (Iteration) vs Thiết Kế Lại (Redesign) - Bài Test 1 Dòng
* **Iteration (Tinh chỉnh):** Mọi thứ còn có thể xử lý, nhét vừa bên trong **ranh giới các component hiện có** (dù là để sửa accuracy thấp hay latency cao).
* **Redesign (Thiết kế lại):** Bắt buộc làm khi xuất hiện một **yêu cầu mới mà các thành phần (component) hiện tại không thể chứa/biểu đạt được**. (Volume tăng thường chỉ là Iteration; Yêu cầu xử lý loại khái niệm hoàn toàn mới là Redesign).

---

### III. BẢNG NHẬN DIỆN BẪY TRONG ĐỀ THI (CHEAT SHEET)

| Tình huống đề bài (Scenario) | Đáp án ĐÚNG (The Answer is usually) | Đáp án BẪY (The Trap is usually) |
| :--- | :--- | :--- |
| Kết quả tính bằng thời gian/chi phí **trên mỗi tài liệu/đơn vị công việc**. | Chọn **Efficiency**. | Chọn Productivity (chỉ vì có người tham gia). |
| Kết quả tính bằng **đầu ra trên mỗi cá nhân / mỗi kỳ**. | Chọn **Productivity**. | Chọn Efficiency (vì thấy làm nhanh hơn). |
| Một vị trí bị cắt giảm, làm việc cũ ít tiền hơn. | Chọn **Efficiency**. | Chọn Transformation (đòi hỏi năng lực mới cơ). |
| Có SLA về thời gian phản hồi, độ khả dụng, throughput. | Dùng làm **Elimination Gate (Cổng loại trừ)** trước khi chấm điểm bất cứ thứ gì khác. | Lấy SLA chấm điểm cộng trung bình bù trừ với Chi phí / Chất lượng. |
| Lo lắng data gửi đi không vừa Context Window. | **Đo ngay bằng Token Counting Endpoint** trước khi quyết định. | Nhắm chừng bằng mắt, cố gò Prompt cho ngắn. |
| Công việc chạy nền, không cần phản hồi trực tiếp (non-interactive). | Dùng **Batch API** lấy giảm giá 50%. | Mặc định để chạy Synchronous y hệt lúc viết code test (prototype). |
| Có yêu cầu mới nhảy vào giữa lúc đang Build. | Vẫn là **Iteration**, trừ phi component hiện tại không đủ sức biểu đạt nó (thì mới Redesign). | Khó quá thì gọi Redesign, dễ quá thì gọi Iteration. |
| Đội vận hành nhận bàn giao (Handoff) hệ thống. | Cần: **Design rationale, Operating procedures, bộ test Runnable checks**. | Đưa cho họ: Project history, timelines, logs cãi nhau của dự án. |
| Hệ thống chạy rất mượt nhưng chẳng ma nào dùng. | Quy trình/Thiết kế **xung quanh công cụ** (work around tool) bị hỏng. | Đi bới móc tìm lỗi bên trong con AI/model. |

### IV. NHỮNG ĐIỀU BẮT BUỘC PHẢI NHỚ (WHAT TO REMEMBER)
1. Con số: **1M / 200k** Tokens; **600 / 100** PDF pages; **Batch giảm 50%** giá; **60 ngày** thông báo retire model; Check token giá **0 đồng**.
2. **SLA là Cổng gác (Gate)** chứ không phải thông số để chấm điểm đánh đổi. Trượt SLA là bỏ đi.
3. Bài Test Mẫu Số: Mẫu số là **Món đồ/Tác vụ $\rightarrow$ Efficiency**. Mẫu số là **Con người $\rightarrow$ Productivity**.
4. Handoff chỉ cần đồ nghề thực chiến (**Lý luận, Quy trình, Bộ test**). Không cần đồ cổ (Lịch sử dự án).