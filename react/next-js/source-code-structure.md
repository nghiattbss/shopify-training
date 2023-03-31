# NextJS là gì

NextJS là một framework React được sử dụng để xây dựng các ứng dụng web phức tạp. Nó kết hợp giữa React và Node.js để cung cấp cho người dùng các tính năng như:
- SSR (Server Side Rendering)
- SSG (Static Site Generation)
- Pre-fetching và phân tách dữ liệu. 

NextJS cũng hỗ trợ các tính năng như dynamic routing, code splitting, hot module replacement, và nhiều tính năng khác giúp cho quá trình phát triển ứng dụng React trở nên dễ dàng hơn.

# Các Phiên bản của NextJS
Các phiên bản của NextJS tính từ năm 2020
- Next.js 9: được phát hành vào năm 2020, bổ sung nhiều tính năng mới, trong đó nổi bật là cải thiện khả năng tương thích với các ứng dụng React Native và hỗ trợ Webpack 5.

- Next.js 10: được phát hành vào tháng 11 năm 2020, bổ sung nhiều cải tiến liên quan đến khả năng tối ưu hóa và hiệu suất, bao gồm cải thiện tốc độ tải trang và khả năng tối ưu hóa hình ảnh.

- Next.js 11: được phát hành vào tháng 6 năm 2021, bổ sung nhiều tính năng mới như hỗ trợ Vercel Analytics, tối ưu hóa dữ liệu động, hỗ trợ i18n và cải thiện khả năng tương thích với các trình duyệt.

- Next.js 12: được phát hành vào tháng 11 năm 2021, bổ sung nhiều cải tiến liên quan đến tối ưu hóa và hiệu suất, bao gồm cải thiện khả năng tải trang và tốc độ phản hồi, khả năng tối ưu hóa hình ảnh và hỗ trợ các cấu hình khác nhau của Webpack 5.
- Next.js 13: là phiên bản mới nhất được phát hành vào năm 2022 bao gồm các thay đổi sau: layouts, React Server Components, streaming in the app directory, Turbopack, và cải thiện các vấn đề liên quan tới load image

# Structure Examples
### Cấu trúc cơ bản

```
├── components
│   ├── Layout.js
│   └── Navbar.js
├── pages
│   ├── index.js
│   ├── about.js
│   └── contact.js
├── public
│   ├── images
│   │   ├── logo.png
│   │   └── background.jpg
│   └── styles
│       └── main.css
├── server
│   ├── api.js
│   └── middleware.js
├── utils
│   ├── auth.js
│   └── helpers.js
├── .eslintrc.js
├── .gitignore
├── next.config.js
├── package.json
└── README.md

```
### Kết hợp với TypeScript

```
├── components
│   ├── Layout
│   │   ├── index.tsx
│   │   └── styles.module.css
│   ├── Header
│   │   ├── index.tsx
│   │   └── styles.module.css
│   └── ...
├── pages
│   ├── index.tsx
│   ├── about.tsx
│   ├── blog
│   │   ├── [slug].tsx
│   │   ├── index.tsx
│   │   └── ...
│   └── ...
├── public
│   ├── images
│   ├── favicon.ico
│   └── ...
├── styles
│   ├── globals.css
│   ├── index.module.css
│   └── ...
├── utils
│   ├── api.ts
│   ├── constants.ts
│   ├── helpers.ts
│   └── ...
├── .next
├── node_modules
├── package.json
├── tsconfig.json
└── ...

```

Để generate boilerplate có thể dùng lệnh sau: 
- ```npx create-next-app@latest```
- ```npx create-next-app@latest --typescript```

Ngoài các template về structure bên trên, NextJS project có thể chứa một số folder khác như pages/api, app... Tùy theo từng yêu cầu chức năng.


