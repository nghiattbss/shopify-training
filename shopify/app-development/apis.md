# Shopify APIs

Bao gồm 3 loại sau
- Admin APIs
- Storefront API
- Ajax API
# Admin APIs
## Rest API

Tài liệu chi tiết [tại đây](https://shopify.dev/api/admin-rest)

## GraphQL API

Tài liệu chi tiết [tại đây](https://shopify.dev/api/admin-graphql)

Khi thực hành GraphQL nên cài đặt [Shopify Graphql APP](https://shopify-graphiql-app.shopifycloud.com/login)

# Storefront API
Các tính năng cơ bản của APIhttps://shopify-graphiql-app.shopifycloud.com/login
- Truy cập sản phẩm và danh mục sản phẩm.
- Truy cập đơn hàng và khách hàng.
- Truy cập thông tin cửa hàng như thông tin vận chuyển, thuế và cài đặt thanh toán.
- Tìm kiếm sản phẩm và đơn hàng.
- Xây dựng giỏ hàng cho khách hàng.
- Tích hợp thanh toán trực tiếp vào trang web của bạn.
- Tạo và quản lý phiên làm việc của người dùng.
- Đồng bộ hóa đơn hàng và thông tin khách hàng giữa các kênh bán hàng khác nhau.
- Tùy chỉnh giao diện người dùng và thiết kế trang web của bạn.
- Xử lý đơn hàng và truy vấn dữ liệu vận chuyển.

Chi tiết tài liệu [ở đây](https://shopify.dev/docs/api/storefront#endpoints)

Ví dụ sử dụng storefront API để xây dựng một ứng dụng thực tê [ở đây](https://shopify.dev/docs/custom-storefronts/building-with-the-storefront-api)


## Sale Channels
Shopify sales channels là các kênh bán hàng khác nhau mà một chủ store có thể sở hữu, 
ngoài online store ra. Để có thể tích hợp hoặc xấy dựng riêng cho mình một sales channel, 
developer cần phải sử dụng Storefront API. Ví dụ: mobile apps, react apps...etc
## Hydrogen
Shopify Hydrogen là một Sales channel sử dụng storefront API để xây dựng. Các công nghệ xoay xung quan React.

Tài liệu chi tiết sử dụng Hydrogen [ở đây](https://shopify.dev/docs/custom-storefronts/hydrogen)

# Ajax API

Được sử dụng để thao tác với Shopify Theme. Chi tiết tham khảo [ở đây](https://shopify.dev/docs/api/ajax) 

Ajax API chia làm 4 loại:
- [Cart](https://shopify.dev/docs/api/ajax/reference/cart) 
- [Product](https://shopify.dev/docs/api/ajax/reference/product)
- [Product Recommendations ](https://shopify.dev/docs/api/ajax/reference/product-recommendations)
- [Predictive Search](https://shopify.dev/docs/api/ajax/reference/predictive-search)