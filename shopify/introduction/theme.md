# Shopify Theme
### Folder Structure
```
.
├── assets
├── config
├── layout
├── locales
├── sections
├── snippets
└── templates
    └── customers

```
Để nhìn một cách chi tiết hơn có thể tham khảo theme [Dawn Github tại đây](https://github.com/Shopify/dawn)

Để có thể thực hành với Liquid, các bạn phải cài đặt 1 shopify store, sau đó edit code của theme đang sử dụng.

Khi phát triển App
### Liquid

Shopify Liquid là một ngôn ngữ mẫu được sử dụng bởi nền tảng Shopify để động thời hiển thị nội dung và bố cục cho các cửa hàng trực tuyến. Đó là một ngôn ngữ dựa trên Ruby cho phép các nhà phát triển tạo các mẫu có thể tái sử dụng, kiểm soát luồng nội dung và xây dựng các tính năng

Cú pháp liquid có thể tham khảo tại đây [cheatsheet](https://www.shopify.com/partners/shopify-cheat-sheet)

Một số chú ý về liquid
- Nó được coi là server-side
- Các object như product, customer... đều là read-only, có nghĩa là ta không thể thay đổi giá trị của bất kỳ thuộc tính nào, ví dụ: customer.name = "new name", sau đó in ra customer.name, giá trị vẫn là giá trị cũ.
- Liquid không cung cấp nhiều hàm tiện lợi như PHP, cũng không có cơ chế để cài thêm plugin, hay package hỗ trợ.
- Tốc độ của theme sử dụng liquid là rất nhanh.

# Code Examples

- Hiển thị tên sản phẩm và giá trị của nó:
```
{% for product in collections.all.products %}
  <h3>{{ product.title }}</h3>
  <p>{{ product.price | money }}</p>
{% endfor %}

```
- Sử dụng điều kiện để kiểm tra xem sản phẩm đó có phải là sản phẩm mới không:
```
{% if product.tags contains 'new' %}
  <p class="new-product">New!</p>
{% endif %}

```
- Hiển thị đánh giá trung bình của sản phẩm dưới dạng sao:
```
{% assign rating = product.metafields.product.rating %}
{% for i in (1..5) %}
  {% if i <= rating %}
    <i class="fas fa-star"></i>
  {% else %}
    <i class="far fa-star"></i>
  {% endif %}
{% endfor %}

```
- Sử dụng bộ lọc để định dạng số tiền và hiển thị giá trị giảm giá của một sản phẩm (nếu có):
```
{% if product.compare_at_price_max > product.price %}
  <p><s>{{ product.compare_at_price_max | money }}</s> {{ product.price | money }}</p>
{% else %}
  <p>{{ product.price | money }}</p>
{% endif %}
```



