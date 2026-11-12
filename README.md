# 🎡 RIDE REPORT NOTES — SE TECHNICAL DEPARTMENT

Ứng dụng kiểm tra an toàn hiện trường trò chơi cảm giác mạnh & thiết bị công viên (Amusement Rides Inspection App) thiết kế chuẩn **Mobile First**, hoạt động **100% Offline**, lưu trữ cục bộ bằng **IndexedDB** và xuất file Excel chuẩn Sun World / TÜV NORD.

![Logo SE Technical Department](./icons/icon-192.png)

---

## 🚀 HƯỚNG DẪN DEPLOY TRỰC TIẾP LÊN GITHUB PAGES

Người dùng không cần cài đặt môi trường lập trình hay chỉnh sửa code, chỉ cần upload là chạy được ngay!

### 📌 Cách 1: Upload trực tiếp thư mục `dist-github-pages` (Nhanh nhất - Chạy ngay 100%)

#### **Bước 1: Tạo GitHub Repository**
1. Đăng nhập vào tài khoản [GitHub](https://github.com/).
2. Nhấn nút **New** (hoặc dấu `+` ở góc phải trên) để tạo kho lưu trữ mới.
3. Đặt **Repository name**: `ride-report-notes`.
4. Chọn chế độ **Public**.
5. Nhấn **Create repository**.

#### **Bước 2: Upload toàn bộ file trong thư mục `dist-github-pages`**
1. Mở thư mục `dist-github-pages/` đã được build sẵn trong dự án này.
2. Trên giao diện GitHub repository vừa tạo, chọn **Add file** ➔ **Upload files**.
3. Kéo toàn bộ tất cả các file và thư mục con bên trong `dist-github-pages/` thả vào GitHub (bao gồm `index.html`, `404.html`, `manifest.json`, `service-worker.js`, thư mục `assets/`, thư mục `icons/`, `.nojekyll`, file `.html` độc lập cho Android và iOS).
4. Nhấn **Commit changes**.

#### **Bước 3: Cấu hình GitHub Pages**
1. Vào tab **Settings** của Repository trên GitHub.
2. Tại menu bên trái, chọn **Pages**.
3. Tại mục **Build and deployment** ➔ **Source**: chọn **Deploy from a branch**.
4. Chọn Branch: **`main`** (hoặc `master`), thư mục: **`/(root)`**.
5. Nhấn **Save**.

#### **Bước 4: Truy cập ứng dụng**
Đợi khoảng 1 - 2 phút, GitHub Pages sẽ kích hoạt đường dẫn:
```
https://USERNAME.github.io/ride-report-notes/
```
*(Thay `USERNAME` bằng tên tài khoản GitHub của bạn)*

---

### 📌 Cách 2: Tự động Build bằng GitHub Actions (Dành cho toàn bộ Source Code)
Dự án đã tích hợp sẵn file `.github/workflows/deploy.yml`. Nếu bạn upload toàn bộ mã nguồn:
1. Upload toàn bộ source code của dự án lên GitHub branch `main`.
2. Vào **Settings** ➔ **Pages** ➔ **Source**: Chọn **GitHub Actions**.
3. GitHub sẽ tự động chạy quy trình build và deploy phiên bản mới nhất lên GitHub Pages.

---

## 📱 HƯỚNG DẪN CÀI ĐẶT PWA LÊN ĐIỆN THOẠI

### 🤖 Trên Android (Google Chrome / Samsung Internet)
1. Mở liên kết GitHub Pages trên trình duyệt Chrome: `https://USERNAME.github.io/ride-report-notes/`.
2. Bấm vào biểu tượng **3 chấm (⋮)** ở góc trên bên phải.
3. Chọn **"Cài đặt ứng dụng"** (hoặc **"Thêm vào Màn hình chính"**).
4. Ứng dụng sẽ xuất hiện trên màn hình chính như một ứng dụng native với logo **SE Technical Department**.
5. Bật chế độ máy bay (tắt Wifi/4G) ➔ Mở app vẫn chạy và lưu dữ liệu bình thường 100%!

### 🍏 Trên iPhone / iPad (Safari iOS)
1. Mở liên kết GitHub Pages trên trình duyệt **Safari**: `https://USERNAME.github.io/ride-report-notes/`.
2. Bấm vào nút **Chia sẻ** (biểu tượng hình vuông có mũi tên hướng lên `⎋` ở thanh dưới cùng Safari).
3. Cuộn xuống và chọn **"Thêm vào MH chính"** (biểu tượng dấu `+`).
4. Nhấn **Thêm** (Add) ở góc trên bên phải.
5. Ứng dụng sẽ hiển thị trên màn hình chính iPhone với icon sắc nét, khi mở sẽ chạy toàn màn hình không có thanh địa chỉ web.

---

## ✨ CÁC TÍNH NĂNG ĐẢM BẢO HOẠT ĐỘNG 100% OFFLINE

* ✅ **100% Offline-First:** Tích hợp `service-worker.js` và `manifest.json`. Không cần Internet, không cần 4G, không cần Wifi khi đi kiểm tra hiện trường.
* ✅ **Không Cần Server / Backend:** Toàn bộ dữ liệu kiểm định lưu trữ trực tiếp trên thiết bị bằng **IndexedDB (Dexie.js)**.
* ✅ **Mẫu Báo Cáo Kiểm Định Chuẩn:**
  * **Sheet 1 (`Tổng Hợp`):** Bảng tổng kết số lượng rủi ro theo từng trò chơi, mã hồ sơ (Dossier), số tem kiểm định (Test Mark), kết quả A/B/C và chú giải tiêu chuẩn.
  * **Sheet 2 (`Tất Cả Phát Hiện`):** 9 cột chuẩn theo file mẫu `Report Rides BNC` (`TT`, `NGÀY`, `KHU VỰC`, `TÊN BỘ PHẬN/ THIẾT BỊ`, `MÔ TẢ RỦI RO`, `HÌNH ẢNH`, `CẤP ĐỘ ƯU TIÊN`, `ĐỀ XUẤT`, `NHẬN XÉT BỞI`).
  * **Từng Sheet Theo Trò Chơi:** Tự động tạo từng sheet riêng cho mỗi trò chơi.
  * **Nhúng Ảnh Trực Tiếp:** Ảnh chụp hiện trường và ảnh vẽ đánh dấu lỗi được tự động chèn và co giãn vừa vặn vào từng ô trong Excel.
* ✅ **Thao Tác Nhập Hiện Trường Cực Nhanh:**
  * **Không bắt buộc phải nhập hết:** Bỏ mọi ràng buộc cứng, lưu ngay những gì có.
  * **Ngày tự động:** Lấy ngày giờ thiết bị tự động.
  * **Khu vực tự nhập tay:** Kèm nút **"🔄 Nhập Lại Từ Khóa Đã Lưu"** và chip 1-chạm cho 22 trò chơi Sun World.
  * **Voice-to-Text:** Nhập nội dung lỗi bằng giọng nói tiếng Việt qua Web Speech API.
  * **Vẽ Đánh Dấu Lỗi:** Vẽ mũi tên, khoanh tròn, ghi chú trực tiếp lên ảnh.
* ✅ **Sao Lưu & Phục Hồi Dữ Liệu:** Xuất và nhập toàn bộ database dạng file `.json` tiện lợi.
* ✅ **Hai Bản HTML Tải Về Trực Tiếp:** Có sẵn `ride-report-android.html` và `ride-report-ios.html` chạy độc lập 1 file duy nhất.

---

## 🛠️ CÔNG NGHỆ SỬ DỤNG
* **Framework:** React 19 + TypeScript + Vite
* **Styling:** TailwindCSS (Material Design 3 Dark Mode)
* **Local Storage:** Dexie.js (IndexedDB)
* **Excel Engine:** ExcelJS + FileSaver.js
* **Compression:** JSZip
* **Offline Cache:** Service Worker PWA Cache-first

---

**Phát triển bởi:** SE Technical Department • Sun World Ride Safety Inspection
