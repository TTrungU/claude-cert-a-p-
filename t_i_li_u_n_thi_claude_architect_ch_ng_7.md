# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL

## Chương 7: Model, Context Window, Context Strategy (Model, Cửa Sổ Ngữ Cảnh & Chiến Lược)

### I. TÓM TẮT CỐT LÕI (CORE SUMMARY)
Chương này là nơi đề thi hỏi chi tiết và "ác" nhất, vì nó liên quan trực tiếp đến tài liệu kỹ thuật (docs) của Anthropic. 
* 3 quyết định mấu chốt: Cái gì thực sự chiếm dụng Context Window? Tại sao nhồi nhét quá nhiều lại làm giảm chất lượng (chứ không chỉ tốn tiền)? Khi nào nên nạp sẵn dữ liệu vs. tải khi cần (on-demand)? 
* Chọn model phải dựa trên **Đo lường (Measure)**, không dựa trên cảm tính hay cãi vã.

---

### II. KIẾN THỨC TRỌNG TÂM & BẪY KỸ THUẬT (RẤT DỄ THI)

#### 1. Sự thật về Context Window (Bộ nhớ làm việc)
* **MỌI THỨ đều bị tính vào Window:** System prompt, lịch sử chat, tool results, ảnh, tài liệu, **Tool definitions (định nghĩa tool)**, và output sinh ra. 
* 🚨 **Bẫy Caching (Prompt Caching):** Việc bạn Cache một đoạn prompt dài **KHÔNG** làm giải phóng không gian của Context Window. Caching chỉ thay đổi **số tiền bạn phải trả**, nó không thay đổi **số lượng token bị đếm**.
* **Vách đá bộ nhớ (The Working-Memory Cliff):** Context Window là RAM, không phải Ổ cứng. Khi bị nhồi quá đầy, nó không báo lỗi, mà âm thầm **quên mất dữ liệu nằm ở GIỮA (middle)** đoạn hội thoại, trong khi dữ liệu ở 2 đầu vẫn nhớ.
  * *Cách sửa duy nhất:* Giảm lượng dữ liệu nạp vào. Đừng tốn công reordering (đảo vị trí) hay viết prompt nhắc nhở.

#### 2. Thông số Model & Nhận thức Ngữ cảnh (Context Awareness) - *HỌC THUỘC BẢNG NÀY*
| Thông số | Dòng Model |
| :--- | :--- |
| **Window 1 Triệu Token** (Output tối đa 128k) | Claude Opus 5, Opus 4.8, Opus 4.7, Opus 4.6, Sonnet 5, Sonnet 4.6 |
| **Window 200k Token** | Các model khác (Bao gồm Sonnet 4.5) |
| **CÓ Nhận thức ngữ cảnh** (Được tiêm tags báo dung lượng còn lại sau mỗi tool call) | **Sonnet 5, Sonnet 4.6, Sonnet 4.5, Haiku 4.5** |
| **KHÔNG CÓ nhận thức ngữ cảnh** | **Opus 4.7 (và Opus sau này), Fable 5, Mythos 5** |

* 🚨 **Bẫy tư duy (Counter-intuitive Trap):** Model MẠNH NHẤT (Opus 4.7+) lại **KHÔNG BIẾT** nó còn bao nhiêu chỗ trống trong Window. Đừng thiết kế hệ thống dựa trên giả định rằng "Model xịn thì tự biết quản lý dung lượng".
* **Giá cả:** Từ bản 4.6 trở lên, 1M Window có giá tiêu chuẩn (Standard pricing). Một request 900k token có chung đơn giá per-token như request 9k token (không bị tính phí premium).

