# Giới thiệu
Functional Component là một kiểu component trong React được định nghĩa bằng một hàm JavaScript thay vì sử dụng class như Component dạng Class. Functional Component có thể nhận tham số đầu vào là một đối tượng props và trả về một phần tử React để hiển thị trên giao diện. Functional Component là một cách tiếp cận đơn giản và dễ hiểu để tạo các component trong React. Functional Component thường được sử dụng để định nghĩa các component đơn giản, không có nhiều logic xử lý phức tạp và không cần sử dụng các chức năng mà chỉ có thể được định nghĩa bằng Class Component.
# So sánh giữa Functional Component và Class Component

|              |          Functional component         | Class component |
|--------------|:-------------------------------------:|----------------:|
| Định nghĩa   |  Được định nghĩa bằng hàm JavaScript  | Được định nghĩa bằng class |
| Props        | Nhận props dưới dạng đối tượng tham số | Nhận props thông qua phương thức this.props |
| State        |             Sửu dụng Hook             | Có thể sử dụng state thông qua phương thức this.state |
| Lifecycle    | 	Không có lifecycle                 |Có lifecycle (componentWillMount, componentDidMount, etc.) |
| Performance  |Nhanh hơn vì không cần thực hiện các bước khởi tạo bổ sung|Chậm hơn vì cần thực hiện các bước khởi tạo bổ sung|
|Độ phức tạp| Thích hợp cho các component đơn giản, không có nhiều logic xử lý phức tạp| Thích hợp cho các component phức tạp, có nhiều logic xử lý|

Nếu người phát triển tuân thủ kiến trúc Component-based architecture, và chia nhỏ các component hợp lý, thì sử dụng Functional Component có lợi thế hơn hẳn. Trong tất cả các bài training về sau, chúng ta đều sử dụng Functional Component.

# Code examples

### Counter sử dụng functional component 

```
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(count + 1);
  }

  function decrement() {
    setCount(count - 1);
  }

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}

export default Counter;

```

### Counter sử dụng class component

```
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  increment = () => {
    this.setState({
      count: this.state.count + 1
    });
  }

  decrement = () => {
    this.setState({
      count: this.state.count - 1
    });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
        <button onClick={this.decrement}>Decrement</button>
      </div>
    );
  }
}

export default Counter;

```