# Typescript

TypeScript là một ngôn ngữ lập trình mã nguồn mở, được phát triển bởi Microsoft. Nó là một phiên bản mở rộng của JavaScript, hỗ trợ các tính năng mới như Static Type, OOP, và các tính năng của ECMAScript mới. TypeScript có thể chạy trên bất kỳ nền tảng nào hỗ trợ JavaScript, và cung cấp một công cụ mạnh mẽ để phát triển các ứng dụng web phức tạp và dễ bảo trì.

Tài liệu chi tiết [tại đây](https://www.typescriptlang.org/)

# Cấu hính tsconfig.json

`tsconfig.json` là một tệp cấu hình TypeScript được sử dụng để chỉ định cài đặt cho trình biên dịch TypeScript. Nó cho phép bạn tùy chỉnh cách TypeScript được biên dịch và cung cấp cho trình biên dịch một số thông tin về dự án.

Dưới đây là một số cách sử dụng tsconfig.json:

- Thiết lập môi trường:
```
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "lib": ["es6", "dom"],
    "outDir": "dist"
  },
  "include": ["src"]
}

```
Trong đó:

    - "target" xác định phiên bản JavaScript mà TypeScript nên tạo ra.
    - "module" chỉ định loại module được sử dụng trong dự án.
    - "lib" liệt kê các thư viện được sử dụng trong dự án.
    - "outDir" chỉ định thư mục đầu ra.
    - "include" chỉ định các tệp TypeScript được bao gồm trong dự án.

- Khai báo các loại dữ liệu tùy chỉnh:
```
{
  "compilerOptions": {
    "typeRoots": ["./typings"],
    "types": ["node", "lodash"]
  }
}

```
Trong đó:

    - "typeRoots" chỉ định đường dẫn đến các thư mục chứa các tệp khai báo tùy chỉnh.
    - "types" chỉ định các loại khai báo được sử dụng trong dự án.

- Thiết lập cho dự án React:
```
{
  "compilerOptions": {
    "jsx": "react",
    "strict": true,
    "esModuleInterop": true
  },
  "include": ["src"]
}

```
Trong đó:

    - "jsx" xác định loại JSX được sử dụng.
    - "strict" bật chế độ kiểm tra cấu trúc dữ liệu tĩnh.
    - "esModuleInterop" bật tính năng tương thích với CommonJS và ES Modules.

Ngoài ra, có thể sử dụng tsconfig.json để thiết lập nhiều cài đặt khác nhau cho dự án, như quản lý phiên bản, quản lý cấu hình webpack, tối ưu hóa code, ...

Tài liệu chi tiết hơn có thể đọc [ở đây](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

# Code examples:
- Hello Word
```
function greet(name: string): string {
  return `Hello, ${name}!`;
}

console.log(greet("John"));

```
- Narrowing: Typescript Narrowing là quá trình rút gọn các kiểu dữ liệu trong Typescript, để có thể xác định kiểu dữ liệu chính xác hơn trong quá trình biên dịch.
```
function printId(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  } else {
    console.log(id);
  }
}

```
- Function
```
// Khai báo kiểu dữ liệu cho tham số và kết quả của function
function add(a: number, b: number): number {
  return a + b;
}

// Sử dụng Union Types cho tham số
function printId(id: number | string) {
  console.log(`ID is: ${id}`);
}

// Sử dụng Optional Parameters
function printName(firstname: string, lastname?: string) {
  if (lastname) {
    console.log(`Fullname is: ${firstname} ${lastname}`);
  } else {
    console.log(`Firstname is: ${firstname}`);
  }
}

// Sử dụng Default Parameters
function printGreeting(greeting: string = "Hello") {
  console.log(`${greeting}, world!`);
}

// Sử dụng Function Overloading
function reverse(string: string): string;
function reverse<T>(array: T[]): T[];
function reverse(stringOrArray: string | any[]) {
  if (typeof stringOrArray === "string") {
    return stringOrArray.split("").reverse().join("");
  } else {
    return stringOrArray.slice().reverse();
  }
}

```

- Object Types
```
type Person = {
  name: string;
  age: number;
  gender: string;
};

function printPerson(person: Person) {
  console.log(`Name: ${person.name}, Age: ${person.age}, Gender: ${person.gender}`);
}

const person1 = { name: 'John', age: 25, gender: 'Male' };
printPerson(person1); // Output: Name: John, Age: 25, Gender: Male

```
- Interface
```
interface IUser {
  id: number;
  name: string;
  email: string;
  age?: number; // optional property
  readonly createdAt: Date; // readonly property
}

function getUserInfo(user: IUser) {
  console.log(`User ${user.name} has email ${user.email}`);
}

const user: IUser = {
  id: 1,
  name: 'John Doe',
  email: 'john.doe@example.com',
  createdAt: new Date('2022-03-28'),
};

getUserInfo(user);

```
- Generics

Generics trong TypeScript là một cách để tạo ra các thành phần có thể tái sử dụng, nhưng cho phép một loại cụ thể được chỉ định sau đó khi được sử dụng. Tức là, generics cho phép chúng ta viết một loại hàm hoặc lớp mà có thể hoạt động với nhiều kiểu dữ liệu khác nhau, tùy thuộc vào cách chúng ta sử dụng nó. Với generics, chúng ta có thể tái sử dụng code một cách linh hoạt và an toàn hơn, vì nó giúp đảm bảo kiểu dữ liệu được sử dụng trong toàn bộ mã nguồn của chúng ta là như mong muốn.

Đây là một ví dụ về cách sử dụng generics trong TypeScript để tạo ra một hàm chung có thể xử lý các giá trị đầu vào khác nhau mà không cần chỉ định kiểu dữ liệu cụ thể:

```
function printArray<T>(arr: T[]): void {
  for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
  }
}

// Sử dụng hàm với một mảng số nguyên
const intArray: number[] = [1, 2, 3];
printArray(intArray);

// Sử dụng hàm với một mảng chuỗi
const stringArray: string[] = ["hello", "world"];
printArray(stringArray);

```

Trong ví dụ trên, T được sử dụng như một tham số kiểu generic. Khi gọi hàm printArray, ta chỉ cần truyền vào một mảng có kiểu dữ liệu bất kỳ là được. Hàm sẽ in ra tất cả các phần tử trong mảng, không phụ thuộc vào kiểu dữ liệu của chúng.

Đây là một ví dụ khác sử dụng Typescript generics để tạo ra một class chứa một mảng đối tượng bất kỳ loại nào:

```
class MyArray<T> {
  private array: T[];

  constructor() {
    this.array = [];
  }

  push(item: T) {
    this.array.push(item);
  }

  pop() {
    this.array.pop();
  }

  get length() {
    return this.array.length;
  }

  getItem(index: number): T {
    return this.array[index];
  }
}

// Sử dụng MyArray với number
const numberArray = new MyArray<number>();
numberArray.push(1);
numberArray.push(2);
console.log(numberArray.getItem(1)); // output: 2

// Sử dụng MyArray với string
const stringArray = new MyArray<string>();
stringArray.push('hello');
stringArray.push('world');
console.log(stringArray.getItem(0)); // output: 'hello'

```

Ở đây, chúng ta đã tạo ra một class MyArray có chứa một mảng đối tượng bất kỳ loại nào thông qua việc sử dụng generics. Class này cho phép thêm, xóa, truy xuất đối tượng trong mảng bằng cách sử dụng phương thức push(), pop(), getItem(). Chúng ta có thể sử dụng MyArray với bất kỳ kiểu dữ liệu nào chỉ cần khai báo kiểu dữ liệu đó khi tạo instance của MyArray.

Chi tiết hơn về các Type Manipulation các bạn có thể tìm đọc [ở đây](https://www.typescriptlang.org/docs/handbook/2/types-from-types.html)

- Class

Ví dụ về Class đơn giản

```
class Person {
  name: string;
  age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  sayHello() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const person = new Person("John", 30);
person.sayHello(); // Output: Hello, my name is John and I am 30 years old.

```

Ví dụ về Class implement interface

```
interface Animal {
  name: string;
  makeSound: () => void;
}

class Cat implements Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  makeSound() {
    console.log("Meow");
  }
}

const myCat = new Cat("Fluffy");
console.log(myCat.name); // Output: Fluffy
myCat.makeSound(); // Output: Meow

```

Trong ví dụ này, chúng ta định nghĩa một interface Animal với hai thuộc tính: name là một chuỗi và makeSound là một phương thức không có tham số và không trả về gì cả. Sau đó, chúng ta tạo một class Cat và implement interface Animal. Class này có một thuộc tính name và một phương thức makeSound để in ra chuỗi "Meow". Cuối cùng, chúng ta tạo một instance của class Cat và gọi phương thức makeSound.