#### 3. Hai Kiểu Tràn Window (Window Exceeded)
1. **Input > Window:** Báo lỗi `400 invalid request` NGAY LẬP TỨC. Request không hề chạy.
2. **Input + max_tokens > Window:** Request **VẪN CHẠY**. Khi chạm trần, nó sẽ dừng lại và trả về mã stop reason là `model_context_window_exceeded`. 
   * *Bẫy thực tế:* Nếu code của bạn chỉ check mã HTTP 200, hệ thống sẽ coi kết quả bị cắt cụt (truncated) này là hoàn chỉnh. Bắt buộc phải **đọc Stop Reasons**.

#### 4. Chi phí cho việc "Suy nghĩ" (Thinking & Effort)
* Token suy nghĩ (Thinking tokens) **được tính tiền bằng giá Output Token**, ngay cả khi phần text suy nghĩ bị ẩn không trả về cho bạn. Chúng "giành giật" không gian với Output thật trong giới hạn `max_tokens`.
* **Cơ chế kiểm soát mới (Adaptive models):** 
  * `max_tokens`: Giới hạn CỨNG cho tổng output của 1 request.
  * `effort`: Giới hạn MỀM quyết định model nghĩ sâu đến đâu. Mặc định là `high`.
* **Sự khác biệt trong Vòng lặp Agent (Agentic Loop):** 
  * `max_tokens` chỉ giới hạn cho **1 request**. Nếu agent chạy 10 vòng (round trips), nó sẽ tốn 10 lần max_tokens.
  * Nếu muốn giới hạn chi phí/token cho TOÀN BỘ vòng lặp $\rightarrow$ Bắt buộc dùng **Task Budget**.
* *Lưu ý Migration:* Tham số `budget_tokens` cũ (manual extended thinking) đã bị DEPRECATED. Yêu cầu adaptive thinking trên model cũ (Sonnet/Opus/Haiku 4.5) sẽ bị lỗi 400.

#### 5. Compaction vs. Context Editing (Nén vs. Xóa Ngữ Cảnh)
* **Compaction (Nén):** Tự động tóm tắt lại context cũ khi sắp chạm trần (Mặc định kích hoạt ở 150k token, tối thiểu 50k). 
  * *Bẫy chết người:* Nếu bạn viết Custom Instructions cho Compaction, nó sẽ **GHI ĐÈ (Replace hoàn toàn)** prompt mặc định. Bạn sẽ vô tình làm mất lệnh yêu cầu model "ghi nhớ trạng thái và bước tiếp theo", trừ khi bạn tự viết lại câu đó vào prompt của mình.
* **Context Editing (Chỉnh sửa ngữ cảnh):** Xóa bớt lịch sử.
  * Việc xóa Tool Results sẽ làm **mất hiệu lực (invalidate) Cached Prompt**. Vì vậy hãy dùng tham số `clear_at_least` để tích đủ lượng rác rồi xóa 1 lần, tránh việc phải trả tiền tạo Cache liên tục do xóa lắt nhắt.

#### 6. Xử lý Tool Catalogues khổng lồ
* Việc ném bộ lọc (Router) ra trước Tool Catalogue khổng lồ **KHÔNG** giải quyết được lỗi model chọn nhầm tool. Nó chỉ giới hạn số tool hiển thị, nhưng các tool có *Mô tả trùng lặp/Na ná nhau (Overlap)* thì vẫn nằm đó.
* **Cách giải quyết (Decomposition):** Phân rã bộ tool dựa trên 2 bằng chứng bắt buộc:
  1. Các mô tả tool đang bị trùng lặp/chồng chéo (Overlap).
  2. Tồn tại một "đường ranh giới tự nhiên" (Seam) trong lĩnh vực (domain) để cắt đôi bộ tool.
  *(Chỉ vì danh sách tool dài không phải là lý do để chia tách).*

---

### III. CHEAT SHEET: NHẬN DIỆN BẪY ĐỀ THI CHƯƠNG 7

