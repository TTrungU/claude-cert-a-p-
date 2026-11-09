# TÀI LIỆU ÔN THI CLAUDE ARCHITECT PROFESSIONAL
## Chương 1: What You Are Actually Being Asked to Decide (Bản Chất Của Việc Ra Quyết Định Thiết Kế)

---

### I. TÓM TẮT TƯ DUY CỐT LÕI (CORE MINDSET)
Khi nhận một bài toán kinh doanh và cần đưa ra kiến trúc (Solution Design), **đừng hỏi "Claude nên làm gì?"**. Hãy hỏi:
1. **Công việc nào đang được ủy quyền (delegated)?**
2. **Ủy quyền cho ai (Model, Hệ thống cố định, hay Con người)?**
3. **Chi phí/Hậu quả là gì khi đối tượng được ủy quyền làm sai?**

---

### II. GIẢI THÍCH CHI TIẾT CÁC KHÁI NIỆM TRỌNG TÂM

#### 1. Con số Độ chính xác (Accuracy %) KHÔNG phải là đầu vào thiết kế
* **Bản chất:** Tỷ lệ % (ví dụ: $99.7\%$) chỉ mô tả hành vi hệ thống, không cho biết doanh nghiệp phải gánh chịu hậu quả gì.
* **Cách xử lý trong bài thi:** 
  * Bước 1: Đổi % ra **số lượng lỗi thực tế** (Ví dụ: $99.7\%$ của $14,000$ yêu cầu/tháng = $41$ lỗi/tháng $\approx 2$ lỗi/ngày).
  * Bước 2: Hỏi **"41 lỗi đó là những lỗi cụ thể nào?"** (Which 41?).
* **Hệ quả kiến trúc:** Cùng một độ chính xác nhưng hậu quả khác nhau sẽ sinh ra kiến trúc hoàn toàn khác nhau:
  * *41 lỗi cập nhật trùng địa chỉ:* Chỉ cần một batch job dọn dẹp vào cuối ngày.
  * *41 lỗi từ chối bảo hiểm y tế:* Cần **con người kiểm duyệt (Human-in-the-loop)** trước khi gửi kết quả đi.

#### 2. Bốn đặc tính cố định của Model (Phải chấp nhận trước khi vẽ kiến trúc)
1. **Không tất định (Non-deterministic):** Cùng một đầu vào (input) có thể ra đầu ra (output) khác nhau, **ngay cả khi đặt `temperature = 0`** (trên cả API của Anthropic hay bên thứ 3). 
   * *Lưu ý thi:* Nếu đề bài yêu cầu "cùng một trường hợp phải luôn trả về cùng một kết quả", **bắt buộc phải dùng một thành phần tất định (deterministic component/code/database)** đứng cạnh model, không được dùng prompt hay chỉnh temperature.
2. **Context Window là bộ nhớ tạm (Working memory), không phải kho lưu trữ (Storage):** Nó hữu hạn. Khi đầy, độ chính xác và khả năng truy xuất giảm xuống — hiện tượng này gọi là **Context Rot** (thối rữa ngữ cảnh). Không thể thiết kế kiểu "cứ nối thêm dữ liệu mãi vào prompt".
3. **Model không biết về doanh nghiệp của bạn:** Có 2 mốc thời gian là *Reliable knowledge cutoff* (kiến thức đáng tin cậy nhất) và *Training data cutoff* (dữ liệu huấn luyện rộng hơn). Nhưng **cả hai đều không biết** bảng giá nội bộ, ngoại lệ chính sách, hay thay đổi tuần trước của công ty. Dữ liệu nội bộ phải được **truyền vào (handed to)** model mỗi lần chạy thông qua **Tools/RAG**.
4. **Sự sai sót có thể phát hiện được, nhưng phải tự xây bộ phát hiện (Detector):** Các kỹ thuật như *Chain-of-thought verification, chạy lặp lại prompt để so sánh, tinh chỉnh lặp (iterative refinement), giới hạn trong tài liệu cung cấp* đều không tự động có. Bạn phải thiết kế, trả phí độ trễ (latency) và bảo trì chúng.

