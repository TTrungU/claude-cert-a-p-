# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL

## Chương 6: Reference Architectures and Retrieval Against Live State (Kiến Trúc Tham Chiếu & Truy Xuất Dữ Liệu Thực)

### I. TÓM TẮT CỐT LÕI (CORE SUMMARY)
Retrieval (RAG) là nơi hệ thống dễ "lừa" bạn nhất: thiết kế trông có vẻ rất chuẩn nhưng lại trả về kết quả sai bét với một khuôn mặt tỉnh bơ. Hầu hết lỗi đến từ 2 nguyên nhân:
1. **Ép một chiến lược tìm kiếm duy nhất** lên một luồng dữ liệu (traffic) chứa 2 loại câu hỏi hoàn toàn trái ngược nhau.
2. **Đưa dữ liệu thay đổi liên tục (live state) vào Index**, khiến dữ liệu thay đổi nhanh hơn tốc độ bạn có thể rebuild index.

---

### II. KIẾN THỨC TRỌNG TÂM: 2 LOẠI QUERY & CHIẾN LƯỢC TÌM KIẾM

Một kho dữ liệu (corpus) không bao giờ chỉ có 1 kiểu query. Nó có 2 kiểu, và chúng đòi hỏi 2 cách xử lý **hoàn toàn trái ngược nhau**.

| Loại Câu Hỏi (Query Shape) | Đặc điểm | Chiến lược ĐÚNG (What matches it) | Cái gì phá hỏng nó? (What breaks it) |
| :--- | :--- | :--- | :--- |
| **1. Tra cứu định danh (Identifier lookups)** | User gõ mã đơn hàng, mã phụ tùng, mã lỗi... Họ biết chính xác mình tìm gì. | **Exact / Lexical matching** (Khớp chính xác) hoặc Key Lookup. | **Semantic Embedding (nhúng ngữ nghĩa)**. Vì embedding loại bỏ bề mặt từ vựng và gộp các mã số gần giống nhau lại với nhau $\rightarrow$ Sai mã là sai hoàn toàn, không có khái niệm "đúng một nửa". |
| **2. Câu hỏi khái niệm (Conceptual questions)** | User hỏi "Quy trình này hoạt động sao?", dùng từ vựng không hề có trong tài liệu. | **Semantic similarity** (Tương đồng ngữ nghĩa) trên các chunk dữ liệu. | **Exact matching**. Vì từ vựng user dùng không hề tồn tại trong tài liệu gốc để mà khớp chính xác. |

🚨 **Giải pháp khi traffic có cả 2 (Rất hay thi):**
Bắt buộc phải **GIỮ CẢ 2 chiến lược và có cơ chế Định Tuyến (Route)** từng query vào đúng chiến lược của nó. 
*Cạm bẫy (Anti-pattern):* Chọn 1 chiến lược duy nhất (ví dụ ép dùng toàn bộ Semantic search) và gọi đó là "đơn giản hoá kiến trúc". Thực chất bạn đang chọn làm cho 50% user bị sai kết quả.

---

### III. DỮ LIỆU THỰC (LIVE STATE) KHÔNG ĐƯỢC ĐỂ TRONG INDEX

Index bản chất là một **bản chụp (snapshot)**. Giữa lúc bạn chụp snapshot và lúc user hỏi, số lượng tồn kho đã đổi, tài khoản đã bị trừ tiền, đơn hàng đã được giao.
*   **Hậu quả:** Hệ thống search thành công $\rightarrow$ Lấy ra văn bản hợp lệ $\rightarrow$ Trả về câu trả lời SAI nhưng cực kỳ tự tin, đính kèm cả trích dẫn (citation) khiến nó trông cực kỳ uy tín.
*   **Cách khắc phục:** 
    *   Dữ liệu tĩnh (Stable) $\rightarrow$ Đưa vào Index.
    *   Dữ liệu động/Live state (Tồn kho, Số dư, Trạng thái đơn, Giá thay đổi hàng ngày) $\rightarrow$ **Dùng Tool Call / API chọc thẳng vào System of Record (Hệ thống gốc) tại thời điểm hỏi**.
*   🚨 **Bẫy bài thi:** Đề xuất "Tăng tần suất Rebuild Index" (từ 1 ngày/lần xuống 1 giờ/lần). Sai! Dữ liệu thay đổi từng phút thì rebuild lịch nào cũng chết. Đây là **lỗi kiến trúc (architectural defect)**, không phải lỗi nhịp độ (cadence).

---

### IV. SỰ THẬT VỀ GROUNDING (TRÍCH DẪN / CITATIONS)

