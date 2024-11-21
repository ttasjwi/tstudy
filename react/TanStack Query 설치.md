# TanStack Query 설치
[공식 홈페이지](https://tanstack.com/query/latest)

---

#### 개요

- 강력한 비동기 상태 관리 라이브러리
- TypeScript, JavaScript, React, Svelt, Vue, ... 모두 사용 가능
- 주요 기능
  - fetching : 데이터 가져오기
  - caching: 데이터 캐싱

---

#### 의존성 추가
```bash
# npm
npm install @tanstack/react-query
# yarn
yarn add @tanstack/react-query
```

---

#### 설정
```jsx
import {QueryClient, QueryClientProvider} from "@tanstack/react-query";

const client = new QueryClient();

const App = () => (
    <QueryClientProvider client={client}>
        <AuthContextProvider>
            {...}
        </AuthContextProvider>
    </QueryClientProvider>
);
```
프로젝트에서 Tanstack Query 를 사용할 영역을 QueryClientProvider 로 래핑해야만,  
해당 영역 내에서 TanStack Query를 사용할 수 있다.

```tsx
'use client';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import React from "react";

const queryClient = new QueryClient();

export const QueryClientProviderWrapper = ({ children }: { children: React.ReactNode }) => {
    return (
        <QueryClientProvider client={queryClient}>
            {children}
        </QueryClientProvider>
    );
};
```
```tsx
const RootLayout = ({children}: Readonly<Props>) => {

    return (
        <html lang="ko" className={sans.className}>
        <body>
        <QueryClientProviderWrapper>
            <Header/>
            <main>
                {children}
            </main>
        </QueryClientProviderWrapper>
        </body>
        </html>
    );
}
```
그런데 Next.js 에서는 클라이언트 컴포넌트/서버 컴포넌트 구분이 강제되는데  
이럴 경우 클라이언트 컴포넌트로 별도로 분리하고, 래핑해주면 된다.

---
