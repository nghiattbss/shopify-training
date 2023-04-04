# Custom Hook
Custom hook trong React là một cách để tái sử dụng logic stateful giữa các component khác nhau. Nó cho phép bạn tách một phần logic của component và đưa nó vào một hook có thể được sử dụng lại trong bất kỳ component nào.

Khi tạo một custom hook, bạn có thể sử dụng bất kỳ hook nào mà React cung cấp, bao gồm useState, useEffect, useContext, useReducer, useCallback, useMemo, useRef, và useImperativeHandle. Bạn cũng có thể sử dụng một số custom hook khác để tạo ra các hook mới.

Một số lợi ích của việc sử dụng custom hook là giảm sự trùng lặp code, tăng tính tổ chức và độ bảo trì, và tăng tính tái sử dụng của code.

Ví dụ, bạn có thể tạo một custom hook để xử lý các side effect của một component, hoặc để lưu trữ và truy vấn dữ liệu từ một API.

# Sử dụng custom hook để quản lý trạng thái
Dựa vào định nghĩa bên trên, các bạn có thể thấy rằng hoàn toàn có thể sử dụng Hook để quản lý trạng thái của 1 page hoặc components. 

### Code examples

- Quản lý first name và last name
```
import React, { useState } from 'react';

// Custom hook để quản lý state của input field
function useInput(initialValue) {
  const [value, setValue] = useState(initialValue);

  const handleChange = event => {
    setValue(event.target.value);
  };

  return [value, handleChange];
}

// Component sử dụng custom hook
function MyForm() {
  const [firstName, handleFirstNameChange] = useInput('');
  const [lastName, handleLastNameChange] = useInput('');

  const handleSubmit = event => {
    event.preventDefault();
    console.log(`Hello ${firstName} ${lastName}!`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        First Name:
        <input type="text" value={firstName} onChange={handleFirstNameChange} />
      </label>
      <label>
        Last Name:
        <input type="text" value={lastName} onChange={handleLastNameChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

```

- Dùng custom hook với useEffect để lấy về danh sách sản phẩm và hiển thị

Hook: useProductState

```
import { useState, useEffect } from 'react';

const useProductState = () => {
  const [products, setProducts] = useState([]);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    setLoading(true);

    fetch('/api/products')
      .then(res => res.json())
      .then(data => {
        setProducts(data);
        setLoading(false);
      })
      .catch(error => {
        console.error('Error fetching products', error);
        setLoading(false);
      });
  }, []);

  const addProduct = newProduct => {
    setProducts([...products, newProduct]);
  };

  const deleteProduct = id => {
    setProducts(products.filter(product => product.id !== id));
  };

  return { products, loading, addProduct, deleteProduct };
};

export default useProductState;

```

Trong custom hook này, chúng ta sử dụng useState để khai báo state products và loading, và sử dụng useEffect để fetch dữ liệu sản phẩm từ API khi component được render lần đầu tiên. Khi fetch hoàn tất, chúng ta sẽ cập nhật state products và loading.

Chúng ta cũng khai báo hai hàm addProduct và deleteProduct để thêm và xoá sản phẩm, tương tự như trong ví dụ trước đó.

Sau khi khai báo custom hook, chúng ta có thể sử dụng nó trong các component khác nhau như sau:

```
import React from 'react';
import useProductState from './useProductState';

const ProductList = () => {
  const { products, loading, deleteProduct } = useProductState();

  return (
    <div>
      {loading ? <p>Loading...</p> :
        <ul>
          {products.map(product =>
            <li key={product.id}>
              {product.name}
              <button onClick={() => deleteProduct(product.id)}>Delete</button>
            </li>
          )}
        </ul>
      }
    </div>
  );
};

export default ProductList;

```
Trong component này, chúng ta sử dụng custom hook useProductState để lấy danh sách sản phẩm và trạng thái loading. Chúng ta cũng sử dụng hàm deleteProduct để xoá sản phẩm khi người dùng click vào nút "Delete".

Chúng ta nhận thấy rằng, sử dụng custom hook để quản lý trạng thái ở quy mô nhỏ. Để quản lý cả những action bất đồng bộ hoặc global state cho mulitple components thì sẽ phải code thủ công nhiều hơn.

Do vậy, chúng ta cần sử dụng một thư viện mạnh hơn cho những dự án lớn hơn.


