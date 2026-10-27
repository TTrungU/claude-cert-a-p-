# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL
## Chương 2: Discovery Is Elicitation, Not Conversation (Khám Phá Là Khai Thác Yêu Cầu, Không Phải Trò Chuyện)

---

### I. TÓM TẮT TƯ DUY CỐT LÕI (CORE MINDSET)
* **Sự thất bại kinh điển của giai đoạn Discovery:** Một ràng buộc (constraint) vốn luôn tồn tại ngay từ đầu nhưng đến tận tuần thứ 6 mới lộ ra và làm sụp đổ toàn bộ thiết kế. Không ai giấu nó cả — chỉ là **không ai hỏi**.
* **Bản chất của Discovery:** Khách hàng luôn mở lời bằng một **giải pháp (named solution)** mà họ muốn bạn xây dựng. Công việc của Discovery là tách bạch **giải pháp họ vừa nêu** ra khỏi **vấn đề thực sự (unnamed problem)** mà họ chưa hề nhắc tới.
* **Con người chỉ trả lời những gì được hỏi (They do not volunteer constraints):** Đừng kỳ vọng khách hàng tự giác khai báo mọi ràng buộc. Bạn phải chủ động dùng phương pháp để "khai thác" (elicit) chứ không chỉ ngồi "trò chuyện" (converse).

---

### II. GIẢI THÍCH CHI TIẾT CÁC KHÁI NIỆM TRỌNG TÂM

#### 1. Giả định chưa được ghi nhận (The Undocumented Assumption)
Là những ràng buộc có tính bắt buộc đối với thiết kế, đã tồn tại trước khi dự án bắt đầu nhưng chưa ai nói ra thành lời. Có **2 nhóm chính** và cần 2 cách đặt câu hỏi khác nhau để lôi chúng ra ánh sáng:

| Loại ràng buộc ẩn | Bản chất & Ví dụ | Tại sao họ không tự nói ra? | Cách đặt câu hỏi để khai thác (Elicitation Move) |
| :--- | :--- | :--- | :--- |
| **1. Ràng buộc "Hiển nhiên với họ" (Obvious-to-them constraint)** | Quy định pháp lý (regulation), nơi lưu trữ dữ liệu (data residency), thời hạn lưu trữ (retention rules), hợp đồng sẵn có với vendor, thỏa thuận công đoàn. | Vì nó quá hiển nhiên và thường trực trong công việc hàng ngày của họ (giống như bàn về xe hơi thì không ai tự nhiên nhắc là "phải có đường nhựa"). | **Hỏi về danh mục/phạm trù (Category)** thay vì trường hợp cụ thể: *"Quy tắc nào chi phối nơi dữ liệu này được phép tồn tại?", "Ai khác có quyền quyết định trên quy trình này?", "Điều gì phải đảm bảo để bộ phận Pháp chế ký duyệt?"* |
| **2. Ràng buộc "Đáng xấu hổ/Nhạy cảm" (Embarrassing constraint)** | Quy trình trên giấy tờ khác xa quy trình thực tế; chất lượng dữ liệu rất tệ và mọi người đang phải lách thủ công; hai phòng ban tranh chấp quyền quyết định. | Vì tự nói ra chẳng khác nào "tự thú" về sự yếu kém nội bộ. | **Hỏi về các ngoại lệ và cách chữa cháy (Exceptions & Workarounds):** *"Chuyện gì xảy ra khi luồng bình thường không chạy được?", "Việc đó xảy ra bao nhiêu lần?", "Ai là người đứng ra xử lý nó?"* |

> ⚠️ **Anti-Pattern cần nhớ: Phỏng vấn luồng màu hồng (The Happy-Path Interview)**
> Nếu bạn chỉ hỏi *"Quy trình này được thiết kế hoạt động như thế nào?"*, bạn sẽ nhận được một tài liệu yêu cầu cực kỳ sạch đẹp mô tả một thứ... không ai thực sự làm theo. Sự lệch pha này sẽ nổ ra ở giai đoạn nghiệm thu (Acceptance) và bắt bạn phải thiết kế lại từ đầu.

