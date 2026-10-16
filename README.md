Phần 1. Phân tích: Sai lầm của Nam và ưu thế của Markdown
1. Hai sai lầm trong tư duy của Nam khi dùng Rich Text cho lưu trữ mã nguồn
Sai lầm 1: Nhầm lẫn giữa văn bản định dạng đóng (Binary/Rich Text) và mã nguồn/tài liệu cộng tác.

Định dạng .docx của Microsoft Word không phải là văn bản thô mà thực chất là một gói nén ZIP chứa các tệp XML định dạng kiểu chữ, bảng biểu, hình ảnh.

Khi đẩy lên Git, Git vốn quản lý văn bản theo từng dòng (line-by-line diff). Với .docx, Git không hiểu được cấu trúc XML bên trong mà coi đó là một khối dữ liệu lớn. Do đó, chỉ cần Nam sửa một dấu phẩy, hệ thống Git sẽ không thể tự động ghép nối (merge) mà phải khóa toàn bộ tệp, dẫn đến lỗi Conflict toàn cục.

Sai lầm 2: Thiếu tư duy "Web-native" (tương thích nguyên bản với nền tảng web).

Trong môi trường phát triển phần mềm (đặc biệt là GitHub), tài liệu cần được xem trực tiếp ngay trên trình duyệt để các thành viên dễ dàng review, thảo luận (pull request) và chỉnh sửa nhanh.

Việc dùng tệp .docx buộc các thành viên phải tải file về máy, mở bằng Microsoft Word, gây gián đoạn luồng làm việc (workflow) của nhóm dự án CNTT.

2. So sánh khả năng chống hư hại file và dung lượng giữa Rich Text và Markdown
Về khả năng chống hư hại dữ liệu (Bẫy 1 byte):

Rich Text (.docx): Cấu trúc nén ZIP và mã hóa XML bên trong .docx có tính liên kết chặt chẽ. Nếu tệp bị lỗi mạng làm mất hoặc sai lệch chỉ 1 byte ở header hoặc cấu trúc XML, toàn bộ tệp sẽ bị hỏng hoàn toàn. Khi mở lên, Microsoft Word sẽ báo lỗi kinh điển: "The file is corrupt and cannot be opened" và người dùng mất trắng toàn bộ nội dung.

Markdown (.md): Là định dạng Plain Text (văn bản thô) thuần túy. Nếu file bị lỗi 1 byte do đường truyền mạng, chỉ có duy nhất 1 ký tự tại vị trí đó bị lỗi hiển thị (hoặc đổi thành ký tự lạ), toàn bộ các phần còn lại của tài liệu vẫn hoàn toàn nguyên vẹn, đọc hiểu bình thường bằng bất kỳ phần mềm soạn thảo nào (Notepad, VS Code, StackEdit).

Về dung lượng: Tệp .docx chứa rất nhiều metadata (thông tin ngầm về tác giả, kiểu định dạng rườm rà), khiến dung lượng lớn. Trong khi đó, file .md cực kỳ nhẹ (chỉ vài KB), giúp tối ưu hóa tốc độ tải và lưu trữ trên hệ thống quản lý mã nguồn.

Phần 2. Hoàn thiện: Chuyển đổi tài liệu GreenTech sang Markdown (.md)
Dưới đây là phần nội dung giới thiệu dự án "GreenTech" sau khi được chuyển đổi chuẩn xác sang cú pháp Markdown, mô phỏng kết quả từ công cụ StackEdit:

Markdown
# Dự án GreenTech: Giải pháp Công nghệ Xanh cho Đô thị Thông minh

## 1. Giới thiệu chung
**GreenTech** là dự án nghiên cứu và phát triển phần mềm định hướng ứng dụng công nghệ thông tin vào việc tối ưu hóa năng lượng và quản lý môi trường đô thị. Được phát triển bởi đội ngũ sinh viên PTIT, dự án hướng tới mục tiêu xây dựng một hệ sinh thái mã nguồn mở phục vụ cộng đồng.

## 2. Các tính năng cốt lõi
- **Giám sát năng lượng thời gian thực:** Thu thập dữ liệu tiêu thụ điện năng từ các cảm biến IoT.
- **Cảnh báo ô nhiễm:** Phân tích chất lượng không khí và đưa ra dự báo sớm.
- **Báo cáo tự động:** Trích xuất dữ liệu trực quan hỗ trợ công tác quản lý đô thị.

## 3. Công nghệ sử dụng
* **Frontend:** ReactJS, Tailwind CSS
* **Backend:** Node.js, Express
* **Database:** MongoDB
* **Tài liệu:** Markdown (Lưu trữ và quản lý phiên bản trên GitHub)

> **Lưu ý nhóm phát triển:** Mọi đóng góp tài liệu (Documentation) xin vui lòng tuân thủ quy chuẩn định dạng Markdown và thực hiện Pull Request qua nhánh `dev`.
