# Memo Teardown — NotebookLM

**Nhóm:** …  ·  **Thành viên:** …

**Ngày phân tích:** 14/08/2026  
**Phạm vi:** Từ Project Tailwind/NotebookLM năm 2023 đến các cập nhật agentic research, code execution và tích hợp Gemini năm 2026. Lưu ý: Google công bố đổi tên NotebookLM thành **Gemini Notebook** từ 16/07/2026, nhưng memo giữ tên NotebookLM để bám theo đề bài.

## Vì sao chọn sản phẩm này

NotebookLM là một sản phẩm AI có hướng đi khác chatbot tổng quát: bắt đầu từ nguồn tài liệu do người dùng chọn, trả lời có trích dẫn, rồi biến cùng một kho nguồn thành nhiều dạng đầu ra như study guide, audio/video overview, báo cáo và phân tích dữ liệu. Sản phẩm phù hợp để teardown vì các mốc phát triển cho thấy rõ cách Google lần lượt giải quyết ba vấn đề: **grounding**, **friction khi tiêu hóa thông tin** và **khởi động một dự án nghiên cứu**.

## §1. Timeline các cập nhật lớn

| Thời điểm | Cập nhật | Context lúc đó | Nguyên lý |
|---|---|---|---|
| 10/05/2023–07/2023 | Google giới thiệu **Project Tailwind**, sau đó mở thử nghiệm giới hạn tại Mỹ dưới tên NotebookLM. Người dùng đưa Google Docs/tài liệu của mình vào để hỏi, tóm tắt, tạo kết nối và nhận câu trả lời có trích dẫn. [Labs](https://blog.google/innovation-and-ai/products/google-labs-sign-up/) · [NotebookLM launch](https://blog.google/innovation-and-ai/technology/ai/notebooklm-google-ai/) | Chatbot tổng quát có thể trả lời nhiều chủ đề nhưng khó tạo niềm tin khi người dùng cần làm việc trên một tập tài liệu cụ thể. Google chọn nhóm người đã có nguồn — sinh viên, giáo sư, tác giả và knowledge worker — thay vì bắt đầu bằng một trợ lý biết mọi thứ. | **Grounding trước, generation sau:** Giới hạn phạm vi kiến thức vào nguồn người dùng chọn để tăng khả năng kiểm chứng; dữ liệu và hội thoại không được dùng để huấn luyện model mới theo công bố lúc ra mắt. |
| 06/06/2024 | NotebookLM dùng Gemini 1.5 Pro, mở rộng tới hơn 200 quốc gia/vùng lãnh thổ; thêm Google Slides, web URL, hiểu ảnh/biểu đồ, trích dẫn inline và Notebook guide tạo FAQ, briefing doc, study guide. [Nguồn](https://blog.google/innovation-and-ai/products/notebooklm-goes-global-support-for-websites-slides-fact-check/) | Sản phẩm đã chứng minh giá trị với người dùng Mỹ, nhưng nguồn đầu vào còn hẹp và việc kiểm tra câu trả lời vẫn cần quay lại tài liệu thủ công. Mở rộng toàn cầu đồng thời phải làm cho nguồn phong phú hơn và bằng chứng dễ nhìn hơn. | **Trust as UX:** Trích dẫn không chỉ là thuộc tính model; nó phải xuất hiện ngay trong giao diện và đưa người dùng về đúng đoạn nguồn để fact-check. |
| 11/09/2024–26/09/2024 | Ra mắt **Audio Overviews**: hai AI host biến nguồn thành cuộc thảo luận có thể tải xuống; ngay sau đó NotebookLM nhận YouTube URL và audio file, trích dẫn transcript và cho phép chia sẻ Audio Overview. [Audio Overview](https://blog.google/innovation-and-ai/products/notebooklm-audio-overviews/) · [Audio/YouTube sources](https://blog.google/innovation-and-ai/products/notebooklm-audio-video-sources/) | Tóm tắt văn bản vẫn đòi hỏi người dùng ngồi trước màn hình. Google nhận ra cùng một kho nguồn có thể được tiêu hóa khi đi lại, học tập hoặc xử lý bản ghi âm/video — và định dạng mới tạo ra trải nghiệm dễ lan truyền hơn. | **Remix tri thức để giảm friction:** Giá trị không chỉ là “trả lời đúng”, mà là đưa cùng một nguồn sang định dạng phù hợp với hoàn cảnh tiếp nhận của user. |
| 13/12/2024 | Ra mắt NotebookLM Plus, redesign thành ba vùng Sources–Chat–Studio, cho phép “Join” vào Audio Overview; Plus tăng giới hạn notebook/source/audio, tùy biến style/length, shared team notebooks, analytics và privacy/security cho tổ chức. [Nguồn](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-new-features-december-2024/) | NotebookLM đã vượt khỏi thử nghiệm cá nhân: doanh nghiệp, trường học và team cần chia sẻ kho tài liệu, quản trị usage và có lý do trả tiền. Giao diện cũng cần chuyển user liền mạch từ đọc nguồn sang hỏi rồi tạo output. | **Từ tool cá nhân thành workflow có thể bán:** Khi một sản phẩm tạo ra tài sản dùng chung và có quản trị, subscription/enterprise value xuất hiện; Studio là lớp biến insight thành deliverable. |
| 02/04/2025 | Thêm **Discover Sources**: user mô tả chủ đề, hệ thống tìm hàng trăm web source tiềm năng, chọn tối đa 10 gợi ý có chú giải và cho nhập vào notebook bằng một cú nhấp. [Nguồn](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-discover-sources/) | Mô hình cũ có một điểm nghẽn: NotebookLM rất mạnh sau khi user có nguồn, nhưng người mới có thể chưa biết bắt đầu từ đâu hoặc phải tự tìm tài liệu bên ngoài trước. | **Giảm cold-start bằng agent:** Sản phẩm không bỏ grounding; nó tự tìm nguồn nhưng vẫn đưa source vào notebook để user đọc, hỏi và kiểm chứng trước khi tạo output. |
| 19/05/2025–29/07/2025 | Mở app iOS/Android với nghe offline, tương tác với host và share-to-NotebookLM; thêm public notebooks và sau đó Video Overviews/nâng cấp Studio để tạo nhiều output audio/video/mind map/report trong một notebook. [Mobile](https://blog.google/innovation-and-ai/products/notebooklm-app/) · [Public notebooks](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-public-notebooks/) · [Video/Studio](https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-video-overviews-studio-upgrades/) | Người dùng muốn tiếp tục học khi rời desktop, chia sẻ notebook cho lớp/team/cộng đồng và dùng nội dung trực quan hơn audio. NotebookLM bắt đầu có hai phía: người tạo kho tri thức và người đến khám phá kho đã được đóng gói. | **Distribution + ecosystem moat:** Mở rộng điểm vào và khả năng chia sẻ làm tăng giá trị của notebook sau khi tạo; mỗi notebook có thể trở thành một “knowledge experience” cho nhiều người khác. |
| 08/06/2026–16/07/2026 | Google nâng cấp NotebookLM với Gemini 3.5/Antigravity, web research, secure cloud computer để viết/chạy code, tạo chart, PDF, spreadsheet, slide và nhiều định dạng; sau đó đổi tên thành **Gemini Notebook**, đồng bộ notebook với Gemini app và hướng tới Google Search. [Research upgrade](https://blog.google/innovation-and-ai/products/notebooklm/better-research-notebooklm/) · [Gemini Notebook](https://blog.google/innovation-and-ai/products/gemini-notebook/notebooklm-gemini-notebook/) | Khi nguồn có thể được tìm tự động và output đã đa dạng, giới hạn tiếp theo không còn là tóm tắt mà là phân tích, tính toán và hoàn thành một dự án nhiều bước. Google cũng cần đưa tài sản này vào hệ sinh thái Gemini để tăng tần suất sử dụng và distribution. | **Outcome over answer:** NotebookLM tiến từ “hỏi đáp trên tài liệu” sang research workspace có thể tạo bằng chứng, phân tích dữ liệu và sản phẩm đầu ra; compute, quyền truy cập và khả năng hành động trở thành lớp giá trị mới. |

### Vì sao chọn những mốc này

Các mốc được chọn vì mỗi mốc thay đổi ít nhất một trong năm yếu tố: định vị, nguồn dữ liệu, trải nghiệm đầu ra, segment/monetization hoặc mức độ tự chủ. Nhóm loại các cập nhật nhỏ về giao diện và giới hạn sử dụng nếu chúng không làm thay đổi cách user thuê sản phẩm. Chuỗi mốc cho thấy một đường đi khá nhất quán: **grounded assistant → multimodal learning tool → shared knowledge product → agentic research workspace**.

## §2. Tệp user & JTBD

### So sánh early adopters và tệp hiện tại

| | Early adopters | Tệp hiện tại |
|---|---|---|
| Đặc điểm | Người có sẵn một tập nguồn dài và cần tổng hợp: tác giả, nhà nghiên cứu, sinh viên, giảng viên, documentary/podcast researcher, consultant và knowledge worker. Họ chấp nhận thử một sản phẩm Labs, sẵn sàng tự upload tài liệu và tự kiểm tra trích dẫn. | Sinh viên/giáo viên, nhà nghiên cứu, knowledge worker, team doanh nghiệp, chủ doanh nghiệp nhỏ và người học phổ thông. Ngoài người tự tạo notebook còn có người chỉ xem hoặc tương tác với public/featured notebook. Từ 2026, tệp tiềm năng mở rộng sang người dùng Gemini cần quản lý dự án dài hơi, phân tích dữ liệu và tạo deliverable. |
| JTBD chính | “Khi tôi có nhiều tài liệu liên quan nhưng chưa nhìn ra cấu trúc và mối liên hệ, tôi muốn hỏi một trợ lý chỉ dựa trên nguồn của mình, để hiểu nhanh hơn, kiểm chứng được và có bản nháp đầu tiên.” | “Khi tôi cần học, nghiên cứu hoặc hoàn thành một deliverable từ một kho thông tin, tôi muốn bắt đầu từ ý tưởng hoặc nguồn có sẵn, để hệ thống giúp tìm nguồn, phân tích, chuyển thành text/audio/video/chart/report và chia sẻ cho người khác.” |
| Trước đó họ làm bằng cách nào | Đọc và highlight thủ công, ghi chú trong Docs/Notion, tìm kiếm nhiều tab, thuê research assistant, nghe lại phỏng vấn/lecture, tự viết outline hoặc dùng chatbot nhưng phải copy-paste tài liệu vào nhiều lượt. | Google Drive/Docs/Slides, Search, YouTube, LMS/Google Classroom, spreadsheet, công cụ transcription, podcast/YouTube và chatbot tổng quát. Team còn phải tự đóng gói tài liệu thành onboarding, training, briefing hoặc study guide. |
| Cột mốc làm thay đổi hành vi | Launch grounded với citation tạo lý do thử; cập nhật toàn cầu + Slides/web URL làm tăng loại nguồn; Audio Overview tạo “aha moment” mạnh vì biến nghiên cứu thành podcast. | Discover Sources giảm bước bắt đầu; mobile/public sharing/video tạo nhiều điểm sử dụng và người nhận; NotebookLM Plus, Gemini integration và code execution biến notebook thành tài sản workflow thay vì một lần tóm tắt. |

### Dịch chuyển tệp

NotebookLM ban đầu thắng ở nhóm **đã có nguồn và có động lực hiểu sâu**. Đây là nhóm chịu được thao tác “tạo notebook → chọn nguồn → đọc citation” vì lợi ích của việc tổng hợp lớn hơn chi phí thiết lập.

Sau đó, sản phẩm mở rộng theo ba hướng:

1. **Từ người tự mang nguồn sang người được hỗ trợ tìm nguồn:** Discover Sources làm giảm cold-start nhưng vẫn giữ notebook làm nơi kiểm chứng.
2. **Từ người đọc sang nhiều kiểu người tiêu thụ:** Audio/Video Overviews, mobile và public notebooks cho phép người nghe, người xem, học sinh hoặc đồng đội dùng output mà không cần hiểu toàn bộ quy trình research.
3. **Từ cá nhân sang tổ chức/hệ sinh thái:** Plus, shared team notebooks, Workspace/Education và đồng bộ với Gemini đưa notebook vào các workflow dài hơn như onboarding, lesson planning, nghiên cứu và phân tích dữ liệu.

Vì vậy, segment shift không đơn giản là “từ sinh viên sang tất cả mọi người”. Nó là sự chuyển từ **người dùng có một bộ tài liệu và tự vận hành công cụ** sang **người dùng thuê NotebookLM xây một lớp tri thức có thể truy vấn, remix, chia sẻ và tạo sản phẩm đầu ra**.

### Switching cost — 4 forces

| Lực | Phân tích |
|---|---|
| **Push of current situation — vấn đề với cách cũ** | Nguồn nằm rải trong PDF, Docs, Slides, email, YouTube và audio; người dùng phải đọc, ghi chú, đối chiếu và đóng gói thủ công. Với team/giáo viên, cùng một nội dung còn phải làm nhiều phiên bản cho nhiều vai trò hoặc trình độ. |
| **Pull of the new — sức hút của NotebookLM** | Grounding theo nguồn đã chọn, citation để fact-check, hỗ trợ nhiều loại nguồn, Audio/Video Overview, mind map, report, source discovery, mobile và từ 2026 là code/chart/output file. User có thể biến cùng một kho nguồn thành nhiều đầu ra mà không chuyển qua nhiều công cụ. |
| **Habit of the present — thói quen giữ user lại** | Quy trình Google Drive/Docs/Slides, Search, YouTube, Classroom, LMS và spreadsheet đã ăn sâu. Người dùng cũng quen tự đọc hoặc dùng ChatGPT/Gemini như một giao diện chung; việc tạo notebook riêng cho từng project có thể bị xem là thêm bước. |
| **Anxiety of switching — nỗi lo khi chuyển sang NotebookLM** | Citation không bảo đảm câu trả lời luôn đúng; Audio/Video có thể sai hoặc bỏ sót. User lo tài liệu nhạy cảm, quyền sở hữu nội dung, public sharing ngoài ý muốn, giới hạn nguồn/compute, chi phí Plus/AI plan và việc bị phụ thuộc vào Google account/ecosystem. |

**Lực giữ user mạnh nhất:** **chi phí tái tạo notebook và tài sản đầu ra theo thời gian**, cộng với trust từ citation. Một notebook tốt không chỉ là lịch sử chat; nó gồm nguồn, ghi chú, câu hỏi, mind map, audio/video/report và cách team dùng lại. Tuy nhiên đây vẫn là switching cost mềm: nguồn gốc thường vẫn nằm trong Drive hoặc máy người dùng, còn citation có thể được tái tạo bởi đối thủ. Moat dài hạn phải đến từ trải nghiệm đa định dạng, distribution qua Gemini/Search/Workspace/Education, dữ liệu workflow và niềm tin quản trị — không chỉ từ model.

## §3. Ba dự đoán hướng đi trong 6–12 tháng tới

### Dự đoán 1 — Mở rộng tính năng: NotebookLM sẽ trở thành agent nghiên cứu có kiểm soát

- **Dự đoán:** Trong 6–12 tháng tới, NotebookLM/Gemini Notebook sẽ đi sâu vào workflow end-to-end: nhận mục tiêu, lập kế hoạch nghiên cứu, tìm và sàng lọc nguồn, chạy phân tích bằng code, tạo chart/report/slide, rồi yêu cầu user review các nguồn và giả định trước khi xuất bản.
- **Lập luận:** Discover Sources đã giải quyết bước tìm nguồn; cập nhật 06/2026 đã thêm secure cloud computer, code, chart và nhiều loại file; đổi tên và đồng bộ với Gemini đưa notebook ra khỏi vai trò “tóm tắt tài liệu”. Chuỗi này dẫn trực tiếp đến nguyên lý **outcome over answer**, nhưng vì sản phẩm giữ citation nên dạng agent phù hợp nhất là agent có checkpoint và human review, không phải tự hành động không giới hạn.

### Dự đoán 2 — Mở rộng segment: NotebookLM sẽ đi sâu vào giáo dục và knowledge workflow của tổ chức

- **Dự đoán:** Google sẽ ưu tiên các template và quyền quản trị cho trường học, team và vai trò chuyên môn: teacher-led notebook, onboarding, sales enablement, policy/compliance, research brief và phân tích nội bộ; cùng một nguồn sẽ được đóng gói khác nhau cho học sinh, giáo viên, quản lý hoặc khách hàng.
- **Lập luận:** Plus đã thêm shared team notebooks, analytics và privacy/security; public/featured notebooks chứng minh mô hình “người tạo tri thức – người tiêu thụ tri thức”; Video Overviews cho phép tạo các phiên bản theo audience; Gemini/Workspace/Education là kênh phân phối sẵn có. Khi JTBD chuyển từ “tôi hiểu tài liệu” sang “tôi giúp người khác hiểu và hành động”, domain workflow và governance trở thành moat quan trọng hơn một câu trả lời hay.

### Dự đoán 3 — Mô hình kiếm tiền: phân tầng theo compute, nguồn và mức độ tự chủ; NotebookLM bị hấp thụ một phần vào Gemini

- **Dự đoán:** Google sẽ giữ một lớp NotebookLM/Gemini Notebook miễn phí để mở rộng distribution, nhưng phân tầng trả phí theo số notebook/source, lượt web research, code execution, dung lượng output, model reasoning, quyền chia sẻ/quản trị và các tác vụ tốn compute. Về mặt thương hiệu, NotebookLM có thể tiếp tục là trải nghiệm chuyên sâu bên trong Gemini thay vì một sản phẩm hoàn toàn độc lập.
- **Lập luận:** NotebookLM Plus đã chứng minh các giới hạn và tính năng team có thể đóng gói thành subscription; 06/2026 đưa code và nhiều output đắt hơn vào sản phẩm; 07/2026 Google công bố đổi tên thành Gemini Notebook, đồng bộ với Gemini app và hướng tới Search. Vì thế nguyên lý **capability ladder + ecosystem distribution** có khả năng thắng mô hình thu phí đơn giản chỉ theo số người dùng.

**Dự đoán tự tin nhất:** Dự đoán 1.  
**Giả định nếu sai:** Người dùng có thể không tin giao cho agent quyền tìm nguồn, chạy code hoặc tạo báo cáo ở các domain nhạy cảm. Khi đó sản phẩm sẽ giữ mô hình copilot có citation và phê duyệt từng bước; đầu tư vào audit, provenance và quyền kiểm soát sẽ quan trọng hơn tăng mức độ tự chủ.

## §4. AI Log

| Việc | AI làm hay nhóm làm? | Nhóm kiểm chứng/phán đoán lại thế nào? |
|---|---|---|
| Tìm timeline và các tính năng NotebookLM | AI hỗ trợ research, sắp xếp mốc và gợi ý nguồn | Ưu tiên blog Google/Google Labs/Google for Education; mở từng link, kiểm tra ngày, nội dung và phân biệt announcement với rollout. Không dùng snippet tìm kiếm làm bằng chứng duy nhất. |
| Chọn 8 mốc đưa vào timeline | Nhóm phán đoán | Giữ các mốc làm thay đổi định vị, nguồn đầu vào, format output, segment, monetization hoặc mức độ tự chủ; loại các bản sửa giao diện/giới hạn nhỏ. Một số mốc được gộp khi cùng thể hiện một quyết định chiến lược là remix và phân phối tri thức. |
| Viết context và revert về nguyên lý | AI hỗ trợ bản nháp; nhóm chịu trách nhiệm | Đối chiếu context với bài công bố chính thức; đánh dấu các nhãn như “Grounding trước, generation sau”, “Trust as UX” và “Outcome over answer” là diễn giải của nhóm, không phải quote của Google. |
| Phân tích early adopters, tệp hiện tại và JTBD | Nhóm phán đoán dựa trên nguồn và framework JTBD | Kiểm tra mỗi JTBD mô tả việc user cần hoàn thành, không chỉ liệt kê tính năng. Phân biệt người tạo notebook với người chỉ tiêu thụ public/featured notebook. |
| Phân tích switching cost 4 forces | Nhóm phán đoán; AI gợi ý cấu trúc | Tách “dùng nhiều” khỏi lock-in; chỉ gọi là switching cost khi việc chuyển đổi làm mất nguồn, output, workflow, trust hoặc quyền quản trị. Ghi riêng anxiety về sai citation, privacy, public sharing và compute cost. |
| Viết 3 dự đoán 6–12 tháng | Nhóm phán đoán; AI hỗ trợ phản biện | Mỗi dự đoán phải dẫn ngược về ít nhất một mốc timeline và một nhận định user. Kiểm tra không biến feature đã công bố thành “dự đoán”; phần dự đoán nằm ở mức độ tích hợp, ưu tiên segment và cách đóng gói thương mại. |
| Biên tập memo | AI hỗ trợ diễn đạt và kiểm tra logic; nhóm chịu trách nhiệm cuối | Đọc lại toàn văn theo luồng §1 → §2 → §3, kiểm tra link nguồn, tách fact khỏi inference và bổ sung giả định nếu dự đoán có thể sai. |

## Kết luận ngắn

NotebookLM không cố thắng chatbot bằng việc biết nhiều hơn mọi thứ. Nó bắt đầu bằng một lựa chọn hẹp nhưng có tính chiến lược: **chỉ làm việc trên nguồn mà user chọn và giúp user kiểm chứng**. Sau khi tạo được trust, Google mở rộng giá trị theo hai trục: remix nguồn thành audio/video/report để giảm friction, và đưa notebook vào discovery, code execution, Gemini, Workspace, Education và Search để tăng tần suất sử dụng. Moat tiềm năng vì vậy nằm ở tổng hợp của provenance/citation, format output, workflow team và distribution của Google. Rủi ro lớn nhất là sản phẩm bị kéo về hai phía: một bên là chatbot tổng quát của Gemini, bên kia là công cụ research chuyên sâu yêu cầu độ chính xác cao. Quyết định then chốt trong 6–12 tháng tới sẽ là NotebookLM giữ được “trust của nguồn” khi trở thành agent mạnh đến đâu.