#### 2. Bốn Thứ Phải Chốt Trước Khi Thuẹp Phạm Vi Thiết Kế (4 Outputs of Discovery)
Discovery **KHÔNG kết thúc khi các cuộc họp kết thúc**. Nó chỉ kết thúc khi **4 yếu tố sau được đồng thuận bằng văn bản (in writing)** bởi những người có thẩm quyền cam kết:

1. **The Baseline (Điểm xuất phát thực tế):** Hiệu suất hiện tại đang được **đo lường** (measured) là bao nhiêu? *(Lưu ý: Phải là con số đo đạc thực tế, không phải "nhớ mang máng". Không có nó, sau này không thể chứng minh hệ thống mới tốt hơn).*
2. **The Target (Mục tiêu):** Con số cụ thể nào, vào thời hạn nào (by when), thì được tính là thành công? *(Nếu thiếu, thành công sẽ bị phán xét cảm tính bởi sếp lớn nhất trong phòng).*
3. **The Constraints (Các ràng buộc bắt buộc):** Những giới hạn nào trói buộc thiết kế này bất kể chúng ta muốn hay không? *(Giúp chặn đứng thảm họa "đập đi xây lại ở tuần thứ 6").*
4. **The Owner (Người chịu trách nhiệm):** Ai là người chịu trách nhiệm giải trình (accountable) cho việc dịch chuyển kết quả từ Baseline lên Target, và họ có quyền cam kết không?

🚨 **CỰC KỲ QUAN TRỌNG TRONG BÀI THI: Phân biệt "Discovery Outputs" vs "Build Artifacts"**
Rất nhiều đáp án bẫy sẽ đưa các công việc của giai đoạn Build vào làm đáp án cho giai đoạn Discovery. Hãy nhớ:
* **Viết Prompt (Prompt drafts):** KHÔNG phải là Discovery. Prompt chỉ được viết và sửa liên tục trong lúc Build dựa trên tiêu chí mà Discovery bàn giao.
* **Chọn Model (Model choice):** KHÔNG phải là Discovery. Chọn model nào phụ thuộc vào yêu cầu độ chính xác, tốc độ, chi phí — mà những con số này Discovery đang phải đi tìm. Chọn model trước là giải quyết bài toán đánh đổi (trade-off) trước khi biết đề bài.
* **Thiết kế giao diện (Screen designs) / Sơ đồ kiến trúc chi tiết:** KHÔNG phải là Discovery.

#### 3. Hai Loại Yêu Cầu: Functional vs. Non-Functional (Và Bài Test 4 Giây)
Bạn phải phân loại đúng 2 nhóm này vì người ký duyệt và cách kiểm thử chúng hoàn toàn khác nhau:

* **Functional Requirement (Yêu cầu chức năng):** Mô tả **hành vi mà hệ thống phải thực hiện** cho công việc cụ thể này. 
  * *Ví dụ:* Trích xuất tổng tiền hóa đơn; Định tuyến ticket vào đúng hàng đợi; Từ chối yêu cầu nằm ngoài chính sách.
  * *Đặc điểm:* Nếu bê câu này sang một hệ thống làm nghề khác, nó sẽ trở nên vô nghĩa.
* **Non-Functional Requirement (Yêu cầu phi chức năng):** Đặt ra **giới hạn về cách thức hành vi đó được phân phối**. Đo bằng các đơn vị không liên quan đến nội dung nghiệp vụ.
  * *Ví dụ:* Độ trễ $2\text{ giây}$ ở phân vị thứ 95 ($p95$); Hệ thống sẵn sàng theo lịch đã định; Chi phí dưới $\$0.05$/giao dịch; Dữ liệu lưu trữ trong lãnh thổ Việt Nam.
  * *Tại sao nó chí mạng:* Quên Functional requirement thì chỉ thiếu 1 tính năng (xấu hổ chút nhưng code thêm được). Quên Non-functional requirement sẽ tạo ra hệ thống chạy đúng nghiệp vụ nhưng **sai tốc độ, sai vị trí địa lý, hoặc đắt gấp 10 lần ngân sách** $\rightarrow$ Phải đập đi xây lại toàn bộ kiến trúc!

