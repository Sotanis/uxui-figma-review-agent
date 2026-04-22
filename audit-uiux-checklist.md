# Checklist audit UI/UX cho CRM Mobile (RM Retail — QHKH Cá nhân) — review trên Figma

## 0) Cách dùng nhanh (recommend)
- Review theo **flow** và theo **màn hình chính** trong flow (ưu tiên audit sâu 1 flow/section thay vì toàn bộ file).
- Với mỗi màn hình: tick tiêu chí theo mức **P0/P1/P2**, chấm **Score 0–2**, ghi **Issue link** trỏ vào frame/node Figma.
- Kết luận theo **Pass / Conditional / Fail** (rubric bên dưới).
- Khi ghi issue: luôn ghi **Expected vs Observed** (1 câu) + **tác động** (time saved, error reduced, risk).
- **Evidence bắt buộc khi log issue**: `UI element + nodeId` + `Screenshot ref (image-n)` + `Figma link` + `Frequency×Impact`.

---

## 1) Rubric chấm điểm & kết luận (0–2, P0/P1/P2)

### 1.1 Score 0–2 cho từng tiêu chí
- **0 (Không đạt / rủi ro)**: thiếu, sai, mơ hồ, hoặc có thể gây lỗi nghiệp vụ/tuân thủ/giảm hiệu suất đáng kể.
- **1 (Đạt một phần)**: có nhưng chưa rõ, chưa nhất quán, thiếu edge case/state, hoặc làm RM Retail thao tác nhiều hơn cần thiết.
- **2 (Đạt tốt)**: rõ ràng, nhất quán, có đủ state/edge case liên quan, tối ưu cho thao tác nhanh & giảm lỗi.

---

## 1.0) Bối cảnh sử dụng (để audit đúng “người–việc–môi trường”)
- **Người dùng chính**: **RM Retail / QHKH Cá nhân** (nhân sự trẻ 22–30, turnover cao, workload lớn).
- **Môi trường**: làm việc **ngoài chi nhánh nhiều**, dùng **điện thoại** khi di chuyển/đi gặp KH; mạng có thể yếu/không ổn định.
- **Hành vi đặc thù**:
  - **Không thể nhớ** chi tiết 200–500 KH → cần “Customer 360 / context” cực nhanh.
  - Áp lực KPI cao → ưu tiên **tốc độ thao tác**, giảm bước nhập liệu, tránh lỗi.
  - Thường cập nhật CRM **cuối ngày** → các flow “ghi nhanh / lưu nháp / pending sync” quan trọng.

### 1.2 Mức độ ưu tiên tiêu chí
- **P0 (Must)**: ảnh hưởng trực tiếp đến hoàn thành nhiệm vụ, phòng lỗi, dữ liệu/tuân thủ, hoặc gây “kẹt flow”.
- **P1 (Should)**: tăng tốc độ/độ rõ ràng/giảm tải nhận thức; thiếu thì vẫn dùng được nhưng kém.
- **P2 (Nice)**: cải thiện trải nghiệm, thẩm mỹ, “delight”, nhưng không ảnh hưởng đáng kể đến hoàn thành nhiệm vụ.

### 1.3 Severity khi ghi issue (để triage)
- **S0 Blocker**: không thể hoàn thành nhiệm vụ; hoặc rủi ro tuân thủ/dữ liệu nghiêm trọng.
- **S1 High**: hoàn thành được nhưng dễ sai/lỗi; mất nhiều thời gian; confusion cao; sai “next step”.
- **S2 Medium**: gây khó chịu/giảm hiệu suất nhẹ; inconsistency gây chậm.
- **S3 Low**: polishing/cosmetic; không ảnh hưởng đáng kể.

### 1.3b Mapping Score / P-level / Severity (để tránh mâu thuẫn)
- **Score (0–2)**:
  - **0** = Fail (critical usability/reliability/compliance issue)
  - **1** = Partial (usable but flawed)
  - **2** = Good (meets standard)
- **Priority**:
  - **P0** = Must fix before release
  - **P1** = Should fix
  - **P2** = Nice to have
- **Severity (derived; không được mâu thuẫn với Score/P-level)**:
  - **S0** = Score 0 + P0 (hoặc rủi ro data-loss/tuân thủ)
  - **S1** = Score 0/1 + P0, hoặc Score 0 + P1
  - **S2** = Score 1 + P1/P2
  - **S3** = Score 2 với polishing notes

