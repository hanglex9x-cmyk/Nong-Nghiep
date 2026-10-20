# THYM — App Quản lý Nông nghiệp (bản GitHub Pages)

Bản tĩnh GitHub Pages của app nông nghiệp THYM: thiết kế giống hệt demo gốc (token màu light/dark, Be Vietnam Pro + JetBrains Mono, sidebar 248px, topbar + sync-pill, bottomnav mobile), đầy đủ tính năng bản chính, dữ liệu gọi trực tiếp API Apps Script.

## Cấu trúc

- `index.html` — SPA 1 file duy nhất (đăng nhập, Dashboard lọc theo vùng, Vùng & Lô, Cân xe, Giờ máy, Dầu diesel, Bón phân, Sản lượng, Bản đồ Leaflet vệ tinh).

## API

- Base: `https://script.google.com/macros/s/AKfycbx7KJtZDvyiQDLiRukt9QMx6yX_oM55on7WHky036wWXjfmLp99A9KhvdctqUbl8Dma0A/exec`
- Giao thức: `rpc(fn, ...args)` — POST `text/plain`, body `{"fn","args"}`, trả `{ok, data|error}`. Token lưu `localStorage` khóa `thym_token` / `thym_user`; lỗi hết phiên tự đăng xuất về màn hình login.
- Xuất Excel: SheetJS (cdnjs `xlsx 0.18.5`) nạp lười khi bấm xuất, tên file `TenMuc_YYYYMMDD.xlsx`.
- Bản đồ: Leaflet 1.9.4 (unpkg) + Esri World Imagery / OSM, polygon minh họa sinh phía client theo diện tích thật từng lô quanh Nông Cống, Thanh Hóa `[19.62, 105.62]`.

## Deploy lên GitHub Pages

1. Tạo / dùng repo `app-quan-ly-nong-nghiep-thym` trên tài khoản GitHub của chủ dự án.
2. Push thư mục này lên nhánh `main`, giữ `index.html` ở thư mục gốc (root) của repo:
   ```bash
   git remote add origin https://github.com/<owner>/app-quan-ly-nong-nghiep-thym.git
   git push -u origin main
   ```
3. Vào repo → **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main`, Folder = `/ (root)` → Save.
4. Đợi Pages build xong, mở URL `https://<owner>.github.io/app-quan-ly-nong-nghiep-thym/` và đăng nhập bằng tài khoản thật để kiểm chứng.
