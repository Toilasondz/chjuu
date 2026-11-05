# VideoStarTool Pro - iOS Tweak & Reverse Engineering

Dự án Tweak hoàn chỉnh dành cho ứng dụng **VideoStar** (iOS), tích hợp 2 tính năng chính:
1. **Auto Nhập Ảnh / Video (Lọc Lớp Thông Minh)**: Tự động lọc chỉ nạp vào các lớp Ảnh/Video, bỏ qua triệt để các lớp Chữ, Zaps, 3D, Màu đơn sắc, Overlay.
2. **Thanh Công Cụ Chia Beat (Beat Mapping Toolbar)**: Hỗ trợ nhảy Beat tới/lùi trên timeline, cắt phân cảnh (Split), tùy chỉnh BPM và tốc độ phát.
3. **Nút Nổi Thông Minh (Floating Button)**: Nút tròn di chuyển tự do, tự động hít cạnh màn hình, hỗ trợ ActionSheet menu.

---

## 📁 Cấu Trúc Thư Mục

```text
VideoStarTweakPro/
├── Makefile                          # Cấu hình biên dịch Theos (arm64, arm64e, ARC, Frameworks)
├── control                           # Thông tin định danh gói Cydia/Jailbreak (.deb)
├── VideoStarTool.plist               # Bundle ID filter cho MobileSubstrate
├── Tweak.xm                          # Mã nguồn Objective-C & Logos Framework cốt lõi
├── README.md                         # Tài liệu hướng dẫn
└── .github/
    └── workflows/
        └── build.yml                 # GitHub Actions CI biên dịch tự động chuẩn v4
```

---

## 🚀 Hướng Dẫn Biên Dịch (Compilation)

### Cách 1: Biên dịch tự động bằng GitHub Actions (Khuyên dùng)
1. Đưa toàn bộ thư mục `VideoStarTweakPro` lên một kho lưu trữ (repository) GitHub mới của bạn.
2. Vào tab **Actions** trên GitHub.
3. Chọn workflow **Build VideoStar Tweak** và nhấn **Run workflow**.
4. Khi quá trình hoàn tất (dấu tích xanh), tải file tại mục **Artifacts**:
   - File `.deb`: Dành cho iPhone đã Jailbreak (cài qua Sileo / Zebra / Filza).
   - File `.dylib`: Dành cho cài đặt qua TrollStore / Sideloadly / Azule (Inject trực tiếp vào file IPA).

### Cách 2: Biên dịch cục bộ (Local trên Mac/Linux có Theos)
```bash
cd VideoStarTweakPro
make package FINALPACKAGE=1
```
File `.deb` xuất hiện tại thư mục `packages/`, file `.dylib` xuất hiện tại `.theos/obj/VideoStarTool.dylib`.
