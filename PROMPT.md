# AI Logic Explainer — Hoạt động 30 phút

## Mục tiêu

Sau hoạt động, sinh viên có thể:

- Diễn đạt luồng chạy của đoạn JavaScript bằng ngôn ngữ tự nhiên.
- Giải thích vai trò của `getElementById`, điều kiện kiểm tra phần tử và `addEventListener`.
- Mô tả cách `preventDefault()` và `style.display` làm thay đổi hành vi của trang.
- Nhận biết điều gì xảy ra khi một phần tử DOM không tồn tại.
- Đối chiếu câu trả lời của AI với hành vi thực tế trên trang.

## Đoạn mã cần phân tích

```javascript
// Lấy phần tử menu đăng ký và modal tương ứng
const registerMenu = document.getElementById('registerMenu');
const registerModal = document.getElementById('registerModal');
const closeModalBtn = document.getElementById('closeModalBtn');

if (registerMenu && registerModal) {
    // Sự kiện khi click hoặc rê chuột vào menu Đăng ký
    registerMenu.addEventListener('click', function(e) {
        e.preventDefault();
        registerModal.style.display = 'block'; // Hiển thị modal
    });
}

if (closeModalBtn && registerModal) {
    closeModalBtn.addEventListener('click', function() {
        registerModal.style.display = 'none'; // Đóng modal
    });
}
```

## Prompt gợi ý cho sinh viên

Hãy đọc từng câu trả lời và kiểm tra lại bằng cách nhấn menu **Đăng ký** và nút **×** trong `index.html`.

### Prompt 1 — Dịch code sang ngôn ngữ tự nhiên

> Giải thích đoạn JavaScript trên bằng tiếng Việt đơn giản, như thể đang hướng dẫn một người mới học. Chia câu trả lời theo thứ tự code chạy. Với mỗi phần, nêu rõ phần tử nào được tìm, điều kiện nào được kiểm tra và giao diện thay đổi ra sao. Không bỏ qua dòng nào.

### Prompt 2 — Theo dấu sự kiện click

> Mô phỏng chính xác điều xảy ra từ lúc người dùng nhấn menu “Đăng ký” cho đến khi modal hiện ra. Giải thích `addEventListener('click', ...)`, tham số `e`, `e.preventDefault()` và `registerModal.style.display = 'block'`. Phân biệt phần chạy ngay khi tải trang với phần chỉ chạy sau cú nhấn.

### Prompt 3 — Kiểm tra điều kiện và trường hợp thiếu phần tử

> Giải thích ý nghĩa của toán tử `&&` trong hai câu lệnh `if`. Nếu `registerMenu` không tồn tại, nếu `registerModal` không tồn tại, hoặc nếu `closeModalBtn` không tồn tại thì từng phần của chương trình sẽ làm gì? Chỉ ra phần nào vẫn có thể chạy và vì sao.

### Prompt 4 — Tìm điểm chưa chính xác hoặc dễ hiểu nhầm

> Đọc các chú thích trong code và so sánh với hành vi thật. Sự kiện được đăng ký là click hay rê chuột? `preventDefault()` ngăn hành vi mặc định nào của liên kết? Nêu chỗ nào chú thích có thể gây hiểu nhầm và đề xuất cách diễn đạt rõ hơn, nhưng không tự ý đổi logic.

### Prompt 5 — Kiểm tra hiểu bài

> Tạo 4 câu hỏi trắc nghiệm ngắn về luồng chạy của đoạn code này, mỗi câu có 4 lựa chọn và chỉ một đáp án đúng. Chưa đưa đáp án ngay; chờ tôi trả lời rồi chấm điểm và giải thích từng câu bằng tiếng Việt.

### Prompt 6 — Yêu cầu giải thích ngắn gọn

> Tóm tắt đoạn code thành tối đa 5 bước theo mẫu “Khi trang tải… / Khi nhấn Đăng ký… / Khi nhấn nút đóng…”. Cuối cùng, nêu một điều đoạn code chưa xử lý.

## Giải thích từng dòng

