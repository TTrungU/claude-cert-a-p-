# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL
## Chương 5: When a Second Agent Is a Liability (Khi Agent Thứ Hai Trở Thành Cục Nợ)

---

### I. TÓM TẮT CỐT LÕI (CORE SUMMARY)
Chương này giúp phân định rõ ràng giữa **lý do kỹ thuật thực sự** để chia nhỏ công việc thành nhiều Agent và **lý do tổ chức** (như sơ đồ phòng ban). Việc thêm một Agent thứ hai không chỉ là thêm một thành phần, mà là sự đánh đổi về tính toàn vẹn của hệ thống (mất kiểm soát thứ tự, mất khả năng dừng đột ngột khi có lỗi, vỡ log).

---

### II. KHI NÀO THỰC SỰ CẦN AGENT THỨ HAI? (CHỈ 2 TRƯỜNG HỢP)
Đừng bao giờ chia nhỏ Agent vì lý do "Sếp muốn", "Team A không ưa Team B", hoặc "Vẽ sơ đồ cho ngầu". Chỉ có **2 đặc tính của chính bản thân CÔNG VIỆC (task)** mới quyết định việc chia tách:

1. **Chuyên môn hoá đối nghịch (Irreconcilable specialisation):** Hai phần của công việc yêu cầu các tệp lệnh (instructions), quyền truy cập tool hoặc ràng buộc **hoàn toàn mâu thuẫn nhau**.
   * *Ví dụ:* Một bên bắt buộc phải "chỉ trích", bên kia bắt buộc phải "sáng tạo". Một bên cần quyền "Write" database, bên kia cấm tuyệt đối.
2. **Sự độc lập thực sự (Real independence):** Các sub-tasks **không cần** kết quả của nhau. Chúng có thể chạy song song (parallel) mà không phải chờ đợi nhau.

> 🚨 **Bẫy Bài Thi (Exam Trap): Lấy sơ đồ tổ chức làm kiến trúc**
> Nếu đề bài lấy lý do "Công ty có 3 phòng ban, Vendor vẽ 5 cái hộp" $\rightarrow$ Kiến trúc đúng vẫn là **1 Agent** nếu bản chất công việc không thoả mãn 2 điều kiện trên. Chọn kiến trúc theo sơ đồ tổ chức là rước rắc rối chính trị vào code.

---

### III. CÁI GIÁ PHẢI TRẢ KHI DÙNG MULTI-AGENT
Khi tách việc ra cho nhiều Agent, bạn **đánh mất 3 sự bảo đảm (Guarantees)**:

1. **Thứ tự (Ordering) biến thành hành vi:** Ở 1 Agent, bạn quy định A chạy trước B. Ở Multi-Agent, thứ tự là sự "nổi lên" (emergent) từ tương tác, thường đúng nhưng lúc sai thì không thể tái lập (reproduce).
2. **Mất khả năng Dừng khi có lỗi (Halt-on-exception):** Không thể tự động dừng mọi thứ khi 1 bước lỗi, vì mỗi Agent chỉ biết lỗi của chính nó.
3. **Vỡ Audit Trail (Dấu vết kiểm toán):** Log bị xé lẻ. Muốn biết chuyện gì xảy ra, phải đi ghép log (correlation exercise) cực kỳ vất vả.

👉 **Hậu quả: Lỗi không thể bắt (The Uncatchable Failure)**
Một Subagent trả về một kết quả **cực kỳ tự tin, đúng chuẩn format, nhưng sai bét** – và bộ điều phối không có cách nào để nghi ngờ. Hệ thống sinh ra một "sự đồng thuận sai" (consensus) mà không ai chịu trách nhiệm.

---

### IV. VAI TRÒ CỦA ORCHESTRATOR (BỘ ĐIỀU PHỐI)
Để giữ lại 3 sự bảo đảm bị mất ở trên, bạn CẦN một **Thành phần duy nhất (Single Component) nắm quyền Sequencing (Sắp xếp thứ tự)**.
* Các Worker (Subagents) chỉ làm việc. Chúng KHÔNG ĐƯỢC quyết định trình tự.
* Orchestrator nắm quyền: Chạy cái gì tiếp theo, và làm gì khi có lỗi.

**Cơ Chế Của Một Thiết Kế Orchestration Thực Sự (Từ Anthropic):**
* **1 Worker hỏng:** Lỗi phải được cô lập (isolated), trả về chuỗi báo lỗi chứ không làm sập cả run.
* **Rớt mạng:** Có *Per-request timeout* cho từng call.
* **Bị ngắt giữa chừng:** Lưu log theo *Content-addressed journal* (hash prompt của subagent) để khi chạy lại chỉ chạy phần chưa xong.
* **Kết quả tự tin nhưng sai:** Cần một đợt xác minh (verifiers wave) thứ 2 đi kiểm tra lại tận nguồn. **Nguyên tắc: Không chắc chắn $\rightarrow$ Mặc định BÁC BỎ (Refuted).**
* **Nhận lại văn bản xuôi (Prose):** Ép Subagents trả kết quả qua 1 Tool chuyên dụng (Structured JSON). *Dùng Regex để tách kết quả là dấu hiệu cho thấy đáng lẽ phải dùng Tool.*

---

