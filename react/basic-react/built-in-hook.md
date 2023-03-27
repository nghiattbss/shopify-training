# React Hooks là gì
React Hooks là một tính năng được giới thiệu từ phiên bản React 16.8, cho phép chúng ta sử dụng state và các tính năng khác của React (như lifecycle methods, context, refs...) trong functional components. Trước khi Hooks được giới thiệu, chúng ta chỉ có thể sử dụng state và các tính năng khác này trong class components. Tuy nhiên, với sự xuất hiện của Hooks, chúng ta có thể viết các functional components có khả năng đáp ứng các yêu cầu phức tạp hơn, giảm thiểu sự phức tạp của việc quản lý state và tái sử dụng code.

Hooks được xây dựng dựa trên cơ chế của closures và hooks chỉ được sử dụng bên trong functional components. Một số Hooks phổ biến bao gồm **useState, useEffect, useContext, useReducer, useMemo, useCallback, useRef,...**

Nhờ vào React Hooks, chúng ta có thể viết code ngắn gọn và dễ đọc hơn, và giúp chúng ta tránh được sự lộn xộn của việc quản lý state và lifecycle methods trong các component.
# Khác biệt khi sử dụng Hook và LifeCycle

| Lifecycle methods |     Hooks     |
|-------------------|:-------------:|
| componentDidMount         | useEffect(() => {}, [])  |
| componentDidUpdate          |   useEffect(() => {})    |
| componentWillUnmount          | useEffect(() => { return () }) |
|shouldComponentUpdate |useMemo() |
|getDerivedStateFromProps |useReducer() |
|getSnapshotBeforeUpdate |useLayoutEffect() |

# Giải thích và code cho từng hook

Có các loại hook sau:
- useState
- useEffect
- useContext
- useReducer
- useCallback
- useMemo
- useRef
- useImperativeHandle
- useLayoutEffect
- useDebugValue

### Use State
Sử dụng hook với một state dạng dữ liệu nguyên thủy.
```
import React, { useState } from 'react';

function Counter() {
  // Khởi tạo state count với giá trị ban đầu là 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Bạn đã nhấn {count} lần</p>
      <button onClick={() => setCount(count + 1)}>Nhấn để tăng</button>
    </div>
  );
}

export default Counter;

```

Khi dùng object

```
import React, { useState } from 'react';

function UserInfo() {
  // Khởi tạo state user với giá trị ban đầu là một đối tượng
  const [user, setUser] = useState({
    name: '',
    age: '',
    email: ''
  });

  // Hàm xử lý sự kiện khi người dùng nhập thông tin vào form
  const handleInputChange = event => {
    const { name, value } = event.target;
    setUser(prevUser => ({ ...prevUser, [name]: value }));
  };

  return (
    <form>
      <label>
        Họ tên:
        <input type="text" name="name" value={user.name} onChange={handleInputChange} />
      </label>
      <label>
        Tuổi:
        <input type="text" name="age" value={user.age} onChange={handleInputChange} />
      </label>
      <label>
        Email:
        <input type="email" name="email" value={user.email} onChange={handleInputChange} />
      </label>
    </form>
  );
}

export default UserInfo;

```

Chú ý đoạn code sau:
```
setUser(prevUser => ({ ...prevUser, [name]: value }));
```
Chúng ta phải tạo ra 1 clone object để React biết rằng có sự thay đổi trạng thái, ngược lại React sẽ không có phép so sánh dữ liệu cùng một Object trước và sau, và state sẽ không được cập nhật.

### Best practice khi sử dụng useEffect

Dưới đây là ví dụ về việc sử dụng Axios và useEffect để lấy dữ liệu người dùng, các bạn có thể sử dụng fetch thay thế.

```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserList() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        setUsers(response.data);
      })
      .catch(error => {
        console.log(error);
      });
  }, []);

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;

```
Chú ý các vấn đề sau khi sử dụng useEffect:
- **Sử dụng dependencies:** hãy đảm bảo chỉ định những dependency cần thiết. Nếu không, hook useEffect có thể được gọi nhiều lần, và page có thể bị re-render liên tục.
- **Chú ý cleanup**: nếu có sử dụng những hàm như setInterval, hoặc event listener...thì nên chú ý cleanup sau khi đã đạt được mục đích. Bạn có thể sử dụng return trong hàm callback của hook useEffect để cleanup các resource đó.
- **Gộp/Tách logic**: Cần cân nhắc khi tách logic trong useEffect ra làm các hook riêng biệt. Đôi lúc sẽ rất hiệu quả để quản lý code, nhưng có thể gây tình trạng re-render nhiều lần, nếu mỗi hook lại thay đổi state.
- **Hạn chế tác động đến DOM**: Nếu bạn muốn sử dụng hook useEffect để thao tác trực tiếp với DOM, hãy đảm bảo rằng bạn hạn chế tác động đến DOM càng ít càng tốt. Thay vào đó, hãy sử dụng các thư viện hoặc công cụ khác như react-router hoặc redux để quản lý state của component.
- **Sử dụng useCallback để optimize**: Nếu bạn sử dụng hàm callback trong hook useEffect và hàm callback đó có dependencies, hãy sử dụng hook useCallback để optimize lại hàm đó và giảm thiểu sự render lại của component.

### useContext
### useReducer
### useCallback
### useMemo
### useRef
### useImperativeHandle
### useLayoutEffect
### useDebugValue
