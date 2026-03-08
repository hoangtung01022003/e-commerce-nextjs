# 🛒 Full-Stack E-Commerce Platform

Một giải pháp thương mại điện tử hiện đại, tập trung vào hiệu năng cao, trải nghiệm người dùng mượt mà và khả năng mở rộng. Dự án kết hợp sức mạnh của **Server-Side Rendering (SSR)** và **Real-time Database** để tạo ra một hệ thống bán hàng toàn diện.

---

## 🏗️ Kiến Trúc Hệ Thống (Architecture)

Dự án được xây dựng trên mô hình **Serverless Architecture**:

* **Frontend**: Next.js 14 (App Router) tối ưu hóa SEO và tốc độ phản hồi.
* **Backend as a Service (BaaS)**: Firebase (Firestore, Auth, Storage) đảm bảo tính nhất quán dữ liệu thời gian thực.
* **Search Engine**: Tích hợp Algolia AI Search để xử lý tìm kiếm sản phẩm với độ trễ cực thấp.
* **Payment Flow**: Quy trình thanh toán an toàn qua Stripe với cơ chế xử lý trạng thái đơn hàng tự động.

---

## ✨ Tính Năng Nổi Bật

### 1. 🛍️ Trải Nghiệm Mua Sắm Thông Minh

* **AI-Powered Search**: Tìm kiếm nhanh, gợi ý từ khóa và bộ lọc nâng cao nhờ Algolia.
* **Dynamic Cart Management**: Quản lý giỏ hàng thông minh, tự động đồng bộ hóa trạng thái và tồn kho.
* **Review System**: Hệ thống đánh giá sản phẩm real-time giúp tăng độ tin cậy cho khách hàng.

### 2. 👤 Quản Lý Tài Khoản & Bảo Mật

* **Secure Auth**: Xác thực đa phương thức qua Firebase Auth (Email, Google, v.v.).
* **Role-Based Access Control (RBAC)**: Phân quyền chặt chẽ giữa User và Admin thông qua Firestore Security Rules.

### 3. 💳 Thanh Toán & Vận Chuyển

* **Stripe Integration**: Hỗ trợ thanh toán quốc tế qua Stripe Checkout an toàn tuyệt đối.
* **COD Flow**: Quy trình đặt hàng linh hoạt cho thanh toán khi nhận hàng.
* **Real-time Tracking**: Theo dõi trạng thái đơn hàng tức thì ngay khi Admin cập nhật.

### 4. 🛠️ Hệ Quản Trị Admin Toàn Diện

* **Data Dashboard**: Thống kê doanh thu, người dùng và đơn hàng trực quan.
* **Inventory Control**: Quản lý CRUD sản phẩm, thương hiệu, danh mục theo dạng module.
* **Order Fulfillment**: Xử lý đơn hàng tập trung, đảm bảo quy trình vận hành chính xác.

---

## 🛠️ Tech Stack

| Thành phần | Công nghệ |
| --- | --- |
| **Frontend** | Next.js 14, React, Tailwind CSS, Framer Motion |
| **Backend/Auth** | Firebase Services (Firestore, Storage, Auth) |
| **Search** | Algolia AI Search Engine |
| **Payment** | Stripe API Gateway |
| **Deployment** | Vercel (CI/CD) |

---

## ⚡ Tối Ưu Hóa & Bảo Mật

* **Firestore Security Rules**: Thiết lập lớp bảo mật tầng dữ liệu, ngăn chặn truy cập trái phép cấp độ phân quyền (Admin/User).
* **Modular Component Architecture**: Tối ưu hóa việc tái sử dụng code và dễ dàng bảo trì.
* **Next.js Image Optimization**: Tự động nén và tối ưu hóa hình ảnh sản phẩm để tăng điểm Performance.

---

## 🚀 Hướng Dẫn Cài Đặt

1. **Clone & Install**:
```bash
git clone <repository-url>
cd <project-directory>
npm install

```


2. **Cấu hình Environment Variables**:
Tạo tệp `.env.local` và điền đầy đủ các thông tin:
* Firebase SDK Config
* Algolia App ID & Key
* Stripe Secret/Public Key


3. **Run Project**:
```bash
npm run dev

```



---

## 🌐 Trải Nghiệm Demo

* **Live Site**: [docs-reader-store.vercel.app](https://docs-reader-store.vercel.app)
* **Tài khoản Admin dùng thử**:
* *Email*: `admin@gmail.com`
* *Password*: `iloveyou`
