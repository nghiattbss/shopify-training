# Mocha là gì
Mocha là một thư viện testing framework cho JavaScript, được sử dụng cho việc kiểm tra các ứng dụng Node.js và trình duyệt web. Dưới đây là một số tính năng chính của Mocha Test:

- Hỗ trợ nhiều kiểu kiểm tra (assertion library): Mocha hỗ trợ sử dụng nhiều kiểu assertion library như Chai, Should.js, Expect.js, giúp cho việc viết test code dễ dàng hơn.

- Hỗ trợ kiểm tra bất đồng bộ (asynchronous testing): Mocha cung cấp các công cụ để kiểm tra các hàm bất đồng bộ như sử dụng callback hoặc Promise.

- Hỗ trợ tạo báo cáo chi tiết (detailed reporting): Mocha cung cấp các công cụ để tạo ra báo cáo chi tiết về kết quả kiểm tra, giúp dễ dàng xác định lỗi và điều chỉnh ứng dụng.

- Hỗ trợ chạy test trên trình duyệt (browser testing): Mocha cung cấp các công cụ để kiểm tra trên trình duyệt, giúp cho việc kiểm tra tính tương thích của ứng dụng trên nhiều trình duyệt khác nhau.

- Hỗ trợ chạy test song song (parallel testing): Mocha hỗ trợ chạy các test case song song, giúp tăng tốc độ kiểm tra.

- Tùy biến cao: Mocha cho phép tùy biến các thành phần của testing framework, giúp dễ dàng tích hợp với các công cụ khác và phù hợp với nhu cầu của từng dự án.