Khả năng Grounding (trả về đoạn văn bản gốc chứng minh cho câu trả lời) rất tuyệt vời, nhưng hãy hiểu đúng bản chất của nó:
*   Nó làm cho câu trả lời trở nên **CÓ THỂ KIỂM CHỨNG (Checkable)**.
*   Nó **KHÔNG** làm cho câu trả lời trở nên **ĐÚNG (Correct)**.
*   *Lý do:* Nếu corpus của bạn bị cũ (stale), Grounding chỉ cung cấp cho bạn *"một con đường có thể xác minh dẫn đến một câu trả lời sai"*. Đoạn văn đó ủng hộ câu trả lời, nhưng bản thân đoạn văn đó đã lỗi thời.

👉 **Mẹo tối ưu chi phí với Files API:** Upload file **MỘT LẦN** và gọi nó bằng định danh (Identifier) ở các request sau. Tránh việc request nào cũng gửi lại toàn bộ document làm chi phí phình to theo size của corpus.

---

### V. XỬ LÝ ĐỊNH DANH (IDENTIFIERS / HANDLES) - QUY TẮC SỐNG CÒN

Khi bạn đưa cho model một handle/tham chiếu (vd: DOM tab trình duyệt, row ID, session token):
1.  **Im lặng nghĩa là Hợp lệ (Silence = Validity):** API không tự biết handle đã cũ. Executor (hệ thống của bạn) phải là người kiểm tra và **chủ động trả về lỗi** báo cho model biết handle đó đã stale.
2.  **TUYỆT ĐỐI KHÔNG đánh số lại (Renumber) hoặc tái sử dụng (Reuse) Identifiers.** 
    *   Nếu một ID bị hết hạn/xóa $\rightarrow$ Báo lỗi $\rightarrow$ Hệ thống xử lý được lỗi (Catchable error).
    *   Nếu bạn lấy ID cũ gán cho data mới $\rightarrow$ Model cầm ID cũ thực hiện hành động $\rightarrow$ **Hành động bị sai hoàn toàn một cách tự tin (Confident wrong action)**.

---

### VI. CHEAT SHEET: NHẬN DIỆN BẪY ĐỀ THI CHƯƠNG 6

| Khi tình huống đề cập... (Scenario says) | Đáp án đúng thường là... (Answer is usually) | Bẫy thường gặp... (Trap is usually) |
| :--- | :--- | :--- |
| User search bằng mã số, mã phụ tùng, mã lỗi (Part number, Error code). | Dùng **Exact / Lexical matching** hoặc Lookup by Key. | Dùng Semantic search (Làm mã số bị nhòe sang mã gần giống). |
| User hỏi về concept, quy trình bằng từ vựng của riêng họ. | Dùng **Semantic matching** trên embedded chunks. | Dùng Keyword search (Sẽ trượt vì sai từ vựng). |
| Luồng dữ liệu (Traffic) có **CẢ 2** loại query trên. | Giữ CẢ 2 chiến lược và **Định Tuyến (Route)** từng query vào đúng chỗ. | Chọn 1 chiến lược cho mọi thứ và gọi là "Đơn giản hóa". |
| Dữ liệu bị thay đổi trong khoảng thời gian giữa Index và lúc hỏi (Live state). | **Gọi Tool** truy xuất vào hệ thống chủ (System of Record). | Tăng tần suất Rebuild Index / Thêm trường "freshness". |
| Yêu cầu: "Câu trả lời phải được check lại bởi người đọc". | Dùng tính năng **Grounding/Citations** trả về passage gốc. | Mặc định rằng cứ có Attribution (Trích dẫn) thì đáp án là ĐÚNG. |
| Các tài liệu giống hệt nhau bị gửi đi gửi lại ở mọi request. | **Upload 1 lần (Files API)** và tham chiếu lại bằng Identifier. | Chấp nhận chi phí per-request tăng tiến theo kích cỡ corpus. |
| Model cầm một tham chiếu (reference/handle) có thể đã bị thay đổi/hết hạn. | Executor phải **chủ động trả về Lỗi (Explicit error)** báo stale. | Im lặng (Làm model hiểu lầm là vẫn còn dùng được). |
| Một Identifier (Mã định danh) bị trống do data cũ bị xóa. | Bỏ luôn, **để nó báo lỗi (fail)** nếu model gọi lại. | Đánh số lại (Renumber) hoặc tái sử dụng ID đó cho data mới. |

💡 **Thói quen ăn điểm:** Với mọi dữ kiện/sự thật mà hệ thống trả về, hãy hỏi **"Nó ĐÚNG VÀO LÚC NÀO?"**. Kiến trúc Retrieval thất bại vì sai lệch thời gian (time) nhiều hơn là sai lệch độ liên quan (relevance).