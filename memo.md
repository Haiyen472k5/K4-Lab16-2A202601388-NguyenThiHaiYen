# Memo Teardown — ChatGPT

**Nhóm:** …  ·  **Thành viên:** …

**Ngày phân tích:** 14/08/2026  
**Phạm vi:** Các quyết định sản phẩm công khai từ khi ChatGPT ra mắt đến hướng agentic research/action năm 2025.

## Vì sao chọn sản phẩm này

ChatGPT là một sản phẩm AI có đủ dữ liệu công khai để quan sát quá trình chuyển đổi từ một chatbot thử nghiệm thành một nền tảng trợ lý đa phương thức, có mô hình trả phí, doanh nghiệp, hệ sinh thái GPT tùy biến và khả năng thực hiện công việc. Sản phẩm cũng phù hợp để luyện product sense vì mỗi giai đoạn đều cho thấy một lựa chọn khác nhau về phân phối, monetization, capability và mức độ tự chủ của AI.

## §1. Timeline các cập nhật lớn

| Thời điểm | Cập nhật | Context lúc đó | Nguyên lý |
|---|---|---|---|
| 30/11/2022 | OpenAI ra mắt ChatGPT dưới dạng research preview miễn phí; giao diện hội thoại hỗ trợ hỏi tiếp, thừa nhận sai và từ chối yêu cầu không phù hợp. [Nguồn](https://openai.com/index/chatgpt/) | Người dùng đã quen với tìm kiếm và trợ lý giọng nói, nhưng chưa có sản phẩm đại chúng nào cho phép đối thoại tự nhiên với mô hình ngôn ngữ. OpenAI cần quan sát các điểm mạnh, điểm yếu và failure mode trong sử dụng thật. | **Vòng lặp học:** Đưa sản phẩm ra sớm để thu feedback và dữ liệu hành vi, sau đó dùng chính việc triển khai để cải thiện sản phẩm. |
| 01/02/2023 | Ra mắt ChatGPT Plus với giá 20 USD/tháng, ưu tiên truy cập, tốc độ cao hơn và quyền dùng tính năng mới; vẫn duy trì gói miễn phí. [Nguồn](https://openai.com/index/chatgpt-plus/) | Nhu cầu tăng nhanh tạo áp lực về năng lực máy chủ. Người dùng đã bắt đầu dùng ChatGPT cho viết, brainstorm, lập trình và học tập, tức là có những use case đủ giá trị để trả tiền. | **Free distribution, paid depth:** Dùng gói miễn phí để mở rộng phễu; thu tiền từ người dùng có nhu cầu cao để tài trợ năng lực và thử nghiệm sản phẩm. |
| 14/03/2023 | GPT-4 được đưa vào ChatGPT Plus với giới hạn sử dụng; bản miễn phí chưa được nâng cấp ở thời điểm ra mắt. [Nguồn](https://openai.com/index/gpt-4-research/) | Chất lượng mô hình trở thành yếu tố phân biệt rõ giữa các nhóm người dùng. Người dùng chuyên nghiệp sẵn sàng đánh đổi chi phí và giới hạn tốc độ để có khả năng suy luận tốt hơn. | **Capability ladder:** Biến tiến bộ của model thành các tầng giá trị trong cùng một sản phẩm, thay vì bắt người dùng chuyển sang công cụ khác. |
| 28/08/2023 | Ra mắt ChatGPT Enterprise với bảo mật, SSO, quản trị, ngữ cảnh dài hơn, phân tích dữ liệu và cam kết không dùng dữ liệu doanh nghiệp để huấn luyện model. [Nguồn](https://openai.com/index/introducing-chatgpt-enterprise/) | ChatGPT đã lan vào tổ chức nhưng doanh nghiệp cần kiểm soát dữ liệu, quyền truy cập, thanh toán và triển khai quy mô lớn. Rào cản chính không còn chỉ là “model có thông minh không” mà là “có an toàn để đưa vào workflow không”. | **Trust as product / moat:** Trong enterprise, bảo mật, quản trị và khả năng triển khai là một phần của sản phẩm; chúng tạo moat khó sao chép hơn một giao diện chatbot. |
| 06/11/2023–10/01/2024 | OpenAI cho phép tạo GPT tùy biến, sau đó mở GPT Store để tìm và chia sẻ các GPT; người dùng có thể thêm hướng dẫn, kiến thức và actions cho mục đích cụ thể. [GPTs](https://openai.com/index/introducing-gpts/) · [GPT Store](https://openai.com/index/introducing-the-gpt-store/) | Một chatbot tổng quát khó bao phủ mọi workflow. Cộng đồng có thể tự tạo lớp chuyên môn và use case mới nhanh hơn đội sản phẩm trung tâm. | **Platform/ecosystem moat:** Mở rộng sản phẩm bằng builder, nội dung và distribution của cộng đồng; giá trị không chỉ nằm ở model mà còn ở các workflow được xây trên model. |
| 13/05/2024 | Ra mắt GPT-4o và mở thêm nhiều năng lực cho người dùng miễn phí; model xử lý text, audio, image và video với tương tác gần thời gian thực. [Nguồn](https://openai.com/index/gpt-4o-and-more-tools-to-chatgpt-free/) | Người dùng không muốn phải chọn công cụ riêng cho text, ảnh, giọng nói và dịch thuật. Độ trễ hội thoại trở thành một phần của trải nghiệm, đặc biệt với voice. | **x10 bằng cách giảm friction:** Một model đa phương thức, nhanh và dễ tiếp cận làm tăng số tình huống mà người dùng có thể đưa vào ChatGPT, thay vì chỉ cải thiện một benchmark. |
| 12/09/2024 | Đưa o1-preview vào ChatGPT và API; model được huấn luyện để dành nhiều thời gian suy nghĩ hơn cho các bài toán khó về toán, khoa học và lập trình. [Nguồn](https://openai.com/index/introducing-openai-o1-preview/) | Không phải tác vụ nào cũng cần câu trả lời tức thời. Khi độ khó và giá trị của câu trả lời tăng, người dùng chấp nhận chờ lâu hơn để đổi lấy suy luận tốt hơn. | **Right model for the job:** Tách trải nghiệm “nhanh và đủ tốt” khỏi “chậm nhưng suy luận sâu”, cho người dùng lựa chọn theo giá trị và độ khó của công việc. |
| 02/02/2025–17/07/2025 | Deep research chuyển ChatGPT từ trả lời sang tự nghiên cứu nhiều bước; ChatGPT agent tiếp tục kết hợp nghiên cứu, trình duyệt, terminal và hành động trên web. [Deep research](https://openai.com/index/introducing-deep-research/) · [Agent](https://openai.com/index/introducing-chatgpt-agent/) | Sau khi chatbot đã trở thành nơi hỏi và tạo nội dung, bước tiếp theo là giao cho AI một mục tiêu dài hơn. Tuy nhiên, quyền truy cập dữ liệu và khả năng hành động làm tăng rủi ro sai, lộ dữ liệu và thao tác ngoài ý muốn. | **Outcome over answer:** Chuyển giá trị từ “một câu trả lời hay” sang “hoàn thành một nhiệm vụ”; khả năng tự chủ phải đi cùng kiểm soát, phê duyệt và safety. |

### Vì sao chọn những mốc này

Các mốc trên được chọn vì chúng là thay đổi về **định vị, mô hình kinh doanh, nhóm khách hàng, capability hoặc mức độ tự chủ**, không phải các bản vá nhỏ. Những mốc bị loại gồm các cập nhật giao diện, tăng giới hạn hoặc sửa lỗi không làm thay đổi cách người dùng thuê sản phẩm. Chuỗi mốc cho thấy ba lần chuyển quan trọng: từ chatbot sang sản phẩm trả phí; từ sản phẩm cá nhân sang nền tảng cho tổ chức/cộng đồng; và từ công cụ trả lời sang trợ lý có thể nghiên cứu và hành động.

## §2. Tệp user & JTBD

### So sánh early adopters và tệp hiện tại

| | Early adopters | Tệp hiện tại |
|---|---|---|
| Đặc điểm | Developer, sinh viên, writer và knowledge worker thích thử công nghệ mới; thường theo dõi AI, chấp nhận output chưa ổn định và sẵn sàng tự viết prompt. Họ ưu tiên khả năng mới hơn độ hoàn thiện. | Người dùng phổ thông, người đi làm tri thức, giáo viên/sinh viên, creator và team doanh nghiệp. Họ dùng ChatGPT cho thông tin, hướng dẫn thực tế, viết, lập kế hoạch, phân tích và ngày càng nhiều workflow có file, ảnh, voice hoặc web. Nghiên cứu usage của OpenAI cho thấy ba nhóm lớn là practical guidance, seeking information và writing. [Nguồn](https://openai.com/index/how-people-are-using-chatgpt/) |
| JTBD chính | “Khi tôi gặp một bài toán hoặc trang giấy trắng, tôi muốn trò chuyện với một model có thể giải thích, brainstorm, sửa code hoặc tạo bản nháp, để tôi có điểm bắt đầu nhanh hơn dù vẫn phải tự kiểm tra.” | “Khi tôi cần hoàn thành một việc thực tế hoặc ra quyết định, tôi muốn đưa yêu cầu, file, hình ảnh hoặc câu hỏi vào một nơi có thể tìm hiểu, tổng hợp, tạo nội dung và hỗ trợ hành động, để giảm thời gian chuyển đổi giữa nhiều công cụ.” |
| Trước đó họ làm bằng cách nào | Google Search, Stack Overflow, documentation, đồng nghiệp, viết từ đầu, IDE và các công cụ riêng lẻ. | Search engine, email, tài liệu văn phòng, spreadsheet, chuyên gia/đồng nghiệp, công cụ viết, công cụ dịch, công cụ phân tích và dịch vụ research riêng. Với doanh nghiệp, họ còn phải tự đánh giá phần mềm về bảo mật và quản trị. |
| Cột mốc làm thay đổi hành vi | Research preview miễn phí và Plus làm giảm chi phí thử nghiệm, sau đó GPT-4 tạo lý do rõ ràng để dùng thường xuyên hoặc trả tiền. | GPT-4o đưa text/voice/image đến đông người dùng hơn; Enterprise, GPTs, deep research và agent đưa ChatGPT vào workflow nhóm, chuyên môn và nhiệm vụ nhiều bước. |

### Dịch chuyển tệp

ChatGPT ban đầu thắng nhờ **người dùng có khả năng tự khám phá**: họ biết mô tả vấn đề, chịu được hallucination và tự kiểm chứng. Sau đó, sản phẩm mở rộng bằng ba hướng:

1. **Giảm yêu cầu kỹ năng:** GPT-4o, voice, image và các công cụ tích hợp giúp người dùng không cần biết nhiều về prompt hay chọn model.
2. **Tăng độ tin cậy để đi vào tổ chức:** Enterprise bổ sung privacy, admin, SSO và kiểm soát dữ liệu.
3. **Tăng độ sâu của công việc:** GPTs, deep research và agent biến ChatGPT từ nơi hỏi đáp thành lớp workflow có thể tái sử dụng và thực thi.

Vì vậy, segment shift không phải từ “developer sang tất cả mọi người” một cách đơn giản. Đó là sự dịch chuyển từ **người dùng tự vận hành công cụ AI** sang **người dùng thuê ChatGPT hoàn thành một kết quả**, trong đó nhóm doanh nghiệp cần thêm lớp quản trị và an toàn.

### Switching cost — 4 forces

| Lực | Phân tích |
|---|---|
| Push of current situation — vấn đề với cách cũ | Tìm kiếm và ghép thông tin mất thời gian; tài liệu, email, spreadsheet và công cụ chuyên biệt bị chia cắt; việc bắt đầu viết, học một chủ đề hoặc phân tích dữ liệu thường có chi phí chuyển đổi cao. |
| Pull of the new — sức hút của ChatGPT | Một giao diện hội thoại cho nhiều loại việc; model ngày càng mạnh; hỗ trợ text, image, voice, file, web research và agent; người dùng có thể bắt đầu từ câu hỏi tự nhiên thay vì học một phần mềm mới. |
| Habit of the present — thói quen giữ user lại với cách cũ | Google, Office, IDE, Slack và quy trình của đội nhóm đã thành thói quen. Người dùng cũng quen tự kiểm tra bằng nguồn riêng và có thể không muốn giao việc quan trọng cho AI. |
| Anxiety of switching — nỗi lo khi chuyển sang ChatGPT | Sợ hallucination, thông tin cũ, rò rỉ dữ liệu, chi phí subscription, output thiếu trách nhiệm và agent thao tác sai. Doanh nghiệp còn lo compliance, quyền truy cập và audit. |

**Lực giữ user mạnh nhất:** sự kết hợp giữa **thói quen workflow mới** và **utility mở rộng theo thời gian**. Một user càng dùng ChatGPT cho nhiều loại việc, càng tạo lịch sử hội thoại, GPT tùy biến, cách prompt, file và thói quen kiểm tra riêng. Tuy nhiên đây là switching cost mềm, chưa phải lock-in tuyệt đối: nếu đối thủ có model tốt hơn, giá thấp hơn hoặc tích hợp sâu hơn vào nơi user đang làm việc, user vẫn có thể chuyển. Do đó moat thực tế của ChatGPT phải đến từ cả model, distribution, ecosystem, trust và workflow.

## §3. Ba dự đoán hướng đi trong 6–12 tháng tới

### Dự đoán 1 — Mở rộng tính năng: ChatGPT sẽ ưu tiên “agent hoàn thành việc” hơn “chat trả lời câu hỏi”

- **Dự đoán:** ChatGPT sẽ tiếp tục gộp research, browser, file, terminal, connectors và các thao tác có phê duyệt vào những workflow end-to-end; người dùng chỉ nêu mục tiêu, còn hệ thống tự chọn model và công cụ.
- **Lập luận:** Deep research đã chuyển từ trả lời sang nghiên cứu nhiều bước, còn ChatGPT agent đã kết hợp research với hành động. Đây là hướng phát triển trực tiếp từ nguyên lý **outcome over answer** ở §1, đồng thời khớp với JTBD hiện tại: người dùng muốn hoàn thành việc thực tế chứ không chỉ nhận một đoạn văn.

### Dự đoán 2 — Mở rộng segment: ChatGPT sẽ đi sâu hơn vào workflow doanh nghiệp và vai trò chuyên môn

- **Dự đoán:** OpenAI sẽ tăng các gói và workflow theo chức năng như phân tích dữ liệu, sales/marketing, customer support, finance, education và research; trọng tâm là dữ liệu nội bộ, quyền truy cập, audit và template dùng chung.
- **Lập luận:** Enterprise đã bổ sung security, SSO, admin và data controls; GPTs tạo lớp tùy biến theo domain; agent mở ra khả năng làm việc trên hệ thống thật. Khi tệp hiện tại đã gồm tổ chức và knowledge worker, moat không thể chỉ là model tổng quát mà phải là **trust as product** và domain workflow.

### Dự đoán 3 — Thay đổi mô hình kiếm tiền: giá sẽ phân tầng theo compute, autonomy và mức độ rủi ro

- **Dự đoán:** Các gói trả phí sẽ phân biệt rõ hơn theo tốc độ, model reasoning, số lượt research/agent, quyền kết nối dữ liệu và tính năng quản trị; những tác vụ dùng nhiều compute hoặc có khả năng hành động sẽ nằm ở tầng cao hơn.
- **Lập luận:** Plus đã chứng minh người dùng trả tiền cho access và capability; o1 cho thấy reasoning có cost/latency khác chat nhanh; deep research và agent dùng nhiều tài nguyên hơn, lại có rủi ro cao hơn. Vì vậy nguyên lý **capability ladder** sẽ tiến thành pricing theo giá trị của outcome và chi phí tự chủ, trong khi gói miễn phí tiếp tục giữ vai trò distribution.

**Dự đoán tự tin nhất:** Dự đoán 1.  
**Giả định nếu sai:** Người dùng có thể không muốn agent tự hành động vì thiếu tin cậy hoặc rủi ro bảo mật; khi đó ChatGPT sẽ bị giữ ở vai trò copilot có người phê duyệt từng bước, thay vì tự động hóa end-to-end.

## §4. AI Log

| Việc | AI làm hay nhóm làm? | Nhóm kiểm chứng/phán đoán lại thế nào? |
|---|---|---|
| Tìm và tổng hợp các cột mốc công khai của ChatGPT | AI hỗ trợ research và lập danh sách nguồn | Nhóm phải mở từng link nguồn gốc, kiểm tra ngày, nội dung cập nhật và loại bỏ mốc chỉ là bản vá nhỏ. |
| Chọn 8 cột mốc đưa vào timeline | Nhóm phán đoán | Dùng tiêu chí: mốc có làm thay đổi định vị, pricing, segment, capability hoặc mức độ tự chủ không? Nếu không, loại khỏi timeline. |
| Viết context của từng mốc | AI hỗ trợ bản nháp; nhóm chịu trách nhiệm | Đối chiếu với nội dung công bố chính thức và phân biệt fact với inference. Các nguyên lý như “vòng lặp học”, “trust as product” và “outcome over answer” là diễn giải của nhóm, không phải trích dẫn nguyên văn từ OpenAI. |
| Phân tích early adopters, tệp hiện tại và JTBD | Nhóm phán đoán dựa trên nguồn và framework JTBD | Kiểm tra mỗi JTBD có viết theo việc cần làm, không viết theo tên tính năng; kiểm tra segment có đủ cụ thể để hình dung một người dùng thật. |
| Phân tích switching cost 4 forces | Nhóm phán đoán; AI giúp gợi ý cấu trúc | Nhóm chất vấn lực nào thực sự giữ user lại, phân biệt “dùng nhiều” với lock-in, và ghi rõ anxiety về hallucination/privacy/agent risk. |
| Viết 3 dự đoán 6–12 tháng | Nhóm phán đoán; AI hỗ trợ phản biện | Mỗi dự đoán phải trỏ ngược về ít nhất một cột mốc và một nhận định về user; nhóm tự đánh dấu giả định có thể làm dự đoán sai. |
| Biên tập memo theo template | AI hỗ trợ biên tập và diễn đạt | Nhóm đọc toàn văn, kiểm tra logic §1 → §2 → §3, kiểm tra link và thay các câu chung chung bằng lập luận cụ thể. |

## Kết luận ngắn

ChatGPT không chỉ thắng nhờ model tốt hơn. Chuỗi quyết định quan trọng là: dùng research preview để học nhanh; tạo paid tier để duy trì scale; dùng model mới để nâng capability; xây trust cho doanh nghiệp; mở ecosystem cho cộng đồng; giảm friction bằng multimodal; rồi chuyển từ trả lời sang nghiên cứu và hành động. Moat dài hạn vì thế nằm ở tổng hợp của model, distribution, ecosystem, trust và workflow — không nằm ở một lớp chat đơn lẻ.