Các bạn có thể đọc chi tiết hơn [tại đây](https://mochajs.org/)

### Một số ví dụ sử dụng Mocha Test

- Giả sử chúng ta có hàm add, cộng 2 số. Dưới đây là test case đơn giản
```
const assert = require('assert');
const add = require('./add');

describe('add function', () => {
  it('should add two numbers', () => {
    assert.equal(add(1, 2), 3);
  });

  it('should add two negative numbers', () => {
    assert.equal(add(-1, -2), -3);
  });
});

```

- Test case cho một async function

```
const assert = require('assert');
const fetchData = require('./fetchData');

describe('fetchData function', () => {
  it('should return correct data', () => {
    return fetchData('https://api.example.com/data')
      .then((data) => {
        assert.equal(data, 'some data');
      });
  });

  it('should reject with error if URL is invalid', () => {
    return fetchData('invalid_url')
      .catch((err) => {
        assert.equal(err.message, 'Invalid URL');
      });
  });
});

```

- Test case cho một Class
```
const assert = require('assert');
const Calculator = require('./Calculator');

describe('Calculator class', () => {
  let calculator;

  beforeEach(() => {
    calculator = new Calculator();
  });

  it('should add two numbers', () => {
    assert.equal(calculator.add(1, 2), 3);
  });

  it('should subtract two numbers', () => {
    assert.equal(calculator.subtract(3, 2), 1);
  });
});

```



# Jest là gì

Jest là một thư viện kiểm thử JavaScript mã nguồn mở, được phát triển bởi Facebook. Jest có các tính năng chính sau:

- Tự động phát hiện các test case và thực hiện chúng một cách tự động.
- Snapshot testing: cho phép bạn kiểm tra các snapshot của UI và đảm bảo rằng chúng không bị thay đổi một cách vô ý.
- Tích hợp sẵn với Babel, cho phép bạn viết mã mới nhất của JavaScript mà không cần phải lo lắng về việc đồng bộ hóa phiên bản.
- Hỗ trợ các mock function để giả lập một số hành vi.
- Hỗ trợ các test runner khác như Jasmine, Mocha hoặc QUnit.

Ngoài ra, Jest cũng hỗ trợ các tính năng khác như code coverage, watch mode, parallelization, tự động giảm thiểu thời gian chạy test, và rất nhiều tính năng hữu ích khác.

Các bạn có thể đọc chi tiết hơn [tại đây](https://jestjs.io/)

# So sánh Mocha vs Jest
Dưới đây là so sánh tương đối giữa Mocha và Jest, tuy nhiên trong từng trường hợp cụ thể có thể khác nhau, ví dụ như Speed của chương trình chạy test.

(Bảng so sánh này được thực hiện dựa trên các phiên bản mới nhất đầu năm 2022.)


|          |         Mocha          |                       Jest |
|----------|:----------------------:|---------------------------:|
| Ngôn ngữ | JavaScript, TypeScript | JavaScript, TypeScript |
|Assertions|            Requires an external assertion library (e.g. Chai)            |Includes built-in assertion library|
|Syntax|	describe(), it(), before(), after(), beforeEach(), afterEach()|describe(), it(), beforeAll(), afterAll(), beforeEach(), afterEach(), test()|
|Mocking|Requires external libraries (e.g. Sinon)|Includes built-in mocking functionality (Jest Mocks)|
|Coverage|Requires external tools (e.g. Istanbul)|Includes built-in code coverage tools|
|Snapshot testing|Not built-in but can be implemented with external libraries (e.g. Jest Snapshot)|Includes built-in snapshot testing feature|
|Speed|Faster|Slower due to additional built-in features|

Nhìn như bảng so sánh trên, chúng ta thấy rằng tùy theo nhu cầu sử dụng, chúng ta có thể sài Mocha hoặc Jest. Jest rất đầy đủ tính năng và hỗ trợ tận răng, tuy nhiên Mocha thì nhẹ và dễ học hơn.

# Giải thích một số khái niệm

- Mocking: giả lập 1 đối tượng thật, giúp khi test, không cần trực tiếp gọi đến các đối tượng thật.
```
import React from 'react';
import { render, screen } from '@testing-library/react';
import axios from 'axios';
import MyComponent from './MyComponent';

// Mock the axios module
jest.mock('axios');

describe('MyComponent', () => {
  test('renders data from API', async () => {
    // Define the mocked response from axios
    const mockedResponse = { data: { name: 'John' } };

    // Mock the axios get function to return the mocked response
    axios.get.mockResolvedValue(mockedResponse);

    // Render the component
    render(<MyComponent />);

    // Assert that the component displays the data from the API
    expect(await screen.findByText('Name: John')).toBeInTheDocument();
  });
});

```

Trong ví dụ này, chúng ta sử dụng Jest để mocking module axios, đảm bảo rằng các request từ axios sẽ không được thực sự gửi đến server. Thay vào đó, chúng ta mock lại các giá trị trả về từ axios để kiểm tra các phản hồi từ server mà không cần phải gọi thực sự đến server.

- Coverage: là một công cụ, cho biết bao nhiêu phần trăm mã nguồn của một ứng dụng đã được thực thi trong quá trình thử nghiệm. Nó được sử dụng để đo lường chất lượng của bộ kiểm tra và phát hiện các vùng mã không được thử nghiệm hoặc chưa đủ bảo vệ.

Giả sử chúng ta có một file sum.js như sau:

```
function sum(a, b) {
  return a + b;
}
module.exports = sum;

```

Chúng ta muốn viết test case cho hàm sum này và kiểm tra độ phủ (coverage) của mã nguồn. Để làm điều này, chúng ta cần cài đặt Jest và các công cụ liên quan:

```
npm install jest jest-cli --save-dev
```

Sau đó, chúng ta viết file sum.test.js để test hàm sum:

```
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});

test('adds 0 + 0 to equal 0', () => {
  expect(sum(0, 0)).toBe(0);
});

```

File test này sẽ chạy 2 test case, kiểm tra kết quả trả về của hàm sum với các tham số khác nhau.

Sau đó, chúng ta chạy lệnh sau để chạy Jest và xem độ phủ của mã nguồn:

```
npm test -- --coverage
```

Kết quả sẽ hiển thị tỷ lệ phủ của mã nguồn, được tính dựa trên các test case đã viết:

```
----------------------|---------|----------|---------|---------|-------------------
File                  | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
----------------------|---------|----------|---------|---------|-------------------
All files             |   66.67 |      100 |      50 |      75 |                   
 sum.js               |   66.67 |      100 |      50 |      75 |                   3
----------------------|---------|----------|---------|---------|-------------------

```

Đây là kết quả tính toán độ phủ của mã nguồn. Trong trường hợp này, mã nguồn có 66.67% phủ sóng cho statements, 100% cho branches, 50% cho functions và 75% cho lines. Bên cạnh đó, kết quả cũng hiển thị số dòng chưa được phủ sóng bởi các test case.

- Snapshot testing: Snapshot testing là một kỹ thuật test trong đó ta tạo ra một bản snapshot (một bản chụp ảnh) của một component hoặc một đoạn code bất kỳ. Khi thay đổi code, ta so sánh bản snapshot hiện tại với bản snapshot cũ. Nếu hai bản snapshot khác nhau, Jest sẽ báo lỗi và yêu cầu ta cập nhật lại bản snapshot. Kỹ thuật này giúp ta kiểm tra sự thay đổi của component hoặc code một cách nhanh chóng và đảm bảo tính nhất quán của UI.

```
import React from 'react';
import renderer from 'react-test-renderer';
import MyComponent from './MyComponent';

test('MyComponent should render correctly', () => {
  const tree = renderer.create(<MyComponent />).toJSON();
  expect(tree).toMatchSnapshot();
});

```

Ở đây, chúng ta đang snapshot test cho component ```MyComponent```. Chúng ta sử dụng ```renderer.create``` để tạo một snapshot của component và ```toJSON()``` để chuyển đổi nó thành một JSON object.

```toMatchSnapshot()``` là một hàm của Jest để so sánh snapshot hiện tại với snapshot trước đó, nếu có. Nếu không có snapshot trước đó, Jest sẽ tạo ra một snapshot mới.

Mỗi lần chạy test, Jest sẽ so sánh snapshot hiện tại với snapshot trước đó. Nếu có sự khác biệt, Jest sẽ cảnh báo và yêu cầu bạn xác nhận lại snapshot mới. Nếu bạn xác nhận snapshot mới, Jest sẽ lưu nó lại và sử dụng nó để so sánh trong các lần test tiếp theo.