> 💡 **Mẹo "Bài Test 4 Giây" để phân loại trong phòng thi:**
> Hãy nhấc nguyên câu yêu cầu đó đặt sang một hệ thống làm một việc hoàn toàn khác (ví dụ từ hệ thống Bảo hiểm sang hệ thống Đặt đồ ăn). **Nếu câu đó đọc vẫn có lý $\rightarrow$ Chắc chắn là Non-Functional Requirement** (và nó thuộc nhóm **Binding Constraints**).

#### 4. Ai KHÔNG Có Mặt Trong Phòng Sẽ Quyết Định Thứ Bạn KHÔNG Được Nghe
* Mỗi loại ràng buộc đều có một **chủ sở hữu (owner)**. Nếu chủ sở hữu đó không có mặt trong phòng họp Discovery, ràng buộc đó sẽ không được nêu ra. Đây là toán học, không phải quản trị rủi ro.
* **Cách làm đúng (Đi ngược từ danh sách ràng buộc):** Đừng chỉ mời những người do Sponsor gợi ý. Hãy liệt kê các loại ràng buộc có thể phá hủy thiết kế, rồi tìm người có thẩm quyền (authority) cho từng loại:
  * *Legal & Compliance:* Dữ liệu được phép làm gì.
  * *Security:* Ai được phép nhìn thấy dữ liệu.
  * *Operations (Vận hành):* Quy trình thực tế diễn ra thế nào vào một ngày bình thường.
  * *Finance:* Con số tài chính/chi phí phải là bao nhiêu.
  * *Nhân viên trực tiếp làm việc (Frontline workers):* Các ngoại lệ chưa từng được viết vào tài liệu.
* **Kiểm tra thực tế:** Với mỗi mảng trên, **người có thẩm quyền đã trực tiếp phát ngôn chưa**, hay bạn chỉ đang tự giả định (assuming)?
* **Tư duy nhận lỗi:** Khi một ràng buộc xuất hiện muộn làm hỏng thiết kế, **lỗi thuộc về quá trình khai thác yêu cầu (elicitation defect), KHÔNG PHẢI lỗi của khách hàng**. Đổ lỗi cho "khách hàng phức tạp" hay "stakeholder không chịu nói sớm" là tư duy sai trong bài thi.

#### 5. Những Từ Ngữ Che Giấu Sự Phức Tạp: *"Just", "Only", "Simply", "Basically"*
* Khi stakeholder nói: *"Hệ thống **chỉ cần (just/only/simply/basically)** đọc ticket và chuyển đi"*, những từ này đang nén một sự phức tạp rất lớn chưa được kiểm tra.
* Tương tự với các cụm danh từ chung chung chưa được định nghĩa: *"Yêu cầu tiêu chuẩn (Standard requests)", "Khối lượng bình thường (Normal volume)", "Phê duyệt thông thường (The usual approvals)"*.
* **Hành động của Architect:** Đừng tranh cãi về từ đó. Hãy hỏi ngay về **phần bị từ đó loại trừ**: *"Chỉ xử lý ticket tiêu chuẩn thôi à? Vậy các ticket KHÔNG tiêu chuẩn thì sao? Có bao nhiêu cái như vậy? Hiện tại ai đang xử lý chúng?"*

---

### III. BÍ KÍP NHẬN DIỆN ĐÁP ÁN SAI TRONG BÀI THI (EXAM TRAPS)
Các đáp án sai trong Chương 2 thường mô tả những hành động rất chuyên nghiệp của một kỹ sư giỏi, nhưng lại **sai thời điểm (wrong sequence)** hoặc **sai vai trò**. Hãy cảnh giác với 3 nhóm bẫy sau:

1. **Làm ra sản phẩm trước khi đạt được thỏa thuận (Producing before agreeing):**
   * *Dấu hiệu:* Đáp án đề xuất làm Prototype nhanh, viết nháp Prompt, chọn Model, vẽ màn hình UI, báo giá cố định (fixed price), hoặc bê nguyên kiến trúc của dự án cũ sang.
   * *Tại sao sai:* Làm những việc này khiến mọi cuộc họp sau đó bị cuốn vào việc "chỉnh sửa cái prototype trước mặt" thay vì trả lời câu hỏi "có nên xây cái này không?".
   * *Câu hỏi kiểm tra:* Chọn đáp án này có làm **tốn tiền, công sức kỹ thuật hoặc chốt quyết định thiết kế** cho một câu trả lời mà chưa ai chứng minh là phù hợp với bài toán gốc không?
2. **Coi ràng buộc bắt buộc như một sở thích có thể đàm phán (Treating a binding constraint as a preference):**
   * *Dấu hiệu:* Khi gặp quy định pháp lý/hợp đồng/vùng dữ liệu, đáp án lại đề xuất: *đàm phán xin ngoại lệ (negotiate an exception), trình lên sếp xin miễn trừ (escalate for a waiver), hoặc cứ làm tiếp trong lúc chờ xin phép*.
   * *Tại sao sai:* Các nghĩa vụ từ bên ngoài tổ chức (luật pháp, hợp đồng) là bất khả kháng. Cứ làm tiếp trong lúc chờ xin waiver chỉ làm tăng đống rác bạn phải vứt đi khi đơn xin bị từ chối. **Phải chấp nhận nó và lập kế hoạch lại ngay lập tức (replan now).**
3. **Đổ lỗi cho phòng họp thay vì câu hỏi (Locating the failure in the room rather than in the questions):**
   * *Dấu hiệu:* Khi yêu cầu xuất hiện trễ, đáp án kết luận rằng khách hàng này quá phức tạp, hoặc stakeholder thiếu hợp tác.
   * *Câu hỏi kiểm tra:* Liệu một **câu hỏi được đặt ra sớm hơn**, gửi đến **đúng người mà bạn hoàn toàn có thể xác định trước**, có lôi được thông tin này ra không? Nếu có $\rightarrow$ Lỗi tại quy trình Elicitation của bạn.

---

### IV. BẢNG TRA CỨU NHANH KHI LÀM BÀI (CHEAT SHEET)
*Mẹo tối thượng: Khi thấy một đáp án mô tả một việc rất hợp lý mà bạn chắc chắn sẽ làm trong dự án, hãy hỏi **"Mình sẽ làm việc này vào lúc nào?"**. Đa số đáp án sai ở chương này là **đáp án đúng cho câu hỏi của 3 tuần sau**.*