### 1.4 Kết luận Pass / Conditional / Fail cho mỗi màn hình/flow
- **Fail** nếu có **≥1 issue P0 ở mức S0 hoặc S1**.
- **Conditional** nếu:
  - Không có P0 S0/S1, nhưng có **≥2 issue P0 (S2+)**, hoặc
  - Tổng điểm các tiêu chí P0 của màn hình **< 70%** (tính theo số tiêu chí P0 áp dụng).
- **Pass** nếu:
  - **0 issue P0 S0/S1**, và
  - Tổng điểm P0 **≥ 70%**, và
  - Các tiêu chí P1 quan trọng không rơi vào “0” theo cụm (ví dụ: state/loading/empty).

> Gợi ý: Với Figma review, “issue P0” thường đến từ thiếu states (loading/error/empty), thiếu validation/confirm, điều hướng không rõ, hoặc đặt CTA sai.

---

## 2) Checklist cốt lõi (áp dụng cho mọi màn hình)

### 2.0 Cách ghi Issue (template tối thiểu cho mọi tiêu chí)
- **UI element + nodeId**: (vd: `PrimaryCTAButton 1200:115748`)
- **Screenshot ref**: (vd: `image-2`)
- **Expected vs Observed**: 1–2 câu
- **Frequency×Impact**: Daily/Weekly/Rare × time/error/risk
- **P-level / Severity / Score**: theo mapping ở mục 1.3b

### 2.1 Nhiệm vụ cốt lõi & ưu tiên thông tin (P0/P1)
- **P0 – Mục tiêu màn hình rõ ràng**: title/heading mô tả đúng; người dùng biết đang ở “đối tượng nào” (KH/lead/cơ hội/công việc).\n+  - **Check**: title + context (tên KH/lead/cơ hội) xuất hiện “above the fold” trên mobile.\n+  - **Fail (Score 0)** nếu user không biết đang thao tác với ai/cái gì.\n+- **P0 – CTA chính đúng & nổi bật**: đúng “next step” và không cạnh tranh với CTA phụ.\n+  - **Check**: chỉ **1** primary CTA; vị trí dễ thấy; có state disabled/loading nếu có submit.\n+  - **Fail (Score 0)** nếu thiếu CTA cho tác vụ chính hoặc có “double primary” gây nhầm.\n+- **P1 – Thứ bậc thông tin (hierarchy) hỗ trợ quét nhanh**.\n+  - **Check**: dữ liệu quan trọng (status, deadline, next action, cảnh báo) nổi bật hơn phụ.\n+- **P1 – Giảm tải nhớ (recognition > recall)**.\n+  - **Check**: label rõ + ví dụ/format; default/prefill; tránh yêu cầu user nhớ mã.\n+- **P1 – Mật độ thông tin (Data density) cân bằng**.\n+  - **Check**: user xem được đủ dữ liệu để so sánh/ra quyết định mà không phải cuộn quá nhiều; tránh khoảng trắng “lãng phí”.\n+  - **Signal**: nếu phải cuộn chỉ để thấy thông tin liên quan (owner/status/deadline/next action) → Score 0–1.

### 2.2 Điều hướng & kiến trúc thông tin (P0/P1)
- **P0 – Đường đi và đường về rõ**.\n+  - **Check**: back/close nhất quán; không “kẹt” khi từ list→detail→action.\n+- **P0 – Không mất dữ liệu khi quay lại**.\n+  - **Check**: confirm discard; draft/autosave (nếu product có).\n+  - **Fail (Score 0)** nếu có rủi ro mất dữ liệu ghi chú/form.\n+- **P1 – Search/filter entry point hợp lý**.\n+  - **Check**: trạng thái filter hiển thị (chips/badge) + clear all.\n+- **P1 – Time-to-action tối ưu**.\n+  - **Check**: CTA quan trọng không bị đẩy xuống phải cuộn; có sticky action nếu màn dài.\n+  - **Metric (optional)**: ghi lại taps/screens/scrolls cho 1 task chính.

### 2.3 Tương tác & hiệu quả thao tác (P0/P1)
- **P0 – Số bước hợp lý cho nhiệm vụ phổ biến**.\n+  - **Check**: không đi vòng; CTA nằm ở vị trí “thumb zone” (mobile).\n+- **P1 – Shortcuts cho hành động thường dùng** (call/copy/add activity).\n+  - **Check**: không giấu trong menu sâu.\n+- **P1 – Feedback tương tác**.\n+  - **Check**: pressed/selected/disabled + loading/progress cho thao tác có latency.

