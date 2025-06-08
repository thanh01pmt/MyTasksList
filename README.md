# MyTasks App - Ứng Dụng Quản Lý Công Việc

Đây là một ứng dụng di động đơn giản được xây dựng hoàn toàn bằng **SwiftUI**, cho phép người dùng quản lý các công việc cá nhân. Ứng dụng được phát triển dựa trên bản thiết kế (mockup) đã cho, bao gồm các chức năng cốt lõi: đăng nhập, xem danh sách công việc và xem chi tiết từng công việc.

## Luồng Hoạt Động (User Flow)

Luồng hoạt động chính của người dùng trong ứng dụng như sau:

`Màn hình Login` → `Màn hình Danh sách Task (Task List)` → `Màn hình Thông tin Task (Task Info)`

## Tính Năng Chính

*   **Xác thực người dùng:** Màn hình đăng nhập cơ bản để người dùng truy cập vào danh sách công việc của họ.
*   **Hiển thị danh sách công việc:** Các công việc được hiển thị trong một danh sách và được phân loại tự động thành hai nhóm:
    *   **Urgent (Khẩn cấp):** Các công việc có hạn chót (deadline) sắp tới.
    *   **Not Urgent (Không khẩn cấp):** Các công việc còn nhiều thời gian để hoàn thành.
*   **Xem chi tiết công việc:** Người dùng có thể nhấn vào một công việc bất kỳ để xem thông tin chi tiết, bao gồm Tên, Hạn chót, Mô tả và Ghi chú.

## Cấu Trúc Dự Án

Dự án được tổ chức theo cấu trúc MV (Model-View), tập trung vào việc phân tách dữ liệu và giao diện.

### 1. Model

Phần lõi dữ liệu của ứng dụng, định nghĩa cấu trúc của một công việc.

*   **`Task.swift`**: Struct `Task` tuân thủ `Identifiable` để sử dụng trong `List` của SwiftUI.
    ```swift
    struct Task: Identifiable {
        let id: UUID
        var name: String         // Tên công việc
        var deadline: Date       // Hạn chót
        var description: String  // Mô tả
        var note: String         // Ghi chú
        var isUrgent: Bool     // Thuộc tính tính toán để xác định độ khẩn cấp
    }
    ```

### 2. Views (Màn hình chính)

Các màn hình chính mà người dùng tương tác.

*   **`LoginView.swift`**: Màn hình đăng nhập, chứa các `TextField` cho username/password và `Button` để đăng nhập.
*   **`TaskListView.swift`**: Màn hình hiển thị danh sách công việc.
    *   Sử dụng `NavigationView` để quản lý điều hướng.
    *   Sử dụng `List` và `Section` để phân nhóm công việc thành "Urgent" và "Not Urgent".
    *   Sử dụng `NavigationLink` để chuyển sang màn hình chi tiết.
*   **`TaskInfoView.swift`**: Màn hình hiển thị toàn bộ thông tin chi tiết của một `Task` được chọn.

### 3. Components (Thành phần tái sử dụng)

Các View nhỏ, được thiết kế để tái sử dụng ở nhiều nơi, giúp code sạch và nhất quán.

*   **`TaskRowView.swift`**: Giao diện cho một hàng (row) trong danh sách công việc trên màn hình `TaskListView`.
*   **`SectionHeaderView.swift`**: Giao diện cho tiêu đề (`Urgent`, `Not Urgent`) của mỗi nhóm trong `TaskListView`.
*   **`InfoDetailRow.swift`**: Một View nhỏ để hiển thị một cặp "Nhãn - Giá trị" trên màn hình `TaskInfoView` (ví dụ: "Deadline" - "17-06-2025").

---

## Trạng Thái Dự Án (Checklist)

Checklist này dùng để theo dõi tiến độ phát triển các tính năng của dự án.

### Giai đoạn 1: Nền tảng & Dữ liệu
- [x] **Khởi tạo Project SwiftUI**
- [x] **Định nghĩa `Task` Model**
- [ ] **Tạo Dữ liệu Mẫu (Mock Data)**

### Giai đoạn 2: Xây dựng Giao diện (UI)
- [ ] **Xây dựng `TaskRowView`**
- [ ] **Xây dựng `TaskInfoView`**
- [ ] **Xây dựng `TaskListView`**
- [ ] **Kết nối Navigation giữa `TaskListView` và `TaskInfoView`**

### Giai đoạn 3: Hoàn thiện Luồng Ứng dụng
- [ ] **Xây dựng `LoginView`**
- [ ] **Quản lý luồng chính (Login ↔ TaskList)**
- [ ] **Tinh chỉnh giao diện (Màu sắc, Font, Spacing)**

### Giai đoạn 4: Tính năng Mở rộng (Tương lai)
- [ ] **Thêm, Sửa, Xóa công việc**
- [ ] **Lưu trữ dữ liệu cục bộ (Core Data / SwiftData / Realm)**
- [ ] **Kết nối API để đồng bộ dữ liệu**
- [ ] **Thêm tính năng thông báo (Push Notification) cho deadline**

---