| Dòng | Giải thích |
| --- | --- |
| `// Lấy phần tử menu đăng ký và modal tương ứng` | Chú thích giới thiệu mục đích của nhóm lệnh tiếp theo. Chú thích không được trình duyệt thực thi. |
| `const registerMenu = document.getElementById('registerMenu');` | Tìm phần tử HTML có `id="registerMenu"` và lưu tham chiếu vào biến `registerMenu`. |
| `const registerModal = document.getElementById('registerModal');` | Tìm phần tử có `id="registerModal"` để JavaScript có thể điều khiển cửa sổ modal. |
| `const closeModalBtn = document.getElementById('closeModalBtn');` | Tìm nút có `id="closeModalBtn"`, dùng để đóng modal. |
| `if (registerMenu && registerModal) {` | Chỉ thực hiện khối lệnh bên trong nếu cả menu và modal đều tìm thấy. Giá trị `null` bị xem là sai trong điều kiện. |
| `// Sự kiện khi click hoặc rê chuột vào menu Đăng ký` | Chú thích nói “click hoặc rê chuột”, nhưng code bên dưới chỉ lắng nghe sự kiện `click`; rê chuột không tự mở modal. |
| `registerMenu.addEventListener('click', function(e) {` | Đăng ký một hàm xử lý sự kiện click trên menu. Hàm này chưa chạy ở đây; trình duyệt gọi nó khi người dùng click. |
| `e.preventDefault();` | Ngăn hành động mặc định của phần tử được click. Trong bản minh họa, menu là liên kết nên dòng này ngăn trình duyệt điều hướng tới URL trong `href`. |
| `registerModal.style.display = 'block';` | Đặt CSS inline `display` của modal thành `block`, khiến modal đang ẩn được hiển thị. |
| `});` | Kết thúc hàm xử lý click và lời gọi đăng ký sự kiện. |
| `}` | Kết thúc điều kiện kiểm tra menu và modal. |
| `if (closeModalBtn && registerModal) {` | Chỉ đăng ký sự kiện đóng khi tìm thấy cả nút đóng và modal. |
| `closeModalBtn.addEventListener('click', function() {` | Đăng ký hàm sẽ chạy khi người dùng click nút đóng. Hàm này không cần tham số sự kiện vì không sử dụng nó. |
| `registerModal.style.display = 'none';` | Ẩn modal bằng cách đặt CSS inline `display` thành `none`. |
| `});` | Kết thúc hàm xử lý click nút đóng và lời gọi đăng ký sự kiện. |
| `}` | Kết thúc điều kiện kiểm tra nút đóng và modal. |

## Thứ tự chạy

1. Khi trình duyệt đọc đến `<script>`, ba lệnh `getElementById` chạy để tìm phần tử trong trang.
2. Hai điều kiện `if` được kiểm tra; nếu đủ phần tử, các hàm xử lý click được đăng ký.
3. Chưa có modal nào được mở chỉ vì `addEventListener` được gọi.
4. Khi nhấn menu đăng ký, trình duyệt gọi hàm click: hành động mặc định của liên kết bị ngăn và modal được hiện.
5. Khi nhấn nút đóng, trình duyệt gọi hàm click thứ hai và modal được ẩn.

## Lưu ý khi thảo luận

- `getElementById()` trả về phần tử nếu tìm thấy, nếu không thì trả về `null`.
- `&&` yêu cầu cả hai vế đều đúng để vào khối `if`; đây là kiểm tra bảo vệ trước khi gọi phương thức trên phần tử.
- Chú thích “click hoặc rê chuột” không khớp với code: chỉ có sự kiện `click`.
- `preventDefault()` không hủy sự kiện click; nó chỉ ngăn hành động mặc định của phần tử.
- Đoạn code này không xử lý nhấn phím Escape, click bên ngoài modal, quản lý focus, hoặc gửi dữ liệu biểu mẫu.

## Gợi ý phân bổ 30 phút

| Thời gian | Hoạt động |
| --- | --- |
| 5 phút | Đọc code, xác định ba phần tử DOM, hai điều kiện và hai sự kiện; tự dự đoán kết quả. |
| 10 phút | Dùng Prompt 1 và Prompt 2 để yêu cầu AI dịch code và mô phỏng sự kiện click. |
| 5 phút | Dùng Prompt 3 và Prompt 4 để kiểm tra điều kiện, trường hợp thiếu phần tử và độ chính xác của chú thích. |
| 7 phút | Chạy thử trên `index.html`, đối chiếu từng bước trả lời với hành vi thực tế. |
| 3 phút | Dùng Prompt 5 hoặc Prompt 6 để tự kiểm tra và tự tóm tắt luồng chạy. |
