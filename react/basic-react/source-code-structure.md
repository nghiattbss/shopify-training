# Source code structure

Các React App không có một chuẩn chung cho source code. Nó phụ thuộc vào rất nhiều yếu tố như:
- Kích cỡ dự án
- Mục đích dự án
- Kiến trúc dự án
- Tech Stack
- ...etc
# Một số structure phổ biến
## Cấu trúc thông thường
```
my-react-app/
├── node_modules/
├── public/
│   ├── index.html
│   ├── favicon.ico
│   └── manifest.json
├── src/
│   ├── components/
│   │   ├── Header.js
│   │   ├── Footer.js
│   │   └── ...
│   ├── pages/
│   │   ├── Home.js
│   │   ├── About.js
│   │   └── ...
│   ├── services/
│   │   ├── api.js
│   │   └── ...
│   ├── utils/
│   │   ├── helpers.js
│   │   └── ...
│   ├── App.js
│   ├── index.js
│   └── styles.css
├── package.json
├── package-lock.json
└── README.md

```
## Cấu trúc nếu có custom hooks và database.
```
src/
|-- components/
|   |-- Header/
|   |   |-- Header.jsx
|   |   |-- Header.module.css
|   |-- Footer/
|   |   |-- Footer.jsx
|   |   |-- Footer.module.css
|   |-- ...
|-- containers/
|   |-- Home/
|   |   |-- Home.jsx
|   |   |-- Home.module.css
|   |-- About/
|   |   |-- About.jsx
|   |   |-- About.module.css
|   |-- ...
|-- hooks/
|   |-- useAuth.js
|   |-- useModal.js
|   |-- ...
|-- services/
|   |-- api.js
|   |-- database.js
|   |-- ...
|-- utils/
|   |-- helpers.js
|   |-- constants.js
|   |-- ...
|-- App.js
|-- index.js
|-- index.css
|-- setupTests.js
|-- ...

```

## Cấu trúc nếu sử dụng Redux hoặc useContext.
```
├── public/
└── src/
    ├── actions/
    ├── components/
    ├── constants/
    ├── reducers/
    ├── store/
    ├── types/
    ├── utils/
    ├── App.tsx
    ├── index.tsx
    └── rootReducer.ts

```
## Cấu trúc kết hợp NextJS, TypeScript, và Redux
```
├── components
│   ├── Layout
│   │   ├── Footer.tsx
│   │   ├── Header.tsx
│   │   └── index.ts
│   ├── common
│   │   ├── Button.tsx
│   │   └── index.ts
│   ├── pages
│   │   ├── Home
│   │   │   ├── Home.tsx
│   │   │   ├── components
│   │   │   │   ├── FeaturedPost.tsx
│   │   │   │   ├── LatestPosts.tsx
│   │   │   │   ├── PostList.tsx
│   │   │   │   └── index.ts
│   │   │   └── index.ts
│   │   └── About
│   │       ├── About.tsx
│   │       ├── components
│   │       │   ├── EmployeeList.tsx
│   │       │   └── index.ts
│   │       └── index.ts
│   └── index.ts
├── constants
│   ├── API.ts
│   └── index.ts
├── lib
│   ├── api.ts
│   ├── auth.ts
│   └── index.ts
├── pages
│   ├── _app.tsx
│   ├── _document.tsx
│   ├── index.tsx
│   └── about.tsx
├── store
│   ├── actions
│   │   ├── auth.ts
│   │   └── index.ts
│   ├── reducers
│   │   ├── auth.ts
│   │   └── index.ts
│   ├── index.ts
│   └── types.ts
├── styles
│   ├── global.css
│   └── index.ts
├── utils
│   ├── helpers.ts
│   └── index.ts
├── .eslintrc.js
├── .prettierrc.js
├── next.config.js
├── package.json
└── tsconfig.json

```

