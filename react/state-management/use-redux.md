# React Redux
Redux là một thư viện quản lý state được sử dụng phổ biến trong các ứng dụng React. Nó giúp quản lý state tập trung và dễ dàng điều khiển trong toàn bộ ứng dụng. Các state của ứng dụng được lưu trữ trong một store trung tâm, và chỉ có thể được sửa đổi thông qua các actions được gửi đến reducers. Actions là các đối tượng plain JavaScript và reducers là các hàm pure JavaScript xử lý các actions này và trả về một state mới cho store.

Redux có thể được sử dụng với các ứng dụng React, React Native hoặc bất kỳ một framework JavaScript nào khác. Redux được coi là một công cụ mạnh mẽ cho quản lý state và được sử dụng rộng rãi trong các ứng dụng lớn và phức tạp.

Chi tiết tài liệu [ở đây](https://redux.js.org/introduction/getting-started)

Code examples:

- Đây là một ví dụ đơn giản sử dụng Redux và Javascript thông thường để quản lý trạng thái đếm.
```
import { createStore } from 'redux';

// Khai báo action types
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

// Khai báo các actions
export const increment = () => ({
  type: INCREMENT,
});

export const decrement = () => ({
  type: DECREMENT,
});

// Khai báo reducer
const counterReducer = (state = 0, action) => {
  switch (action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

// Khởi tạo store
const store = createStore(counterReducer);

// Đăng ký lắng nghe sự thay đổi của store
store.subscribe(() => console.log(store.getState()));

// Dispatch các action để thay đổi trạng thái
store.dispatch(increment());
store.dispatch(increment());
store.dispatch(decrement());

```
Khi chạy đoạn code trên, kết quả hiển thị trong console sẽ là:
```
2
3
2
```
# Redux Toolkit 

Redux Toolkit là một thư viện giúp đơn giản hóa việc sử dụng Redux trong ứng dụng React. Thay vì phải viết nhiều code để tạo ra các actions, reducers và middleware, Redux Toolkit cung cấp các utilities và hàm helper để giúp giảm thiểu việc lặp lại code, tăng tính ổn định và hiệu quả của ứng dụng. Redux Toolkit cũng giới thiệu một khái niệm mới gọi là "slices", giúp chia nhỏ store của Redux thành các phần nhỏ hơn, dễ quản lý hơn.

Chi tiết tài liệu [ở đây](https://redux-toolkit.js.org/tutorials/overview)

### Redux Thunk

Redux Thunk là một middleware của Redux, được sử dụng để xử lý các action trả về một hàm thay vì một object. Điều này cho phép các action được xử lý bất đồng bộ (asynchronous) và thực hiện các side effect như truy vấn API hay lưu trữ dữ liệu.

Middleware Redux Thunk cho phép chúng ta viết các action creators trả về một hàm thay vì một object, trong đó hàm đó sẽ nhận các tham số dispatch và getState. Điều này cho phép chúng ta thực hiện các logic bất đồng bộ và side effect, và có thể sử dụng thông tin hiện tại từ store thông qua getState và cập nhật store thông qua dispatch.

Chi tiết tài liệu [ở đây](https://redux.js.org/usage/writing-logic-thunks)

Ví dụ, nếu chúng ta muốn lấy dữ liệu từ một API, chúng ta có thể sử dụng Redux Thunk để viết action creator như sau:

```
import { createSlice } from '@reduxjs/toolkit';
import { fetchUserData } from './api';

const slice = createSlice({
  name: 'user',
  initialState: {
    data: null,
    loading: false,
    error: null,
  },
  reducers: {
    fetchUserRequest: (state) => {
      state.loading = true;
    },
    fetchUserSuccess: (state, action) => {
      state.data = action.payload;
      state.loading = false;
      state.error = null;
    },
    fetchUserFailure: (state, action) => {
      state.loading = false;
      state.error = action.payload;
    },
  },
});

export const { fetchUserRequest, fetchUserSuccess, fetchUserFailure } = slice.actions;

export const fetchUser = (userId) => async (dispatch, getState) => {
  dispatch(fetchUserRequest());

  try {
    const userData = await fetchUserData(userId);
    dispatch(fetchUserSuccess(userData));
  } catch (error) {
    dispatch(fetchUserFailure(error.message));
  }
};

```

Ở đây, fetchUser là một action creator trả về một hàm bất đồng bộ. Trong hàm này, chúng ta gọi fetchUserRequest trước khi bắt đầu thực hiện API request. Sau khi nhận được kết quả, chúng ta gọi fetchUserSuccess với dữ liệu nhận được hoặc fetchUserFailure nếu xảy ra lỗi. Cả hai action này đều là các action bình thường trả về một object. Trong quá trình này, chúng ta có thể cập nhật state trong store thông qua các action này.

Ví dụ chỉ mang tính chất tham khảo, không phải một code chuẩn để sử dụng trong thất cả các dự án thực tế.

### Redux RTK query
Redux Toolkit Query (RTK Query) là một thư viện của Redux Toolkit giúp quản lý việc truy vấn API và cache trong Redux một cách dễ dàng. Thay vì phải tự viết các action, reducer, middleware để quản lý việc fetch data từ API, RTK Query cung cấp cho chúng ta các hàm để thực hiện các truy vấn và tự động sinh ra các action và reducer tương ứng. Ngoài ra, RTK Query còn có khả năng tự động cache kết quả và thực hiện các request tối ưu hơn bằng cách sử dụng memoization và batching.

Với RTK Query, ta chỉ cần định nghĩa các endpoints của API, các query và mutation tương ứng, sau đó sử dụng các hooks được sinh ra bởi RTK Query để gọi các truy vấn này trong components. Khi thực hiện truy vấn, RTK Query sẽ tự động sinh ra các action và reducer tương ứng, và kết quả sẽ được lưu vào cache để sử dụng lại ở lần gọi tiếp theo.

RTK Query cũng cung cấp khả năng sử dụng middleware để xử lý các thông báo lỗi, gọi các API khác nhau dựa trên điều kiện, và tùy chỉnh cách cache hoạt động.

Việc sử dụng RTK Query giúp giảm thiểu rất nhiều boilerplate code trong việc quản lý state và truy vấn API, giúp cho việc phát triển ứng dụng nhanh hơn và dễ bảo trì hơn.

Chi tiết tài liệu [ở đây](https://redux-toolkit.js.org/tutorials/rtk-query)

Để sử dụng, trước hết cần cài đặt
```
npm install @reduxjs/toolkit react-redux @reduxjs/toolkit/query
```
Tiếp theo, chúng ta sẽ khai báo một API slice bằng cách sử dụng createApi từ @reduxjs/toolkit/query. Ở đây, chúng ta sẽ lấy dữ liệu từ một REST API endpoint có tên là "todos" và trả về danh sách các công việc.
```
import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query';

export const apiSlice = createApi({
  reducerPath: 'api',
  baseQuery: fetchBaseQuery({ baseUrl: 'https://jsonplaceholder.typicode.com' }),
  endpoints: (builder) => ({
    getTodos: builder.query({
      query: () => '/todos',
    }),
  }),
});

```
Trong ví dụ này, chúng ta sử dụng createApi để khai báo một slice của store với reducerPath là "api". Chúng ta cũng khai báo một baseQuery với baseUrl là "https://jsonplaceholder.typicode.com". Tiếp theo, chúng ta định nghĩa một endpoint với tên là "getTodos" và trả về danh sách các công việc bằng cách truy vấn đến "/todos".

Sau đó, chúng ta cần khai báo slice reducer và các selectors sử dụng apiSlice.reducer và apiSlice.selectors.

```
import { combineReducers } from '@reduxjs/toolkit';
import { apiSlice } from './apiSlice';

const rootReducer = combineReducers({
  [apiSlice.reducerPath]: apiSlice.reducer,
});

export const { useGetTodosQuery } = apiSlice;

export const selectTodos = (state) => state.api.data;
export const selectTodosLoading = (state) => state.api.isLoading;

```

### So sánh Redux Thunk và Sagas

|          | Redux Thunk | Redux Saga |
|----------|:-----------:|-----------:|
| Thao tác bất đồng bộ |      v      |          v |
|Làm việc với Promises|      v      |            |
|Làm việc với Generators|             |          v |
|Được sử dụng phổ biến hơn|      v      |            |
|Cú pháp lập trình đơn giản hơn|      v      |            |
|Tính linh hoạt cao hơn|             |          v |
|Xử lý các trường hợp phức tạp hơn|             |          v |
|Độ phức tạp khi triển khai|      Thấp       |           Cao |

Như vậy, Redux Thunk và Redux Saga đều có thể thực hiện các thao tác bất đồng bộ, nhưng Redux Thunk làm việc với Promises trong khi Redux Saga sử dụng Generators. Redux Thunk cú pháp đơn giản hơn và được sử dụng phổ biến hơn, trong khi Redux Saga có tính linh hoạt cao hơn và có thể xử lý các trường hợp phức tạp hơn. Tuy nhiên, độ phức tạp khi triển khai Redux Saga lại cao hơn.

Nhìn vào bảng so sánh trên, chúng ta có thể kết luận như vậy. Trên thực tế triển khai Redux Toolkit là đơn giản là dễ quản lý hơn, tùy vào nhu cầu sử dụng, chúng ta không nên sử dụng Saga nếu không có mục đích rõ ràng và thực sự cần thiết. 

### So sánh RTK query và react hook useQuery

Cả RTK Query và hook useQuery đều là các thư viện cho phép thực hiện các truy vấn API trong ứng dụng React. Dưới đây là một số điểm khác nhau giữa RTK Query và hook useQuery:

|          | RTK Query | Hook useQuery |
|----------|:---------:|--------------:|
|Phiên bản|Có sẵn trong Redux Toolkit|Phải cài đặt bằng riêng|
|Tính năng|Có thể xử lý cache, tự động refresh, chuyển đổi dữ liệu|Không có tính năng xử lý cache, tự động refresh hay chuyển đổi dữ liệu|
|Cú pháp|Được định nghĩa bằng các hàm được tạo ra bởi createApi() |Được sử dụng như một hook thường|
|Kiến trúc|Sử dụng kiến trúc Slice, giúp tổ chức code dễ dàng hơn|Phù hợp với các dự án nhỏ, không cần quản lý state toàn cục|

Như vậy, RTK Query là một thư viện mạnh mẽ và có tính năng đầy đủ hơn so với hook useQuery. Tuy nhiên, nếu dự án của bạn không cần quản lý state toàn cục hoặc không cần tính năng cache, tự động refresh hay chuyển đổi dữ liệu, hook useQuery cũng là một lựa chọn tốt.