### 2.4 Form & phòng lỗi (P0)
- **P0 – Validation đầy đủ**.\n+  - **Check**: required/format/range; inline error gần field; error summary (optional).\n+  - **Fail (Score 0)** nếu submit được khi thiếu required mà không có hướng dẫn sửa.\n+- **P0 – Format dữ liệu rõ**.\n+  - **Check**: tiền tệ/phone/ID có mask + ví dụ; ngăn nhập sai.\n+- **P0 – Confirm cho hành động rủi ro**.\n+  - **Check**: confirm đúng lúc; nêu hậu quả; có cancel.\n+- **P1 – Khả năng khôi phục (recoverability)**.\n+  - **Check**: undo/restore/draft; đặc biệt note/task khi offline.\n+  - **Risk**: nếu không có → dễ mất dữ liệu/ghi sai.

### 2.5 System states & edge cases (P0/P1)
- **P0 – Loading/skeleton**.\n+  - **Check**: có skeleton/loading cho phần data; không “nhảy layout” quá mức.\n+- **P0 – Error state**.\n+  - **Check**: mất mạng/timeout/permission có message + next action (retry/request access).\n+  - **Fail (Score 0)** nếu user bị kẹt không biết làm gì.\n+- **P0 – Offline & đồng bộ (mobile/offline-first nếu có)**.\n+  - **Check**: có state `Pending sync / Synced / Sync failed`; có retry; có conflict guidance (nếu cần).\n+  - **Fail (Score 0)** nếu offline làm mất dữ liệu hoặc user tưởng đã lưu.\n+- **P1 – Empty state**.\n+  - **Check**: rỗng nhưng có hướng dẫn hành động.\n+- **P1 – No results**.\n+  - **Check**: gợi ý nới filter/clear.

### 2.6 Microcopy & thuật ngữ (P1)
- **P1 – Thuật ngữ nhất quán**: Lead/Prospect/Customer/Account; KPI tên rõ ràng, tránh viết tắt khó hiểu.
- **P1 – Copy hướng dẫn hành động**: nút/label dùng động từ cụ thể; tránh “OK/Submit” chung chung.

### 2.7 Visual consistency (P1)
- **P1 – Grid/spacing/type nhất quán**: cùng cấp độ thông tin dùng cùng style.
- **P1 – Component usage nhất quán**: button/input/chip/tag/status, list item, empty state.
- **P1 – Màu có ý nghĩa & không lạm dụng**: status/KPI rõ; tránh dùng màu chỉ để trang trí gây nhiễu.

### 2.8 Accessibility & inclusive (P0/P1)
- **P0 – Không phụ thuộc vào màu** để hiểu status.\n+  - **Check**: status có text/icon/label.\n+- **P1 – Contrast (WCAG 2.1)**.\n+  - **Check**: CTA/text quan trọng đạt AA (4.5:1 cho text thường; 3:1 cho large).\n+  - **Log**: nếu đo/ước lượng được từ token → ghi ratio; nếu không → “Not verifiable”.\n+- **P1 – Tap target / Focus states**.\n+  - **Check (mobile)**: touch target tối thiểu **44×44px** cho icon buttons/controls.\n+  - **Check (web)**: focus/hover rõ.\n+  - **Fail (Score 0)** nếu control quan trọng quá nhỏ gây thao tác lỗi.

### 2.9 Tin cậy, bảo mật, tuân thủ (P0)
- **P0 – Dữ liệu nhạy cảm**: mask/permission-based; tránh hiển thị dư thừa.
- **P0 – Rủi ro rò rỉ dữ liệu**: copy/share/export có thiết kế cảnh báo/giới hạn khi phù hợp.
- **P1 – Auditability theo UX** (nếu yêu cầu): “last updated”, nguồn dữ liệu, ai thay đổi trạng thái/owner.
- **P0 – Data freshness cho dữ liệu quyết định**: nếu dữ liệu ảnh hưởng quyết định (KPI, SLA, trạng thái), phải có cơ chế thể hiện “cập nhật gần nhất/đang đồng bộ/không mới”.

---

## 3) Checklist đặc thù theo flow

### 3.1 Flow A — Lead → Customer
#### Lead List (P0/P1)
- **P0 – Trạng thái lead rõ**: hot/warm/cold, stage, SLA, last contact.
  - **Check**: mỗi item có stage/status + SLA/last contact; trạng thái nhất quán.
  - **Fail (Score 0)**: RM không phân biệt được lead ưu tiên hoặc trễ SLA.
  - **Evidence**: list item nodeId + screenshot ref.
- **P1 – Sort/filter ưu tiên đúng**: theo SLA, last touch, score, segment.
  - **Check**: filter state hiển thị (chips/badge) + clear all.
  - **Evidence**: filter nodeId + screenshot ref.
