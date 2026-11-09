# 📘 Claude Architect Professional - Study Guide
# Chapter 9: Chunking, Indexing, and the Query You Did Not Anticipate

**Tóm tắt cốt lõi**: Chương này giải quyết sai lầm phổ biến nhất trong RAG: Cố gắng sửa lỗi "thiếu ngữ cảnh" bằng cách tăng số lượng kết quả trả về, thay vì sửa cách cắt dữ liệu (chunking). Ngoài ra, chương này cũng đi sâu vào chi phí PDF, cơ chế trích dẫn (citations) và sự khác biệt giữa Cache và Retrieval.

---

## I. Quyết Định Chunking (Cắt Dữ Liệu)
Lỗi kinh điển: Model trả về một đoạn text chứa 1 phần câu trả lời, nhưng ngoại lệ (exception) hoặc định nghĩa (definition) lại nằm ở đoạn khác.
*   **Sai lầm phổ biến (Exam Trap):** Tăng số lượng passage lấy về, tăng chunk size, thêm overlap, hoặc dùng re-rank. Tất cả những cái này chỉ thay đổi **số lượng**, không thay đổi **nội dung** bên trong mỗi chunk.
*   **Giải pháp đúng:** Cắt các unit sao cho chúng **tự có ý nghĩa trọn vẹn (stand on its own)**. Các điều kiện, ngoại lệ phải được gắn liền với nội dung chính.
*   **Thần chú:** *Chunk by corpus, index by query.* (Cắt theo cấu trúc tài liệu, Index theo câu hỏi người dùng).

---

## II. Cơ Chế Trích Dẫn (Citations & Grounding)
Đơn vị nhỏ nhất có thể trích dẫn (Citable unit) là một **Text Block**.
*   Model trích dẫn *toàn bộ block*, chứ không trích dẫn một vài từ (substrings) trong đó.
*   **Nếu muốn trích dẫn chi tiết hơn:** Phải cắt content thành các block nhỏ hơn. (KHÔNG PHẢI ghi prompt dặn model trích dẫn chi tiết). -> **Ranh giới block chính là ranh giới trích dẫn.**
*   **Lưu ý cực quan trọng:** 
    *   Citation mặc định bị **TẮT** đối với kết quả search (Search results). Thiết kế mà mặc định nó tự bật là sai.
    *   Khi search thất bại/không ra kết quả: Hãy trả về một **plain text block** mô tả việc không tìm thấy, để model có thể giải thích. **KHÔNG** raise error (báo lỗi) vì nó sẽ làm sập nguyên một turn hội thoại bình thường.

| Loại Document | Cách tự động Chunk | Cách Trích dẫn (Citation) |
|---|---|---|
| **Plain text** | Tự cắt theo câu (sentences) | Bằng chỉ số ký tự (character indices) |
| **PDF (có text)** | Tự cắt theo câu (sentences) | Bằng số trang (page number) |
| **Custom content** | **KHÔNG** bị chunk thêm | Bằng block indices -> **Dùng cái này khi muốn kiểm soát độ chi tiết của trích dẫn!** |

---

## III. Sự Thật Về Chi Phí Xử Lý PDF
Việc đưa PDF vào model có độ chênh lệch chi phí lên tới **7 LẦN**, nên đây là một quyết định tài chính chứ không phải sở thích:
*   **Text extraction (Chỉ lấy chữ):** Khoảng 1,000 tokens cho 3 trang.
*   **Full visual understanding (Hiểu cả hình ảnh/cấu trúc):** Khoảng 7,000 tokens cho 3 trang.
👉 Chỉ dùng Visual Understanding khi **cách trình bày có ý nghĩa** (ví dụ: bảng biểu, form, sơ đồ, chữ ký). Đưa 1 đống chữ (wall of text) vào Visual là lãng phí tiền bạc. Tính năng PDF dùng chung năng lực Vision của Claude.

---

## IV. Lỗi Dữ Liệu Cũ (Stale Content) Trong RAG
Khi hệ thống cứ trả về tài liệu lỗi thời, bạn chỉ có thể can thiệp ở 2 chỗ:
1.  **Lúc Ingestion (Nạp dữ liệu vào index):** Sửa cái hệ thống ghi dữ liệu cũ vào.
2.  **Lúc Retrieval filtering (Lọc kết quả tìm kiếm):** Sửa cái hệ thống để nó từ chối trả về dữ liệu cũ.
*   **Bẫy:** Đề bài gài bạn chọn "Thay đổi cách model tạo câu trả lời (generation)" hoặc "Rebuild index thường xuyên hơn". Nếu dữ liệu cũ đã lọt vào danh sách passage đưa cho model, thì prompt nào cũng vô dụng. Rebuild mỗi đêm vẫn để lại 1 ngày dữ liệu cũ.