#### 3. Ba Chủ Sở Hữu Công Việc (Three Owners of Work) & Cách Chúng Thất Bại
Sai lầm đắt giá nhất là giao việc sai chủ sở hữu (đặc biệt là bắt Model nhớ các dữ liệu thực tế của công ty thay vì dùng Tool để lấy từ hệ thống).

| Chủ sở hữu (Owner) | Nên giao việc gì? (Give it) | TUYỆT ĐỐI KHÔNG giao (Never give it) | Cách nó thất bại (How it fails) - *RẤT QUAN TRỌNG* |
| :--- | :--- | :--- | :--- |
| **1. Claude (Model)** | Đánh giá dữ liệu phi cấu trúc, ngôn ngữ tự nhiên, sự mơ hồ (những thứ con người thường nói "còn tùy"). | Tính toán số học cần đối soát chính xác; việc đòi hỏi kết quả giống hệt nhau mọi lần; dữ liệu gốc nằm trong hệ thống lưu trữ (System of record). | **Thất bại một cách hợp lý (Plausibly):** Trả về câu trả lời sai nhưng văn phong rất chuẩn, tự tin, không báo lỗi, nhìn trong log giống hệt câu trả lời đúng. |
| **2. Hệ thống tất định (Deterministic Systems)** | Tính toán, tra cứu (lookup), kiểm tra quyền hạn (entitlement), xác thực (validation), giữ giá trị chuẩn của dữ liệu. | Đọc hiểu và diễn giải văn bản tự do (free text) do con người viết. | **Thất bại ồn ào (Loudly):** Văng lỗi (throw exception), timeout, trả về mã lỗi. Hệ thống giám sát truyền thống phát hiện được ngay. |
| **3. Con người (Humans)** | Các quyết định cần người chịu trách nhiệm giải trình (accountable); các ngoại lệ (exceptions); các trường hợp thiết kế chưa lường trước. | Khối lượng lớn (Volume); những việc đẩy cho người chỉ vì hệ thống "lười" không chịu phân loại quyết định. | **Thất bại từ từ, rồi sụp đổ (Slowly, then all at once):** Sự tập trung giảm dần trước khi năng suất giảm. |

> 💡 **Bản chất của Tools (Function Calling):** Dùng Tool không phải để trang trí, mà là để **chuyển quyền sở hữu (change of owner)**. Khi Claude gọi Tool lấy hạn mức tín dụng, hệ thống bên ngoài chịu trách nhiệm về độ chính xác của con số đó, không phải Claude.

#### 4. Ranh giới Ủy quyền (Delegation Boundary)
Là đường ranh giới phân chia việc gì giao cho Model, việc gì giữ lại cho Code hoặc Con người. **Xác định ranh giới này bằng 3 câu hỏi (theo thứ tự):**
1. **Chi phí ẩn khi sai:** Bước này tốn kém thế nào nếu nó làm sai và **không ai nhận ra trong 1 tuần**? (Tính mức độ tích tụ hậu quả).
2. **Khả năng hoàn tác (Reversibility):** Kết quả sai có **hoàn tác (undo)** được không? (Bản nháp xóa được; tiền chuyển nhầm đòi lại được nhưng cực; tin nhắn gửi cho khách hoặc bản ghi bị xóa cứng thì KHÔNG rút lại được).
3. **Trách nhiệm cá nhân:** **Tên của ai** gắn vào đó khi nó sai? (Nếu cần một chuyên gia chịu trách nhiệm pháp lý/nghề nghiệp, thiết kế phải cung cấp đủ thông tin để họ tự đưa ra quyết định thực sự).

⚠️ **Cạm bẫy Ngưỡng Tự Tin (The Confidence-Threshold Trap):** 
* *Bẫy:* "Chỉ chuyển cho con người khi model báo độ tự tin thấp (low confidence)".
* *Tại sao sai:* Model thường làm sai những ca nghiêm trọng nhất **trong trạng thái rất tự tin**. 
* *Quy tắc vàng:* **Rủi ro/Hậu quả (Stakes) mới là thứ định tuyến công việc, KHÔNG PHẢI độ tự tin (Confidence).**

