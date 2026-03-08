🛒 Full Stack E-Commerce Platform

Một giải pháp thương mại điện tử toàn diện được xây dựng trên nền tảng Next.js 14, kết hợp sức mạnh của Firebase cho dữ liệu thời gian thực, Stripe cho thanh toán và Algolia cho tìm kiếm thông minh.

🚀 Tính năng chính

👤 Hệ thống người dùng & Xác thực

Firebase Auth: Đăng nhập an toàn với Email/Password và các nhà cung cấp bên thứ ba.

Quản lý tài khoản: Xem lịch sử đơn hàng, trạng thái thanh toán và cập nhật thông tin cá nhân.

🛍️ Trải nghiệm mua sắm

Tìm kiếm Algolia: Tìm kiếm sản phẩm cực nhanh với gợi ý thông minh và bộ lọc nâng cao.

Giỏ hàng (Cart): Quản lý giỏ hàng phía Client, tự động đồng bộ hóa giá và số lượng.

Review hệ thống: Cho phép người dùng đánh giá và để lại bình luận về sản phẩm.

💳 Thanh toán & Vận chuyển

Stripe Gateway: Xử lý thanh toán thẻ tín dụng an toàn tuyệt đối qua Stripe Checkout.

COD Flow: Hỗ trợ quy trình đặt hàng thanh toán khi nhận hàng.

Real-time Tracking: Cập nhật trạng thái đơn hàng ngay khi Admin thay đổi.

🛠️ Quản trị viên (Admin Panel)

Dashboard: Tổng quan về doanh thu, số lượng đơn hàng và người dùng.

Inventory Management: Thêm/Sửa/Xóa sản phẩm, thương hiệu, danh mục và bộ sưu tập.

Order Fulfillment: Quản lý và xử lý trạng thái đơn hàng tập trung.

💻 Tech Stack

Thành phần

Công nghệ

Frontend

Next.js 14 (App Router), React, Tailwind CSS, Framer Motion

Backend

Firebase (Firestore, Authentication, Storage)

Search Engine

Algolia AI Search

Payment

Stripe API

Deployment

Vercel

📂 Cấu trúc thư mục dự án
```
├── app/                # Next.js App Router (Pages, Layouts & API)
├── components/         # Các UI Components dùng chung (Header, Footer, v.v.)
├── context/            # Quản lý State toàn cục (AuthContext, CartContext)
├── lib/                # Cấu hình SDK (Firebase, Stripe, Algolia)
├── hooks/              # Các Custom Hooks xử lý logic
├── public/             # Tài nguyên tĩnh (Images, Icons, Fonts)
└── types/              # Định nghĩa TypeScript Interfaces
```

⚙️ Hướng dẫn cài đặt

1. Yêu cầu hệ thống

Node.js 18.x trở lên

Tài khoản Firebase, Stripe và Algolia (Bản miễn phí)

2. Cài đặt các bước

# Clone kho lưu trữ
```
git clone <repository-url>
```
# Truy cập thư mục
```
cd <project-directory>
```
# Cài đặt thư viện
```
npm install
```
# Khởi chạy môi trường phát triển
```
npm run dev
```

🔐 Cấu hình biến môi trường

Tạo tệp .env.local tại thư mục gốc và cung cấp các khóa API sau:

# Firebase Credentials
```
NEXT_PUBLIC_FIREBASE_API_KEY=""
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=""
NEXT_PUBLIC_FIREBASE_PROJECT_ID=""
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=""
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=""
NEXT_PUBLIC_FIREBASE_APP_ID=""
NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=""
```
# App Config
```
NEXT_PUBLIC_DOMAIN="http://localhost:3000"
```
# Algolia Configuration
```
NEXT_PUBLIC_ALGOLIA_APP_ID=""
NEXT_PUBLIC_ALGOLIA_APP_KEY=""
```
# Admin & Service Keys
```
NEXT_PUBLIC_FIREBASE_SERVICE_ACCOUNT_KEYS='{}'
```

🛡️ Quy tắc bảo mật Firestore
```
service cloud.firestore {
  match /databases/{database}/documents {
    
    function isAdmin() {
      return exists(/databases/$(database)/documents/admins/$(request.auth.token.email));
    }

    match /admins/{id} {
      allow read: if true;
      allow write: if isAdmin();
    }

    match /brands/{id}, /categories/{id}, /collections/{id} {
      allow read: if true;
      allow write: if isAdmin();
    }

    match /orders/{id} {
      allow read: if isAdmin() || request.auth.uid == resource.data.uid;
      allow write: if isAdmin();
    }

    match /products/{id} {
      allow read: if true;
      allow write: if isAdmin();

      match /reviews/{uid} {
        allow read: if true;
        allow write: if isAdmin() || request.auth.uid == uid;
      }
    }

    match /users/{uid} {
      allow read: if isAdmin() || request.auth.uid == uid;
      allow write: if isAdmin() || request.auth.uid == uid;

      match /checkout_sessions/{id}, /checkout_sessions_cod/{id} {
        allow read: if isAdmin() || request.auth.uid == uid;
        allow write: if isAdmin() || request.auth.uid == uid;
      }

      match /payments/{id} {
        allow read, write: if false;
      }
    }
  }
}

```
📂 Quy tắc bảo mật Storage
```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read: if true;
      allow write: if request.auth.uid != null && firestore.exists(/databases/(default)/documents/admins/$(request.auth.token.email));
    }
  }
}
```

🌐 Live Demo

Bạn có thể trải nghiệm trực tuyến tại: docs-reader-store.vercel.app

🔑 Thông tin Admin dùng thử

Email: admin@gmail.com

Mật khẩu: iloveyou

(Lưu ý: Tài khoản demo này bị hạn chế quyền ghi/xóa để bảo vệ dữ liệu hệ thống)

📜 Kết luận

Dự án này là minh chứng cho việc xây dựng một hệ thống thương mại điện tử hiện đại, có khả năng mở rộng cao và bảo mật tốt. Bạn có thể tùy chỉnh và mở rộng thêm các tính năng như Webhooks hoặc đa ngôn ngữ.

© 2025 - Xây dựng cho mục đích học tập và Portfolio cá nhân.