| Khi đề bài nhắc đến (Scenario Cue)... | Đáp án ĐÚNG thường là... | Cạm bẫy (TRAP) cần tránh là... |
| :--- | :--- | :--- |
| Khách hàng mô tả **thứ họ muốn bạn xây dựng** | Tách yêu cầu đó thành 2 phần: **giải pháp họ vừa gọi tên** và **vấn đề thực sự phía sau nó**, trước khi làm bất cứ việc gì khác. | Bắt tay ngay vào việc tinh chỉnh (refining), xác định phạm vi (scoping) hoặc báo giá cho thứ họ vừa nêu. |
| Một yêu cầu **xuất hiện muộn** và làm vô hiệu hóa công việc đã làm xong | Sửa lại quy trình khai thác yêu cầu (repair the elicitation): xem lại cần hỏi câu gì, và hỏi ai. | Đổ lỗi cho sự phức tạp của khách hàng, lỗi cá nhân, hoặc cố gắng đàm phán để hạ thấp yêu cầu đó xuống. |
| Một nghĩa vụ thuộc về **pháp lý (regulatory), lãnh thổ (jurisdictional) hoặc hợp đồng (contractual)** | Chấp nhận nó là ràng buộc bắt buộc (binding), và **lập lại kế hoạch ngay lập tức (replan now)**. | Đi xin giấy miễn trừ (waiver), hoặc cứ làm tiếp với giả định là sẽ xin được miễn trừ. |
| Hỏi hoạt động nào được tính là **Discovery** | Chỉ những thứ giới hạn khung thiết kế: **Measured baseline, Dated target, Binding constraints, Accountable owner**. | Viết nháp prompt, chọn model, thiết kế màn hình, vẽ sơ đồ kiến trúc (tất cả đều là Build artifacts). |
| Có một **dự án trước đây rất giống** dự án này | Phân tích đặc điểm bài toán hiện tại theo đúng bản chất của nó trước, rồi mới kiểm tra xem sự tương đồng có thực sự đúng không. | Mở đầu bằng việc áp luôn mô hình của dự án cũ vào, làm đóng băng dự án vào một sự so sánh chưa được kiểm chứng. |
| Khách hàng đề nghị **cung cấp dữ liệu Production (dữ liệu thật) ngay từ đầu** | Chốt rõ xem dữ liệu đó dùng để **trả lời câu hỏi cụ thể nào** trước đã. | Tải dữ liệu về ngay thay vì làm Discovery (việc này còn làm phát sinh rủi ro bảo mật/quyền riêng tư khi chưa chuẩn bị). |
| Quy trình được mô tả nghe **rất trơn tru, sạch sẽ** | Hỏi xem chuyện gì xảy ra vào **những ngày quy trình đó không chạy được**, và tần suất là bao nhiêu. | Ghi chép lại luồng màu hồng (happy path) và coi đó là toàn bộ quy trình thực tế. |
| Yêu cầu **phân loại một Requirement** (Functional hay Non-functional) | Chọn **Non-functional** nếu bê nguyên câu đó sang một hệ thống làm nghề khác mà đọc vẫn đúng. | Xếp các con số về độ trễ (latency), chi phí, độ sẵn sàng (availability), nơi lưu trữ (residency) vào phần mô tả công việc (job description). |

---

### V. TỔNG KẾT: 8 ĐIỀU PHẢI NHỚ THUỘC LÒNG
1. **Tách Giải pháp khỏi Vấn đề:** Yêu cầu của khách hàng luôn bọc sẵn một giải pháp. Phải bóc tách vấn đề thực sự ra trước khi tiêu tốn tài nguyên.
2. **2 loại Giả định ẩn (Undocumented Assumptions):** Loại *Hiển nhiên với họ* (pháp lý, hợp đồng $\rightarrow$ hỏi theo danh mục) và loại *Đáng xấu hổ* (quy trình thật khác giấy tờ, data bẩn $\rightarrow$ hỏi về ngoại lệ và cách chữa cháy).
3. **4 điều kiện hoàn thành Discovery (bằng văn bản):** Measured Baseline + Numeric Target (kèm ngày) + Binding Constraints + Named Owner.
4. **Không làm việc Build trong lúc Discovery:** Prompt, chọn Model, UI, Sơ đồ kiến trúc là sản phẩm của giai đoạn Build. Làm sớm sẽ đóng băng các giả định sai.
5. **Điểm danh người trong phòng:** Thiếu chủ sở hữu của loại ràng buộc nào thì sẽ bị mù thông tin ở mảng đó (Legal, Security, Ops, Finance, Frontline).
6. **Nhận trách nhiệm về Elicitation:** Yêu cầu lòi ra trễ là lỗi do mình hỏi thiếu, không phải lỗi khách hàng rắc rối.
7. **Cảnh giác với từ ngữ nén ("Just", "Only", "Simply", "Basically", "Standard"):** Luôn hỏi ngược lại về những trường hợp nằm ngoài các từ đó.
8. **Bài test 4 giây (Functional vs Non-functional):** Bê yêu cầu sang hệ thống khác mà vẫn có nghĩa $\rightarrow$ Non-functional (thuộc nhóm Binding Constraints).