#### 5. Khung năng lực AI Fluency: Mô hình 4Ds (12 thành phần)
Bài thi sẽ dùng từ vựng của bộ 4Ds này để hỏi. Bạn cần phân biệt rõ:

* **1. Delegation (Ủy quyền - Chương 1):** Chia việc giữa người và máy.
  * *Problem Awareness:* Hiểu mục tiêu và công việc.
  * *Platform Awareness:* Biết hệ thống làm được gì và không làm được gì.
  * *Task Delegation:* Phân chia công việc.
* **2. Description (Mô tả - Chương 8):** Cách bạn ra lệnh/yêu cầu hệ thống.
  * *Product Description:* Bạn muốn tạo ra cái gì (đầu ra).
  * *Process Description:* Bạn muốn tiếp cận/xử lý nó như thế nào.
  * *Performance Description:* Bạn muốn hệ thống hành xử thế nào trong lúc làm.
* **3. Discernment (Nhận định/Đánh giá - Chương 13 & 17):** Cách bạn đánh giá kết quả trả về.
  * *Product Discernment:* Đầu ra có tốt không.
  * *Process Discernment:* Quá trình suy luận ra kết quả có hợp lý không.
  * *Performance Discernment:* Tương tác của hệ thống có hiệu quả không.
* **4. Diligence (Sự cẩn trọng/Trách nhiệm - Chương 15 & 16):** Trách nhiệm khi triển khai.
  * *Creation Diligence:* Chọn hệ thống nào và dùng ra sao.
  * *Transparency Diligence:* Ai cần được thông báo về việc model đã làm.
  * *Deployment Diligence:* Xác minh và bảo chứng cho những gì đưa lên production.

**3 Điểm cốt lõi về 4Ds cần nhớ để làm bài thi:**
1. **Vòng lặp Description - Discernment:** Chúng là 2 đầu của một vòng lặp. Khi đề bài mô tả một phát hiện ở bước **Discernment** (ví dụ: đánh giá thấy đầu ra bị lỗi logic), cách sửa lỗi thường nằm ở bước **Description** (sửa lại prompt/cách mô tả yêu cầu).
2. **3 Phương thức làm việc:** *Automation* (hệ thống làm theo lệnh cứng), *Augmentation* (người và máy cùng làm), và **Agency** (hệ thống tự hoạt động độc lập thay mặt bạn). **Hầu hết kịch bản thi đều là Agency**, nên *Delegation* và *Diligence* là quan trọng nhất.
3. **Phân biệt "Discernment" vs "Research-design caveat" (Bẫy khảo sát):**
   * Nếu một nhận xét phàn nàn về: *cỡ mẫu nhỏ, tỷ lệ phản hồi thấp, thời gian chạy pilot ngắn, chọn sai đối tượng khảo sát* $\rightarrow$ Đó là **Research-design caveat** (lỗi thiết kế nghiên cứu), **KHÔNG PHẢI Discernment**.
   * *Mẹo kiểm tra:* Câu nhận xét đó có thể viết ra **trước khi nhìn thấy kết quả của hệ thống** không? Nếu Có $\rightarrow$ Caveat (Loại đáp án này). Nếu nó chỉ ra lỗi cụ thể do hệ thống sinh ra hoặc bỏ sót $\rightarrow$ Discernment (Chọn).

#### 6. Bốn Giai Đoạn Kiến Trúc End-to-End (Và giai đoạn hay bị bỏ quên)
Một kiến trúc hoàn chỉnh bắt buộc phải có đủ 4 giai đoạn:

| Giai đoạn | Câu hỏi quyết định thiết kế | Hậu quả nếu bỏ qua |
| :--- | :--- | :--- |
| **1. Input** | Trigger là gì? Dữ liệu đến 1 lần (once), ít nhất 1 lần (at least once), hay không ổn định? | Giả định sai về khối lượng (volume), batching và độ trễ (latency). |
| **2. Processing** | Ai sở hữu bước nào? Dữ liệu thực tế là do model tự nhớ (recall) hay được truyền vào (handed)? | Model âm thầm trở thành "nguồn chân lý" cho những thứ nó không thể biết. |
| **3. Output** | Kết quả đổ về đâu? Hệ thống phía sau (downstream) có coi đây là quyết định chính thức không? | Một "bản nháp" bị biến thành "quyết định chính thức" vì đường ống không phân biệt được. |
| **4. Feedback Loop** *(Hay bị bỏ sót nhất)* | Tín hiệu báo lỗi nào sẽ **đến tay một người cụ thể (named person)**, nhanh cỡ nào, và họ phải làm gì? | Hệ thống chạy mù, không có cách nào tự báo cáo khi nó đang làm sai hàng loạt. |