---

## V. Caching (Lưu đệm) vs. Retrieval (Truy xuất)
Hai bài toán đọc nghe giống hệt nhau nhưng cách giải trái ngược nhau:

| Tình huống | Đặc điểm cốt lõi | Giải pháp |
|---|---|---|
| Hỏi nhiều lần trên **Cùng 1 tài liệu lớn** (Hợp đồng, Báo cáo...) | Tài liệu **giữ nguyên**, câu hỏi thay đổi. | **Caching (Lưu đệm)** toàn bộ tài liệu thành Prefix. Trả tiền 1 lần. |
| Một thư viện lớn, mỗi câu hỏi chỉ cần **1 mẩu nhỏ** | Yêu cầu lặp lại, nhưng mỗi câu hỏi **cần 1 phần khác nhau**. | **Retrieval (Truy xuất / RAG)**. Index nó và chỉ lấy phần cần thiết. |

**🚨 Bẫy Data Residency (Ranh giới dữ liệu):**
Nếu dữ liệu **KHÔNG ĐƯỢC PHÉP rời khỏi** ranh giới của khách hàng -> **KHÔNG THỂ dùng Index** (vì Index tạo ra 1 bản sao dữ liệu thứ 2 nằm ở hệ thống khác). Caching an toàn hơn vì nó không tạo ra bản sao vĩnh viễn ở hệ thống khác.

---

## VI. BẢNG TRÁNH BẪY (Cheat Sheet Chương 9)

| Khi tình huống mô tả... (Scenario says) | Đáp án đúng là... (Answer is usually) | Bẫy thường gặp... (Trap is usually) |
|---|---|---|
| Text lấy về hay bị mất vế điều kiện, ngoại lệ, định nghĩa | **Cắt lại các unit độc lập** (Gắn kèm định nghĩa vào nó) | Lấy thêm passage, chunk to hơn, thêm overlap, re-ranking |
| Trích dẫn (Citation) quá chung chung (nguyên cả trang) | **Chia nhỏ content thành các khối (blocks) nhỏ hơn** | Viết prompt bắt model phải trích dẫn chi tiết hơn |
| Bạn cần kiểm soát chặt chẽ ranh giới trích dẫn | Dùng **Custom content** (không bị tự động chunk, cite theo block) | Dùng PDF/Plain text (nó sẽ tự chunk theo câu) |
| Search không ra kết quả / search lỗi | Trả về một **plain text block** mô tả kết quả đó | Raise an error (báo lỗi sập luôn quá trình) |
| Cần hiển thị trích dẫn (Attribution) cho kết quả search | Phải **Bật (Enable)** nó lên vì mặc định nó đang Tắt | Mặc định rằng nó luôn tự động có |
| Tài liệu thay đổi liên tục, dính dữ liệu cũ | Chỉ xử lý được ở **Ingestion** (Lúc nạp) và **Retrieval filtering** (Lúc lọc) | Thay đổi Generation prompt, Rebuild index thường xuyên hơn |
| Cần xử lý PDF, muốn tối ưu chi phí | Phân biệt rõ **Text extraction (rẻ)** vs **Visual understanding (đắt gấp 7)** | Nghĩ rằng Visual lúc nào cũng tốt và là tuỳ chọn chất lượng |
| Tool catalogue quá khổng lồ | **Search catalogue** và chỉ nạp (load) cái nào task đó cần | Bắt model đọc hết list tool khổng lồ mỗi lần gọi |
| Cần embedding model (nhúng) | Dùng của **Bên thứ ba (Third-party provider)** | Chọn "Anthropic embedding endpoint" (Anthropic không có!) |
| Hỏi nhiều câu trên cùng 1 tài liệu lớn | **Cache** nó vào prefix (Dữ liệu lặp, câu hỏi đổi) | Xây dựng Index riêng cho tài liệu đó (RAG) |
| Chính sách công ty cấm dữ liệu rời khỏi ranh giới mạng | **KHÔNG dùng external Index** (Dùng Cache vì nó không lưu bản sao lâu dài) | Bỏ qua vấn đề bảo mật và vẫn tập trung vào hiệu năng RAG |

---
*Mẹo ghi nhớ: Trước bất kỳ thay đổi nào của RAG, hãy tự hỏi "Cái này làm thay đổi SỐ LƯỢNG (size) hay NỘI DUNG (content) của tập kết quả?". Hầu hết bẫy bài thi là lấy Số lượng để chữa lỗi Nội dung.*