- **P1 – Hành động nhanh**: call/message/add activity/assign.
  - **Check**: ≤2 taps từ list tới action phổ biến; không giấu quá sâu.
  - **Metric (optional)**: taps/screens.

#### Lead Detail (P0/P1)
- **P0 – CTA chính phù hợp**: Convert / Add Activity / Call.
  - **Check**: chỉ 1 primary CTA; không bị “chìm” dưới fold.
  - **Fail (Score 0)**: thiếu next step hoặc “double primary”.
  - **Evidence**: CTA nodeId + screenshot ref.
- **P0 – Thông tin liên hệ dễ dùng**.
  - **Check**: phone/email có affordance (copy/call) + permission state.
  - **Fail (Score 0)**: call/copy không rõ hoặc permission kẹt không có hướng dẫn.
  - **Evidence**: contact action nodeId + screenshot ref.
- **P1 – Lịch sử tương tác**.
  - **Check**: last contact time + outcome; có lối thêm activity.
  - **Evidence**: timeline snippet nodeId + screenshot ref.

#### Convert Flow (P0)
- **P0 – Stepper/tiến trình rõ**.
  - **Check**: step 1/2/3; điều kiện hoàn tất; back không mất dữ liệu.
  - **Fail (Score 0)**: user không biết còn bước nào hoặc back làm mất dữ liệu.
  - **Evidence**: stepper nodeId + screenshot ref.
- **P0 – Mapping dữ liệu minh bạch**.
  - **Check**: field prefill vs required bổ sung; label rõ.
  - **Fail (Score 0)**: mapping mơ hồ gây nhập sai/thiếu.
  - **Evidence**: mapping field nodes + screenshot ref.
- **P0 – Xử lý trùng lặp (duplicate)**.
  - **Check**: state phát hiện trùng + lựa chọn merge/link/cancel.
  - **Fail (Score 0)**: có nguy cơ tạo trùng KH không kiểm soát.
  - **Evidence**: duplicate state nodeId + screenshot ref.
- **P0 – Confirm/undo strategy**.
  - **Check**: confirm nêu hậu quả; nếu không undo phải nói rõ.
  - **Evidence**: confirm modal/bottom-sheet nodeId + screenshot ref.

#### Ownership/Assignment (P0/P1)
- **P0 – Đổi owner có guardrails**.
  - **Check**: hiển thị owner hiện tại; đổi owner có confirm + lý do (nếu policy yêu cầu).
  - **Fail (Score 0)**: đổi owner gây mất kiểm soát/audit.
  - **Evidence**: assignment control nodeId + screenshot ref.
- **P1 – Quy tắc phân bổ rõ**.
  - **Check**: auto-assigned có nhãn + giải thích ngắn.
  - **Evidence**: assignment note nodeId + screenshot ref.

---

### 3.2 Flow B — Customer 360
#### Tổng quan 30 giây (P0/P1)
- **P0 – “What matters now”**: next action, mức độ ưu tiên, sản phẩm chính, cảnh báo/rủi ro liên quan.
- **P0 – Định danh KH rõ**: tên, mã/ID (nếu dùng), segment; tránh nhầm KH.
- **P1 – Tóm tắt giá trị**: portfolio/AUM/limit/relationship summary (tuỳ sản phẩm) hiển thị gọn, dễ quét.

#### Tabs/Sections & thông tin sâu (P0/P1)
- **P0 – IA không quá tải**: nhóm thông tin theo mục tiêu (Timeline, Products, Opportunities, Notes, Documents).
- **P1 – Progressive disclosure**: chi tiết sâu nằm sau “View more/expand”, không đẩy RM đọc dài ngay.

#### Search nâng cao trong Customer 360 (P0/P1)
- **P0 – Tìm kiếm theo định danh quan trọng**: số tài khoản / số điện thoại / CCCD.
  - **Check**: nhận diện loại input (mask/format) + xử lý “no match”.
  - **Fail (Score 0)**: không thể tìm nhanh theo định danh phổ biến.
  - **Evidence**: search input nodeId + screenshot ref.
- **P1 – Auto-suggestion & ưu tiên kết quả**.
  - **Check**: suggestion theo history; ưu tiên exact match; candidate đủ để tránh chọn nhầm.
  - **Evidence**: suggestion dropdown nodeId + screenshot ref.

#### Timeline / Interactions (P0/P1)
- **P0 – Thứ tự thời gian rõ**: timestamp, kênh (call/meeting), outcome; phân biệt note vs activity.
- **P0 – Add activity nhanh**: CTA rõ, prefill khách hàng; validation tối thiểu.
- **P1 – Filter timeline**: theo loại tương tác; trạng thái filter hiển thị rõ.

