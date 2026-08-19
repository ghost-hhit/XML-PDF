# Hóa đơn & BCTC: XML → PDF

Công cụ web tĩnh chuyển **XML thuế của Việt Nam** thành **bản thể hiện PDF**, chạy hoàn toàn trong trình duyệt (dữ liệu không rời khỏi máy). Tự nhận diện và xử lý **hai loại file**:

1. **Hóa đơn điện tử** (chuẩn TT78/ND123, thẻ gốc `<HDon>`) → bản thể hiện hóa đơn GTGT.
2. **Hồ sơ khai thuế / Báo cáo tài chính từ HTKK** (thẻ gốc `<HSoThueDTu>`) → bảng chỉ tiêu tài chính, hiện có nhãn chuẩn (TT133) cho:
   - Bảng cân đối kế toán (B01a-DNN)
   - Kết quả hoạt động kinh doanh (B02-DNN)
   - Lưu chuyển tiền tệ (B03-DNN — nhãn các chỉ tiêu tổng hợp)
   - Bảng cân đối tài khoản (theo số hiệu tài khoản)

## Tính năng

- Kéo–thả hoặc chọn **nhiều file** cùng lúc; danh sách bên trái đánh dấu từng file là *HĐ* hay *Tờ khai/BCTC*.
- **Tải PDF** một chạm (A4, tự chia trang) — hoặc **In / Lưu PDF** qua trình duyệt (chữ nét, chọn được, nhẹ). Với BCTC nhiều trang, nút *In / Lưu PDF* thường đẹp hơn.
- **Tải tất cả (PDF)** khi mở nhiều file.
- Tự chứa: đã nhúng jsPDF + html2canvas, **không cần internet** khi dùng.

## Cách dùng nhanh

Mở thẳng `index.html` bằng trình duyệt, kéo file XML vào là chạy. Không cần cài gì.

## Đưa lên GitHub Pages

Đẩy `index.html` (ở thư mục gốc repo) lên nhánh `main`, rồi vào **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main` / `(root)` → Save. Trang chạy tại `https://<tài-khoản>.github.io/<tên-repo>/`.

## Cách nhận diện của tool

- Có thẻ `NDHDon` hoặc gốc `HDon` → xử lý như **hóa đơn**.
- Gốc `HSoThueDTu` hoặc có `TKhaiThue` → xử lý như **tờ khai/BCTC**.
- Không khớp cả hai → báo lỗi rõ ràng, không "đoán bừa".

## Mở rộng

Bộ nhãn chỉ tiêu để trong một chỗ (biến `LBL` / `FORMS` trong `index.html`). Muốn hỗ trợ thêm mẫu tờ khai khác (GTGT 01, TNCN, TNDN…) thì bổ sung nhãn cho mã chỉ tiêu tương ứng; các mẫu chưa có nhãn vẫn hiển thị **mã chỉ tiêu + giá trị** đúng cột nên vẫn đọc được.

## Lưu ý pháp lý

Bản PDF/bản in chỉ là **bản thể hiện** để xem, in, lưu trữ nội bộ. File **XML gốc** mới có giá trị pháp lý.

## Kèm theo

- `index.html` — toàn bộ công cụ, một file duy nhất.
- `sample.xml` — hóa đơn mẫu để thử.
