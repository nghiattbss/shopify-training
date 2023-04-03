# NextJS Typescript structure
Các bạn có thể đọc chi tiết hơn [tại đây](https://nextjs.org/docs/basic-features/typescript)

Dưới đây là một ví dụ về coding structure.

```
├── components/
│   ├── Header.tsx
│   ├── Footer.tsx
│   └── ...
│
├── pages/
│   ├── index.tsx
│   ├── about.tsx
│   └── ...
│
├── public/
│   ├── images/
│   ├── styles/
│   └── ...
│
├── services/
│   ├── api.ts
│   └── ...
│
├── types/
│   ├── common.d.ts
│   ├── index.d.ts
│   └── ...
│
├── utils/
│   ├── helpers.ts
│   ├── constants.ts
│   └── ...
│
├── .eslintrc.json
├── jest.config.js
├── next-env.d.ts
├── next.config.js
├── package.json
├── tsconfig.json
└── yarn.lock

```

# Một NextJS page sử dụng typescript

```
import { NextPage } from 'next';
import Head from 'next/head';
import Link from 'next/link';

interface Props {
  title: string;
  description: string;
}

const Home: NextPage<Props> = ({ title, description }) => {
  return (
    <>
      <Head>
        <title>{title}</title>
        <meta name="description" content={description} />
      </Head>
      <h1>Welcome to my Next.js site!</h1>
      <p>Here are some resources to get you started:</p>
      <ul>
        <li>
          <Link href="/blog">
            <a>Blog</a>
          </Link>
        </li>
        <li>
          <Link href="/about">
            <a>About</a>
          </Link>
        </li>
      </ul>
    </>
  );
};

Home.getInitialProps = async () => {
  return {
    title: 'Next.js with TypeScript',
    description: 'A starter template for Next.js using TypeScript.',
  };
};

export default Home;

```

Chú ý trong các phiên bản mới của NextJs, getInitialProps có thể được thay thế bằng getServerSideProps.

```
export async function getServerSideProps(context) {
  return {
    props: {}, // will be passed to the page component as props
  }
}
```

