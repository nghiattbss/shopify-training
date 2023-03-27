# React Router là gì
React Router là một thư viện điều hướng phổ biến cho ứng dụng React. Nó cho phép bạn tạo ra các đường dẫn URL tương ứng với các component và điều hướng giữa chúng mà không cần phải reload lại trang. React Router cung cấp các thành phần để quản lý việc điều hướng, bao gồm Route, Link, Redirect, Switch và nhiều thành phần khác.
# Code Examples
Chi tiết về React Router ở đây [React Router](https://reactrouter.com/en/main).
Dưới đây là một số ví dụ cơ bản.
### Điều hướng sang các trang khác nhau
```
import { BrowserRouter, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Route exact path="/" component={HomePage} />
      <Route path="/about" component={AboutPage} />
      <Route path="/contact" component={ContactPage} />
    </BrowserRouter>
  );
}
```
#### Sử dụng Link 

```
import { Link } from 'react-router-dom';

function Navbar() {
  return (
    <nav>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/about">About</Link></li>
        <li><Link to="/contact">Contact</Link></li>
      </ul>
    </nav>
  );
}

```

### Sử dụng userParams hook để lấy params

```
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { username } = useParams();

  return (
    <div>
      <h1>{username}'s Profile</h1>
      <p>Here is some information about {username}...</p>
    </div>
  );
}
```