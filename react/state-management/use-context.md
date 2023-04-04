# Use Context

Trong React, useContext là một hook cho phép các component con có thể truy cập trực tiếp vào context của component cha mà không cần truyền props qua nhiều tầng. Khi sử dụng useContext, ta cần truyền vào context object (được tạo bởi React.createContext()) và hook sẽ trả về giá trị hiện tại của context đó. Khi giá trị context thay đổi, hook sẽ tự động cập nhật lại component sử dụng nó.

Ví dụ đơn giản về sử dụng context

```
import React, { useContext } from 'react';

// Create a context
const MyContext = React.createContext();

// Create a provider component for the context
function MyContextProvider(props) {
  const value = { data: 'some data' }; // data to be shared by the context
  return <MyContext.Provider value={value}>{props.children}</MyContext.Provider>;
}

// Child component that uses the context
function ChildComponent() {
  const contextValue = useContext(MyContext); // Get the context value
  return <div>{contextValue.data}</div>; // Use the context value in the component
}

// Parent component
function ParentComponent() {
  return (
    <MyContextProvider>
      <ChildComponent />
    </MyContextProvider>
  );
}

```

# Use Reducer
useReducer là một trong những hooks cung cấp bởi React giúp quản lý state của component. Nó tương tự như useState, nhưng sử dụng một hàm reducer để xác định state mới thay vì một giá trị mới.

Cú pháp sử dụng useReducer như sau:

```
const [state, dispatch] = useReducer(reducer, initialState);

```

Trong đó:

- state: đại diện cho state hiện tại
- dispatch: là một hàm giúp thực thi các hành động (actions) để cập nhật state mới
- reducer: là một hàm xử lý các actions và trả về state mới
- initialState: là giá trị ban đầu của state
- Khi gọi hàm dispatch với một action, React sẽ gọi hàm reducer với các tham số là state hiện tại và action đó. Hàm reducer sẽ xử lý action và trả về state mới. Sau đó, React sẽ cập nhật state mới và re-render component.

Đây là một ví dụ về cách sử dụng useReducer:
```
import React, { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </>
  );
}

```
Trong ví dụ này, chúng ta định nghĩa một hàm reducer để xử lý các actions. Trong component Counter, chúng ta sử dụng useReducer để khởi tạo state ban đầu và lấy ra các giá trị state và dispatch. Các nút + và - được sử dụng để gọi hàm dispatch với các actions tương ứng, từ đó cập nhật state mới.

# Kết hợp useContext và useReducer để quản lý trạng thái

```
import React, { createContext, useContext, useReducer } from 'react';

// Khởi tạo context
const MyContext = createContext(null);

// Khởi tạo reducer
const reducer = (state, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
};

// Khởi tạo component cha
const Parent = () => {
  const [state, dispatch] = useReducer(reducer, { count: 0 });
  return (
    <MyContext.Provider value={{ state, dispatch }}>
      <Child />
    </MyContext.Provider>
  );
};

// Khởi tạo component con
const Child = () => {
  const { state, dispatch } = useContext(MyContext);
  const handleIncrement = () => dispatch({ type: 'INCREMENT' });
  const handleDecrement = () => dispatch({ type: 'DECREMENT' });

  return (
    <div>
      <h2>Count: {state.count}</h2>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  );
};

export default Parent;

```

Trong ví dụ này, ta sử dụng createContext để khởi tạo context, và useContext để sử dụng context này trong Child component. Ta cũng sử dụng useReducer để quản lý trạng thái và xử lý các hành động (action) được gửi từ Child component thông qua dispatch function.

# Multiple reducers
Để có thể quản lý nhiều reducer, chúng ta cần tách ra. Dưới đây là ví dụ để quản lý công việc và nhân viên của một công ty

