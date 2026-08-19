# Hóa đơn điện tử XML → PDF

Công cụ web tĩnh chuyển **hóa đơn điện tử (.xml)** theo chuẩn Tổng cục Thuế (QĐ 1450/QĐ-TCT) thành **bản thể hiện PDF**. Chạy hoàn toàn trong trình duyệt — file XML **không** được gửi lên bất kỳ máy chủ nào, phù hợp để xử lý hóa đơn nội bộ.

## Tính năng

- Kéo–thả hoặc chọn **một hay nhiều** file XML cùng lúc.
- Xem trước bản thể hiện đúng bố cục hóa đơn GTGT (tiêu đề đỏ, mẫu số/ký hiệu/số, người bán, người mua, bảng hàng hóa, tổng tiền, tiền bằng chữ, thời gian ký số, mã cơ quan thuế).
- **Tải PDF**: xuất PDF một chạm (ảnh hóa, khổ A4, tự chia trang).
- **In / Lưu PDF**: dùng hộp thoại in của trình duyệt (Ctrl/Cmd + P → *Save as PDF*) — chữ nét, chọn/copy được, dung lượng nhẹ.
- **Tải tất cả (PDF)**: khi mở nhiều file, xuất PDF cho từng hóa đơn.
- Tự chứa: đã nhúng sẵn jsPDF + html2canvas, **không cần internet** khi dùng.

## Dùng thử tại chỗ

Mở thẳng `index.html` bằng trình duyệt là chạy được ngay (không cần cài gì).

## Đưa lên GitHub Pages

1. Tạo một repo mới trên GitHub (ví dụ `hddt-pdf`).
2. Đẩy file `index.html` (và `README.md` nếu muốn) lên nhánh `main`:

   ```bash
   git init
   git add index.html README.md
   git commit -m "Công cụ chuyển hóa đơn XML sang PDF"
   git branch -M main
   git remote add origin https://github.com/<tài-khoản>/hddt-pdf.git
   git push -u origin main
   ```

3. Vào **Settings → Pages** của repo:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main` · thư mục `/ (root)` → **Save**.
4. Chờ khoảng 1 phút, trang sẽ chạy tại:
   `https://<tài-khoản>.github.io/hddt-pdf/`

> `index.html` phải nằm ở thư mục gốc để mở đúng địa chỉ trên. Nếu để trong thư mục con, địa chỉ sẽ có thêm đường dẫn thư mục đó.

## Trường dữ liệu đọc từ XML

Theo chuẩn: `TTChung` (THDon, KHMSHDon, KHHDon, SHDon, NLap, DVTTe), `NBan`/`NMua`, `DSHHDVu/HHDVu`, `TToan` (TgTCThue, TgTThue, TgTTTBSo, TgTTTBChu), `MCCQT`, và thời gian ký số trong `DSCKS`. Bộ đọc bỏ qua namespace nên chạy được với XML của nhiều nhà cung cấp.

## Lưu ý

- Bản PDF/bản in **chỉ là bản thể hiện**; file XML mới là bản gốc có giá trị pháp lý.
- File cần là hóa đơn XML chuẩn Tổng cục Thuế, mã hóa **UTF-8** (mặc định của hầu hết phần mềm hóa đơn).
- Cấu trúc mỗi nhà cung cấp có thể khác đôi chút; nếu một trường không hiện, gửi mình file mẫu (đã che số liệu) để bổ sung ánh xạ.

## Kèm theo

- `index.html` — toàn bộ công cụ, một file duy nhất.
- `sample.xml` — hóa đơn mẫu để thử.
