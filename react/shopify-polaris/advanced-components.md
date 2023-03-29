# Resource Picker
Đây là một component đặc biệt, được xây dựng tương thích với Shopify Polaris. Đặc điểm
- Chỉ hoạt động với một dạng Shopify App (App Nhúng)
- Có thể sử dụng kèm theo các câu truy vấn GraphQL
- Có 3 kiểu resource type cơ bản:
  - Product
  - ProductVariant
  - Collection
### React Code Example
```
import React from 'react';
import ReactDOM from 'react-dom';
import {Provider, ResourcePicker} from '@shopify/app-bridge-react';

function MyApp() {
  return (
    <Provider config={config}>
      <ResourcePicker resourceType="Product" open />
    </Provider>
  );
}

const root = document.createElement('div');
document.body.appendChild(root);
ReactDOM.createRoot(root).render(<MyApp />);

```
# AppBridge Components
Resource picker bên trên cũng là một trong những loại component chỉ hoạt động với AppBridge. Tuy nhiên còn nhiều loại nữa, các bạn có thể theo dõi ở đây.

Đặc điểm khác biệt là các loại component này chỉ hoạt động trên Shopify Embedded APP.

Tài liệu chi tiết [ở đây](https://shopify.dev/docs/apps/tools/app-bridge)