⚠️ **Cạm bẫy Dashboard (The Dashboard Failure Mode):**
* *Bẫy:* "Thiết kế đã có hệ thống Observability / Dashboard / Logging xịn sò nên coi như đã có Feedback Loop".
* *Tại sao sai:* Dashboard chỉ là nơi tín hiệu nằm chờ ai đó rảnh vào xem. Nếu không có cơ chế **định tuyến tín hiệu lỗi đến một người cụ thể theo lịch trình/cảnh báo**, vòng lặp vẫn là **vòng lặp hở (open loop)**.
* *Lưu ý:* Phải thiết kế Feedback Loop **ngay từ đầu (design time)** vì nó quyết định phải log cái gì ở bước Processing và giữ lại ID nào ở bước Output.

---

### III. BÍ KÍP NHẬN DIỆN ĐÁP ÁN SAI TRONG BÀI THI (EXAM TRAPS)
Trong bài thi cấp độ Professional, các đáp án sai đều nghe rất hợp lý và chuyên nghiệp. Chúng sai vì dựa trên **4 giả định ngầm sai lầm** sau:

1. **Nhầm lẫn giữa "Cải thiện" (Improvement) và "Đảm bảo" (Guarantee):**
   * *Dấu hiệu:* Đề bài yêu cầu kết quả phải **chắc chắn/đảm bảo 100%**, nhưng đáp án lại là: *viết lại prompt rõ hơn, dùng Chain-of-Thought, chia nhỏ task*.
   * *Chốt:* Những cách đó chỉ tăng xác suất đúng, không đảm bảo 100%. Muốn đảm bảo $\rightarrow$ **Chuyển sang dùng Code/Deterministic component**.
2. **Nhầm lẫn giữa "Phát hiện" (Detection) và "Ngăn chặn" (Prevention):**
   * *Dấu hiệu:* Đề bài hỏi làm sao **tránh/ngăn chặn thiệt hại**, nhưng đáp án lại là: *lấy mẫu kiểm tra (sampling), đối soát hàng tuần, làm báo cáo kiểm toán (audit report)*.
   * *Chốt:* Đọc kỹ đề hỏi "Làm sao phát hiện ra lỗi?" (chọn Detection) hay "Làm sao ngăn chặn hậu quả?" (phải chặn trước khi Output bay ra ngoài).
3. **Nhầm lẫn giữa "Cấu trúc lại" (Restructuring) và "Chuyển giao quyền" (Reassignment):**
   * *Dấu hiệu:* Model đang bị bắt tự nhớ một thông tin nội bộ (sai chủ sở hữu). Đáp án đề xuất *tách thành 2 bước prompt nối tiếp nhau (chaining)*.
   * *Chốt:* Dù chia mấy bước thì quyền phán đoán vẫn nằm ở Model. Phải **Reassign** (dùng Tool lấy từ Database).
4. **Đánh giá sai tính Hoàn tác (Reversibility misjudged):**
   * *Dấu hiệu:* Đề xuất phân luồng kiểm duyệt dựa trên số tiền lớn/nhỏ hoặc khối lượng, khiến một hành động nhỏ nhưng **không thể hoàn tác** (gửi email thẳng cho khách) lọt qua, trong khi bắt người duyệt một việc lớn nhưng **dễ dàng hoàn tác** nội bộ.
   * *Chốt:* **Khả năng hoàn tác (Reversibility) luôn quan trọng hơn quy mô (Size/Amount).**

---

### IV. BẢNG TRA CỨU NHANH KHI LÀM BÀI (CHEAT SHEET)
*Học thuộc bảng phản xạ này để xử lý nhanh các câu hỏi tình huống (Scenario-based questions):*

