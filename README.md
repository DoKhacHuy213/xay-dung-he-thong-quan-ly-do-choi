# Hệ thống quản lý bán đồ chơi

## 👤 Thông tin sinh viên

- **Họ tên:** Đỗ Khắc Huy  
- **Mã sinh viên:** 23010020

---

## 📌 Giới thiệu dự án

Đây là dự án môn học xây dựng hệ thống quản lý bán đồ chơi sử dụng Laravel 11.  
Ứng dụng cho phép người dùng (khách hàng) duyệt danh mục, đặt hàng và quản trị viên quản lý sản phẩm, đơn hàng và người dùng.

---

## 🧱 Cấu trúc hệ thống (Class Diagram)

![Class Diagram]

---

## 🔄 Sơ đồ thuật toán (Activity Diagram)

### 1. Hiển thị tất cả sản phẩm đã được mua bởi khách hàng

![Activity Diagram - Display Products]

### 2. Tìm kiếm sản phẩm được chọn nhiều nhất

![Activity Diagram - Most Selected Product]

---



## 💡 Một số đoạn mã minh họa

### Model: `User.php` và `Product.php`

```php
// app/Models/User.php
public function orders() {
    return $this->hasMany(Order::class);
}
// app/Models/Product.php
public function orders() {
    return $this->belongsToMany(Order::class);
}
public function store(Request $request) {
    $order = new Order();
    $order->user_id = auth()->id();
    $order->save();
    $order->products()->attach($request->product_ids);
    return redirect()->route('orders.index');
}
@foreach($products as $product)
    <div class="card">
        <h4>{{ $product->name }}</h4>
        <p>Giá: {{ $product->price }} VNĐ</p>
        <a href="{{ route('products.show', $product->id) }}">Chi tiết</a>
    </div>
@endforea
🔗 Liên kết
🔗 Link Repo: https://github.com/DoKhacHuy213/xay-dung-he-thong-quan-ly-do-choi

🚀 Link Demo (Codespaces / localhost): [Điền link Codespaces hoặc Localhost nếu có]

🌐 Link deployment (Public web): [Ví dụ: https://quanlydochoi-huy.vercel.app hoặc render.com]

⚙️ Công nghệ sử dụng
Laravel 11

PHP 8.x

MySQL / MariaDB

TailwindCSS / Bootstrap

Laravel Breeze (xác thực)

Cloud deployment: [Heroku / Vercel / Render / Codespaces]
