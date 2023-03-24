# Giới thiệu

React là một thư viện JavaScript mã nguồn mở được phát triển bởi Facebook. Nó được sử dụng để xây dựng các ứng dụng web đơn trang (single-page applications - SPAs) hoặc các thành phần giao diện người dùng (user interface components) trên các trang web phức tạp. React giúp cho việc tạo ra các giao diện người dùng tương tác nhanh chóng và dễ dàng quản lý, vì nó cung cấp một cách tiếp cận linh hoạt cho việc quản lý trạng thái (state management) của các thành phần giao diện người dùng. React cũng kết hợp với các thư viện khác, chẳng hạn như React Router và Redux, để tạo ra các ứng dụng web phức tạp hơn.

# Lịch sử phát triển
Dưới đây là các mốc thời gian cụ thể trong lịch sử phát triển của React:

- 2011: React được bắt đầu phát triển bởi Jordan Walke tại Facebook.
- 2013: Facebook công bố việc sử dụng React để xây dựng giao diện người dùng trên trang web của mình.
- 2015: React được phát hành mã nguồn mở cho cộng đồng phát triển sử dụng.
- 2016: React Native được giới thiệu, cho phép phát triển các ứng dụng di động sử dụng React.
- 2017: React Fiber được giới thiệu, là một bản cập nhật quan trọng cho React, cải thiện hiệu suất và khả năng mở rộng của nó.
- 2018: React 16.3 được phát hành, cung cấp các tính năng mới như Context API và Fragments.
- 2019: React Hooks được giới thiệu, cho phép lập trình viên quản lý trạng thái của các thành phần giao diện người dùng một cách đơn giản hơn.
- 2020: React 17 được phát hành, cung cấp các cải tiến về tính ổn định và khả năng tương thích của React.
- 2022: React 18 được phát hành. Bản phát hành này tập trung vào các cải tiến hiệu suất và cập nhật công cụ kết xuất. React 18 đặt nền tảng cho  concurrent rendering APIs mà các tính năng React trong tương lai sẽ được xây dựng dựa trên đó.
- Hiện tại, React vẫn đang được phát triển và cập nhật thường xuyên để cải thiện hiệu suất và tính năng của nó.
# Cơ chế hoạt động
### Component-based architecture (Kiến trúc hướng thành phần):
React sử dụng một kiến trúc hướng thành phần, trong đó các thành phần (components) được xây dựng để tái sử dụng và quản lý trạng thái của chúng. Các thành phần là các phần tử độc lập và được xây dựng với HTML, CSS và JavaScript. Mỗi thành phần có thể có trạng thái của riêng nó và có thể truyền các giá trị props (properties) giữa các thành phần để tạo thành các giao diện phức tạp.
### Virtual DOM (DOM ảo):
React sử dụng một khái niệm gọi là Virtual DOM để cập nhật giao diện người dùng một cách hiệu quả. Virtual DOM là một bản sao của DOM thực tế trên trình duyệt, được lưu trữ và quản lý bởi React. Khi trạng thái của một thành phần thay đổi, React sẽ tạo ra một Virtual DOM mới và so sánh với Virtual DOM cũ để tìm ra sự khác biệt. Sau đó, React sẽ chỉ cập nhật những phần cần thiết trên DOM thực tế, giúp tối ưu hiệu suất và giảm thiểu tác động lên các thành phần khác.
### JSX (JavaScript XML):
React sử dụng JSX để tạo ra các thành phần giao diện người dùng. JSX là một phần của JavaScript, cho phép viết các đoạn mã HTML tương tự như HTML chuẩn bằng cú pháp của JavaScript. Khi viết JSX, các thành phần được định nghĩa như các hàm JavaScript và trả về một cây DOM ảo. JSX cũng cho phép sử dụng các đoạn mã JavaScript bên trong đoạn mã HTML để tạo ra các thành phần động.
### State Management (Quản lý trạng thái):
React cung cấp một cách tiếp cận linh hoạt để quản lý trạng thái của các thành phần. Trạng thái (state) được sử dụng để lưu trữ các thông tin thay đổi của các thành phần trong quá trình thực thi. Khi trạng thái của một thành phần thay đổi, React sẽ tự động cập nhật giao diện người dùng tương ứng để hiển

# Lợi thế
- Ban đầu sinh ra đã là component-based architecture, nên React cho phép tái sử dụng mã, giảm thời gian phát triển và cải thiện hiệu quả bảo trì.
- Chỉ re-render component đã thay đổi, nên React tối ưu hóa hiệu suất ứng dụng với Virtual DOM và cơ chế so sánh khác biệt.
- Tạo trải nghiệm người dùng tốt, đặc biệt là thời gian hiển thị nội dung mới nhanh chóng.
- React có cộng đồng lớn và sôi động, cung cấp tài liệu, thư viện và hỗ trợ giải quyết vấn đề liên quan đến React.
- Có hỗ trợ Server-Side Rendering (SSR) để cải thiện tính tương thích với các công cụ tìm kiếm (search engine).
# Hạn chế
- Không có tính năng hoàn chỉnh cho phát triển ứng dụng di động. Tuy nhiên, React Native có thể được sử dụng để phát triển các ứng dụng di động.
- Khó khăn trong việc học và sử dụng các công nghệ mới liên quan đến React, bao gồm Redux, GraphQL, SSR, ...
- Cần sử dụng nhiều công nghệ liên quan để phát triển một ứng dụng hoàn chỉnh, bao gồm các thư viện và công cụ bổ trợ như Redux, React Router, Webpack, Babel, ...
# Các website phổ biến
## Tại Việt Nam
Dưới đây là top 3 website nổi tiếng ở Việt Nam sử dụng React:

- Lazada (https://www.lazada.vn/)
- Zalo Web (https://chat.zalo.me/)
- VinID (https://www.vinid.net/)

## Trên thế giới
Dưới đây là top 3 website nổi tiếng trên thế giới sử dụng React:

- Facebook (https://www.facebook.com/)
- Instagram (https://www.instagram.com/)
- Netflix (https://www.netflix.com/)

# Hello World
Class Component:
```
import React from 'react';
import ReactDOM from 'react-dom';

class HelloWorld extends React.Component {
  render() {
    return <h1>Hello, World!</h1>;
  }
}

ReactDOM.render(<HelloWorld />, document.getElementById('root'));
```
Functional Component:
```
import React from 'react';
import ReactDOM from 'react-dom';

function HelloWorld() {
  return <h1>Hello, World!</h1>;
}

ReactDOM.render(<HelloWorld />, document.getElementById('root'));

```