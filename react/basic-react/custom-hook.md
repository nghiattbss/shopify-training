# Custom Hook là gì
React Custom Hook là code block tái sử dụng trong React, cho phép bạn tái sử dụng logic stateful giữa các component khác nhau.
# Các quy tắc đặt tên của custom hook trong React bao gồm:

- Tên của custom hook phải bắt đầu bằng từ "use" để React biết rằng đó là một hook.
- Tên của custom hook nên mô tả chức năng của hook.
- Tên của custom hook nên được viết bằng chữ cái viết thường đối với các từ khóa, và chữ cái đầu tiên của mỗi từ nối tiếp phải viết hoa (ví dụ: useCounter, useFetchData).
- Nếu custom hook của bạn có các tham số đầu vào, hãy thêm tên của tham số đó vào tên của hook để giúp người đọc hiểu rõ hơn (ví dụ: useInput, useLocalStorage).

# Code Examples
- Sử dụng Custom Hook để xử lý form:
```
import { useState } from 'react';

const useForm = (callback) => {
  const [values, setValues] = useState({});

  const handleSubmit = (event) => {
    if (event) event.preventDefault();
    callback();
  };

  const handleChange = (event) => {
    event.persist();
    setValues(values => ({ ...values, [event.target.name]: event.target.value }));
  };

  return {
    handleChange,
    handleSubmit,
    values,
  }
};

export default useForm;

```
- Sử dụng Custom Hook để lấy dữ liệu từ API:
```
import { useState, useEffect } from 'react';
import axios from 'axios';

const useFetchData = (url) => {
  const [data, setData] = useState([]);
  const [isLoading, setIsLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const result = await axios(url);
        setData(result.data);
      } catch (error) {
        setError(error);
      }
      setIsLoading(false);
    };
    fetchData();
  }, [url]);

  return { data, isLoading, error };
};

export default useFetchData;

```
- Sử dụng Custom Hook để quản lý Dark Mode:
```
import { useState, useEffect } from 'react';

const useDarkMode = () => {
  const [theme, setTheme] = useState('light');
  const [mountedComponent, setMountedComponent] = useState(false);

  const setMode = mode => {
    window.localStorage.setItem('theme', mode);
    setTheme(mode);
  };

  const toggleTheme = () => {
    if (theme === 'light') {
      setMode('dark');
    } else {
      setMode('light');
    }
  };

  useEffect(() => {
    const localTheme = window.localStorage.getItem('theme');
    if (localTheme) {
      setTheme(localTheme);
    } else {
      setMode('light');
    }
    setMountedComponent(true);
  }, []);

  return [theme, toggleTheme, mountedComponent];
};

export default useDarkMode;

```

- Sử dụng Custom Hook để xử lý localStorage:
```
import { useState } from 'react';

const useLocalStorage = (key, initialValue) => {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.log(error);
      return initialValue;
    }
  });

  const setValue = value => {
    try {
      const valueToStore = value instanceof Function ? value(storedValue) : value;
      setStoredValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.log(error);
    }
  };

  return [storedValue, setValue];
};

export default useLocalStorage;

```

- Custom hook to handle window resize:
```
import { useState, useEffect } from "react";

const useWindowResize = () => {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });

  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    };

    window.addEventListener("resize", handleResize);

    return () => {
      window.removeEventListener("resize", handleResize);
    };
  }, []);

  return windowSize;
};

export default useWindowResize;

```