```
import React, { useContext, useReducer } from 'react';

// Khai báo initial state
const initialState = {
  tasks: [],
  employees: []
};

// Khai báo action types
const ADD_TASK = 'ADD_TASK';
const REMOVE_TASK = 'REMOVE_TASK';
const ADD_EMPLOYEE = 'ADD_EMPLOYEE';
const REMOVE_EMPLOYEE = 'REMOVE_EMPLOYEE';

// Khai báo các reducers
const tasksReducer = (state, action) => {
  switch (action.type) {
    case ADD_TASK:
      return {
        ...state,
        tasks: [...state.tasks, action.payload]
      };
    case REMOVE_TASK:
      return {
        ...state,
        tasks: state.tasks.filter(task => task.id !== action.payload)
      };
    default:
      return state;
  }
};

const employeesReducer = (state, action) => {
  switch (action.type) {
    case ADD_EMPLOYEE:
      return {
        ...state,
        employees: [...state.employees, action.payload]
      };
    case REMOVE_EMPLOYEE:
      return {
        ...state,
        employees: state.employees.filter(employee => employee.id !== action.payload)
      };
    default:
      return state;
  }
};

// Khai báo context
const CompanyContext = React.createContext(initialState);

// Provider cho CompanyContext
const CompanyProvider = ({ children }) => {
  const [tasksState, tasksDispatch] = useReducer(tasksReducer, initialState);
  const [employeesState, employeesDispatch] = useReducer(employeesReducer, initialState);

  return (
    <CompanyContext.Provider value={{ tasksState, tasksDispatch, employeesState, employeesDispatch }}>
      {children}
    </CompanyContext.Provider>
  );
};

// Component sử dụng CompanyContext
const Company = () => {
  const { tasksState, tasksDispatch, employeesState, employeesDispatch } = useContext(CompanyContext);

  // Handlers
  const handleAddTask = () => {
    const newTask = { id: Math.random(), name: `Task ${Math.random()}` };
    tasksDispatch({ type: ADD_TASK, payload: newTask });
  };

  const handleRemoveTask = taskId => {
    tasksDispatch({ type: REMOVE_TASK, payload: taskId });
  };

  const handleAddEmployee = () => {
    const newEmployee = { id: Math.random(), name: `Employee ${Math.random()}` };
    employeesDispatch({ type: ADD_EMPLOYEE, payload: newEmployee });
  };

  const handleRemoveEmployee = employeeId => {
    employeesDispatch({ type: REMOVE_EMPLOYEE, payload: employeeId });
  };
    const handleRemoveEmployee = employeeId => {
      employeesDispatch({ type: REMOVE_EMPLOYEE, payload: employeeId });
    };
    
    const handleAddEmployee = () => {
      const newEmployee = { id: Math.random(), name: `Employee ${Math.random()}` };
      employeesDispatch({ type: ADD_EMPLOYEE, payload: newEmployee });
    };

  // Render
  return (
    <div>
      <h2>Tasks:</h2>
      <ul>
        {tasksState.tasks.map(task => (
          <li key={task.id}>
            {task.name} <button onClick={() => handleRemoveTask(task.id)}>Remove</button>
          </li>
        ))}
      </ul>
      <button onClick={handleAddTask}>Add Task</button>

      <h2>Employees:</h2>
      <ul>
        {employeesState.employees.map(employee => (
          <li key={employee.id}>
            {employee.name} <button onClick={() => handleRemoveEmployee(employee.id)}>Remove</button>
          </li>
        ))}
      </ul>
      <button onClick={handleAddEmployee}>Add Employee</button>
    </div>
  )    
```
Trong file _app.js

```
function App() {
  return (
    <CompanyProvider>
      <div className="App">
        <header className="App-header">
          <h1>Company Management</h1>
        </header>
        <main>
          <Company />
        </main>
      </div>
    </CompanyProvider>
  );
}

export default App;

```
Không phức tạp, nhưng nếu số lượng reducer lên tới hàng chục thì cần phải cấu trúc lại các folder source code thật tốt để quản lý.

Câu hỏi đặt ra là nếu xử lý các function bất đồng bộ, ví dụ: gọi data từ API xuống thì chúng ta xử lý ra sao?

Chúng ta có thể sử dụng các thư viện bên ngoài như Redux Thunk để quản lý các việc này, hoặc thủ công sử dụng fetch then như ví dụ sau:

```
// Gửi yêu cầu API và cập nhật trạng thái
useEffect(() => {
  dispatch({ type: 'FETCH_START' });
  fetch('https://jsonplaceholder.typicode.com/todos/1')
    .then(response => response.json())
    .then(data => {
      dispatch({ type: 'FETCH_SUCCESS', payload: data });
    })
    .catch(error => {
      dispatch({ type: 'FETCH_ERROR', payload: error });
    });
}, []);

```