### V. 4 LỖI CƠ KHÍ KHI CHẠY TOOL / PARALLEL (CẦN HỌC THUỘC)
1. **MỌI tool call đều phải có result:** Kể cả khi có nhiều tool calls trong 1 turn và bạn QUYẾT ĐỊNH KHÔNG CHẠY một tool nào đó, bạn vẫn phải trả về result block cho tool đó (đánh dấu là `error`). Không được phép im lặng.
2. **Tool chưa chạy xong (Unfinished tool call):** KHÔNG có cờ (flag) nào báo lỗi này ngoài việc **thiếu result block**. (Cách check: Lấy ID của call so với ID của result).
3. **Vòng lặp bị tạm dừng (Paused turn):** Ở phía server, khi loop đạt giới hạn (iteration limit, mặc định là **10**), turn trả về trạng thái *paused*. Cách xử lý: Cứ **tiếp tục hội thoại (continue the conversation)**. Đừng coi nó là lỗi (failure).
4. **Task Budget KHÔNG PHẢI là giới hạn cứng (Hard cap):** Budget chỉ là "lời nhắc nhẹ" (soft hint), model CÓ THỂ xài lố. Muốn giới hạn **cứng**, phải dùng **Maximum Token Setting** của request.

---

### VI. CÀNG NHIỀU TOOL, AGENT CÀNG LÚ (TOOL CONFUSION)
Khi Agent chọn sai tool liên tục, triệu chứng này **tỉ lệ thuận với số lượng CÁC LĨNH VỰC KHÔNG LIÊN QUAN (unrelated domains)** bị nhét chung vào một context.
* **Cách sửa chuẩn:** Tách nhỏ thành các Agent khác nhau dựa trên ranh giới lĩnh vực.
* **Cách làm sai:** Viết mô tả tool dài hơn, cho thêm ví dụ, thêm lệnh routing vào system prompt (chỉ làm context chật thêm).

---

### VII. CHEAT SHEET: BẪY BÀI THI CHƯƠNG 5

| Khi tình huống đề cập... (Scenario says) | Đáp án đúng thường là... | Bẫy thường gặp... |
| :--- | :--- | :--- |
| Có các phần việc dùng Tool đối nghịch, cấm kỵ nhau | **Tách làm 2 Agent** (Irreconcilable specialisation). | Gom chung vì nghĩ chỉ là việc "hơi khác nhau". |
| Các sub-task hoàn toàn không cần kết quả của nhau | **Tách Agent và chạy song song (Parallel)**. | Tách Agent nhưng bắt chờ nhau chạy tuần tự. |
| Chia Agent vì chia Team, chia sơ đồ tổ chức | Dùng **1 Agent** (Trừ khi bản chất task bắt buộc). | Dùng Org fact làm cơ sở thiết kế kiến trúc. |
| Phải kiểm soát Thứ Tự và dừng khi Lỗi | Dùng **1 Orchestrator nắm quyền Sequencing**. | Các Agent chạy peer-to-peer tự đàm phán. |
| Agent ngày càng chọn sai tool khi thêm tính năng | **Giảm bớt Domain** trên 1 Agent (Tách Agent theo domain).| Viết mô tả dài ra, thêm ví dụ, nhét lệnh routing. |
| Lo ngại Subagent trả về kết quả mượt nhưng bịa đặt | Thêm bộ **Verifier**. Không chắc $\rightarrow$ **REFUTED (Bác bỏ)**.| Verifier mặc định là "Approve" (Đồng ý) khi không chắc. |
| Model trả về nhiều tool calls, bạn không muốn chạy 1 vài cái | **Trả Result cho TẤT CẢ**, cái nào không chạy thì báo lỗi. | Chỉ trả Result cho những tool thực sự chạy. |
| Làm sao biết 1 tool call chưa chạy xong ở server? | Check xem **ID của nó có Result match không**. | Tìm một cờ tên là `status: unfinished`. |
| Request trả về báo Pause vì quá vòng lặp (Iteration limit) | Cứ **tiếp tục hội thoại**. | Ném lỗi (throw error), vứt bỏ kết quả. |
| Cần kiểm soát chi phí CHUẨN XÁC KHÔNG VƯỢT | Dùng **Maximum Token Setting**. | Dùng `Task Budget` (Model có thể vượt). |
| Phải dùng Regex để tách câu trả lời của Subagent | Subagent đáng lẽ **phải trả qua một Tool (JSON)**. | Tối ưu đoạn code Regex. |

### VIII. NHỮNG ĐIỀU BẮT BUỘC PHẢI NHỚ
1. **Chỉ chia Agent khi:** Mâu thuẫn quyền/tool (Irreconcilable specialisation) HOẶC Độc lập hoàn toàn (Real independence).
2. **Multi-Agent làm mất:** Order (thứ tự), Halt-on-exception (dừng khi lỗi), và Audit Trail (log).
3. Phải có **1 Orchestrator nắm quyền Sequencing**.
4. Tool không chạy vẫn phải có Result block báo lỗi. Iteration limit = 10 (tiếp tục hội thoại). Task Budget là Soft Hint.
5. Verifier phải mặc định **Bác bỏ (Refuted)** khi không chắc chắn, nếu mặc định "Cho qua" thì chỉ là cục tốn tiền.