| Khi đề bài nhắc đến (Scenario Cue)... | Đáp án ĐÚNG thường là... | Cạm bẫy (TRAP) cần tránh là... |
| :--- | :--- | :--- |
| Một con số **% độ chính xác (accuracy rate)** nhưng không nói rõ chi tiết lỗi | Hỏi xem các lỗi cụ thể là gì và ai phải gánh chịu hậu quả; thiết kế sẽ đi theo câu trả lời đó. | Chọn ngay kiến trúc chỉ vì thấy con số % đã cao (ví dụ 99.9%). |
| "Cùng một đầu vào **phải luôn tạo ra cùng một kết quả**" | Đưa quyết định đó vào một **thành phần tất định (deterministic component)** bên cạnh model. | Sửa prompt, hạ `temperature = 0`, hoặc chạy lấy mẫu nhiều lần (repeated sampling). |
| Một **dữ liệu thuộc về công ty**: bảng giá, quyền lợi, ngoại lệ chính sách, số dư tài khoản | **Truyền dữ liệu đó cho model** từ hệ thống sở hữu nó (thông qua Tool/API). | Bắt model tự nhớ (recall) từ kiến thức huấn luyện, dù hướng dẫn kỹ đến đâu. |
| **Văn bản tự do (Free text)** do con người viết, cần đọc hiểu/diễn giải | **Giao bước đó cho Claude (Model)** sở hữu. | Đẩy cho bộ quy tắc cứng (rules/regex) hoặc đẩy hết cho người làm vì quá cẩn thận. |
| Một hành động **rời khỏi tổ chức và không thể thu hồi** (gửi khách hàng, xóa dữ liệu) | **Con người phải duyệt quyết định** trước khi nó được gửi đi. | Định tuyến theo số lượng hoặc số tiền (cho phép các giao dịch nhỏ nhưng không thể thu hồi tự động chạy qua). |
| "Chưa ai nhận thấy lỗi cả", và yêu cầu thiết kế phải **an toàn** | Xây dựng **Feedback Loop** đẩy tín hiệu lỗi đến thẳng **một người cụ thể (named person)**. | Chỉ dựng Dashboard, hệ thống Logging hoặc Observability rồi để đó chờ người vào xem. |
| Câu hỏi chọn nhiều đáp án (Multiple choice), các phương án đều có vẻ là "Good Practice" | Chỉ chọn những phương án **thực sự làm thay đổi kết quả/chủ sở hữu**, và chỉ rõ nó thay đổi cái gì. | Chọn các phương án "best practice chung chung" nghe rất hợp lý nhưng không giải quyết gốc rễ vấn đề của đề bài. |

---

### V. TỔNG KẾT: 6 ĐIỀU PHẢI NHỚ THUỘC LÒNG
1. **Đổi % sang số đếm:** Luôn nhân % lỗi với tổng khối lượng để ra số ca lỗi cụ thể, rồi xét mức độ nghiêm trọng của từng loại ca đó.
2. **Đúng người đúng việc (3 Owners):** Claude xử lý sự mơ hồ/ngôn ngữ; Hệ thống tất định xử lý dữ liệu gốc và tính toán; Con người xử lý việc cần chịu trách nhiệm.
3. **Claude sai rất thuyết phục (Fails plausibly):** Không báo lỗi, log nhìn bình thường. Do đó kiến trúc bọc quanh model luôn phải lớn hơn bản thân model.
4. **Không có sự tất định tuyệt đối ở Model:** Ngay cả ở `temperature = 0`. Muốn kết quả giống nhau 100% mọi lần $\rightarrow$ Dùng Code/Database.
5. **3 câu hỏi vẽ Ranh giới Ủy quyền:** Chi phí tích tụ khi sai mà không ai biết là gì? Có Undo được không? Tên ai chịu trách nhiệm? *(Rủi ro định tuyến công việc, không phải độ tự tin của model)*.
6. **Đủ 4 bước (Input - Processing - Output - Feedback):** Không có tín hiệu báo về cho một người cụ thể khi sai = Chưa phải kiến trúc End-to-End (Dashboard không tính là một vòng lặp kín).