| Khi tình huống đề cập... (Scenario says) | Đáp án đúng thường là... (Answer is usually) | Bẫy thường gặp... (Trap is usually) |
| :--- | :--- | :--- |
| Model bắt đầu quên dữ liệu ở GIỮA tài liệu dài. | Phải **giảm lượng dữ liệu** nạp vào Window. | Đảo vị trí, thêm emphasis, mắng model trong prompt. |
| Chi phí tăng VÀ độ chính xác tầm trung giảm. | Đây là 1 lỗi do **Volume (Quá tải dung lượng)** $\rightarrow$ Xử lý chung bằng cách cắt giảm token. | Tưởng là 2 lỗi tách biệt và tìm 2 cách sửa khác nhau. |
| Bạn Cache một đoạn Preamble rất lớn (Prompt Caching). | Đoạn cache đó **vẫn chiếm chỗ** trong Context Window. | Tưởng cache xong thì Window rộng ra $\rightarrow$ Tràn RAM. |
| Model cần tự đong đếm/phân bổ chỗ trống Window còn lại. | Phải check xem model đó có nhận được **Capacity Tags** không. | Mặc định model càng xịn (Opus 4.7) thì tự khắc biết. |
| Sinh văn bản dài bị lỗi tràn Window. | Check **Stop Reasons** (`model_context_window_exceeded`). | Chỉ check lỗi HTTP (sẽ bị lầm tưởng là đã xong). |
| Chọn Tier model cho tác vụ dán nhãn (Labelling/Classification). | Chọn Tier rẻ nhất vượt qua ngưỡng Accuracy đo đạc. | Mua model có "Reasoning Depth" cao dù tác vụ không cần. |
| Cần kiểm soát tổng chi phí của 1 Agentic Loop (nhiều bước). | Dùng **Task Budget** (quản lý trọn gói loop). | Dùng `max_tokens` (chỉ áp dụng cho 1 vòng request). |
| Đưa Custom Compaction Instructions để tóm tắt context. | Bạn phải **Viết toàn bộ prompt** (kể cả lệnh lưu state/next steps). | Tưởng chỉ cần viết thêm 1 dòng instruction bổ sung. |
| Muốn xóa bớt Tool results để lấy không gian (Context edit). | Dùng **`clear_at_least`** để dọn theo đợt đáng đồng tiền bát gạo. | Xóa lắt nhắt liên tục (Làm mất Cache $\rightarrow$ Tốn tiền). |
| Tool Catalogue bị phình to gây lỗi chọn nhầm tool. | **Decompose (Phân rã)** bộ tool dọc theo ranh giới domain. | Dùng Router (Không giải quyết được việc các tool na ná nhau). |
| Dữ liệu phụ nhỏ, không đổi hoặc lúc nào cũng cần xài. | **Nạp sẵn từ đầu (Load up front)**. | Tải khi cần (Deferral/On-demand) làm tốn round-trips vô ích. |

---

### IV. NHỮNG ĐIỀU BẮT BUỘC PHẢI NHỚ (MUST REMEMBER)
1. **Caching không tăng RAM:** Nó chỉ giảm tiền. Mọi thứ vẫn chiếm Context Window.
2. **Vách đá trí nhớ:** Model sẽ chết chìm/quên ở phần GIỮA của context.
3. **Mã lỗi Tràn Window:** Bị ngay từ đầu $\rightarrow$ 400. Bị lúc đang generate $\rightarrow$ Stop reason: `model_context_window_exceeded`.
4. **Nhận thức Context (Context Tags):** Có ở Sonnet 4.5, 4.6, 5 & Haiku 4.5. **KHÔNG CÓ ở Opus 4.7+, Fable 5**.
5. **Thinking cost:** Tính tiền như Output, nằm trong giới hạn `max_tokens`.
6. **Task Budget vs Max Tokens:** Task budget cho toàn bộ quá trình Agentic. Max tokens cho đúng 1 request API lẻ.
7. **Compaction Ghi Đè (Override):** Custom instruction sẽ thay thế hoàn toàn lệnh mặc định, hãy cẩn thận mất lệnh giữ state.