#### Dữ liệu nhạy cảm & tuân thủ (P0)
- **P0 – Masking/permission**: trường nhạy cảm có state “no access” + hướng dẫn xin quyền.
- **P0 – Copy/download**: nếu cho phép, có ràng buộc/trace hoặc cảnh báo phù hợp.

---

### 3.3 Flow C — KPI Dashboard
#### Tổng quan KPI (P0/P1)
- **P0 – Scope thời gian rõ**: MTD/QTD/YTD hoặc custom; hiển thị prominently.
- **P0 – Định nghĩa KPI rõ**: tooltip/legend; tránh KPI tên giống nhau gây nhầm.
- **P1 – Thứ bậc KPI**: KPI chính nổi bật; KPI phụ nhóm theo mục tiêu (acquisition, activity, conversion, revenue).

#### Target vs Actual & diễn giải (P0/P1)
- **P0 – So sánh với target rõ**: actual/target/% attainment; trạng thái đạt/chưa đạt không chỉ bằng màu.
- **P1 – Khuyến nghị hành động**: “what to do next” (vd: tăng follow-up, ưu tiên lead nóng) nếu sản phẩm có.

#### Drill-down (P0)
- **P0 – Drill-down hợp lý**: click KPI → danh sách lead/customer/case liên quan; có filter sẵn.
- **P0 – Không “dead end”**: từ drill-down có đường quay về dashboard và giữ context filter.

#### Data freshness (P0/P1)
- **P0 – Cập nhật gần nhất**: timestamp + nguồn (nếu cần); tránh quyết định dựa trên dữ liệu cũ.
- **P1 – State “data stale”**: cảnh báo nhẹ + hướng dẫn refresh/đợi sync.

---

## 4) System feedback (áp dụng cho nhiều flow)
- **P0 – Phản hồi sau hành động**.\n+  - **Check**: lưu note/đổi trạng thái/upload phải có success/fail; fail có next action.\n+  - **Fail (Score 0)** nếu user không biết hành động đã thành công chưa.\n+- **P1 – Toast/snackbar placement**.\n+  - **Check**: không che CTA; auto-dismiss hợp lý; có dismiss.\n+  - **Copy**: “Đã lưu” / “Chưa đồng bộ (sẽ đồng bộ khi có mạng)” / “Không lưu được – Thử lại”.

---

## 5) Review hygiene (để tăng tính khách quan khi nhiều người review)
- **P0 – Issue phải có bằng chứng**: mỗi issue bắt buộc có **UI element+nodeId** + **screenshot ref** + **Figma link** + **Expected vs Observed** + **Severity (S0–S3)**.
- **P1 – Ưu tiên theo Frequency × Impact**: ghi thêm “tần suất dùng” (Daily/Weekly/Rare) và “impact” (time/error/risk) để sắp xếp backlog khách quan.
- **P1 – Consistency audit có số liệu**: đếm nhanh số điểm “lệch hệ thống” (detached style/one-off pattern) theo màn/flow để so sánh các màn và phát hiện hotspot.

### 5.1 Design system & Token debt (để hỗ trợ audit)
- **P1 – DS compliance snapshot**: ghi nhận nhanh theo màn/flow:\n+  - % component reuse (ước lượng), số detached style, số one-off spacing/radius.\n+- **P1 – Style Debt** (khi có token JSON chuẩn): màu/font/spacing không nằm trong token list phải log thành issue “Style Debt” (S2–S1 tuỳ phạm vi ảnh hưởng/theme).\n+  - **Evidence**: layer/component name + current value + expected token.

#### Token/Style Debt khi CHỈ có Figma Variables (không có token JSON)
- **P1 – Variable-binding debt (Unbound)**:\n+  - **Check**: các layer quan trọng (surface, text, border, icon, CTA) có **boundVariables** hoặc dùng style/variable chuẩn; tránh raw hex/fallback.\n+  - **Log**: `Style Debt: Unbound` khi phát hiện paint/text không bind variable trong khi DS đã có.\n+- **P1 – One-off value debt**:\n+  - **Check**: cùng semantic (vd: Primary CTA) nhưng dùng 2 giá trị khác nhau giữa frames; hoặc có giá trị “lẻ” không theo nhịp spacing.\n+  - **Log**: `Style Debt: One-off` + phạm vi ảnh hưởng (1 screen vs cross-screen).\n+- **Evidence bắt buộc**: layer/component name + nodeId + current value + (nếu biết) expected variable/style name.

