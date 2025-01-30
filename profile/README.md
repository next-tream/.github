# 🎬 Nextream

## 실시간 스트리밍 방송 플랫폼
<img width="1000" alt="Nextream Screenshot" src="https://github.com/user-attachments/assets/8417e9d4-8fe2-4978-a62d-5b712a2f2db2" />

## ✨ 주요 기능
- **실시간 스트리밍**: 방송 생성 및 시청 기능 제공
- **채팅 시스템**: 방송 중 실시간 채팅 지원 (socket.io 사용)
- **소셜 로그인**: NextAuth를 이용한 간편 로그인 지원

## 🛠 기술 스택
![image](https://github.com/user-attachments/assets/b6598a82-abe1-4ec3-b406-8bffff81499c)
<img width="1000" alt="Nextream Screenshot" src="https://github.com/user-attachments/assets/96b55886-fdd7-4e2d-91c6-4fc6d469e6c9" />
## 🗒️ ERD 설계
<img width="1000" alt="Nextream Screenshot" src="https://github.com/user-attachments/assets/44fc51a8-0b2c-4f8f-b232-b5e280b09a26" />

## 📁 폴더 구조
### pages
각 페이지별 폴더를 생성하며, 해당 페이지에서만 사용하는 파일들을 포함합니다.

```
/app
  /Home
    /_components  # Home 페이지에서만 사용하는 컴포넌트
    /_types       # Home 페이지에서만 사용하는 타입 정의
    page.tsx      # Home 페이지의 page.tsx
    layout.tsx    # Home 페이지의 공통 layout
```

### common
프로젝트 전반에서 공통적으로 사용하는 파일들을 모아둡니다.

```
/common
  /actions     # Next Server 정의
  /components  # 공통 컴포넌트
  /configs     # 초기 환경 셋팅
  /constants   # 상수 정의
  /hooks       # 공통적으로 사용하는 커스텀 훅
  /layouts     # 공통 레이아웃
  /libs        # ShadCN 셋팅
  /schema      # Zod 스키마 정의
  /stores      # 전역 상태관리
  /types       # 공통 타입 정의
  /utils       # 유틸리티 함수
```

이러한 구조를 통해 페이지별로 독립적인 관리를 하면서도, 공통적으로 사용하는 요소들은 `common` 폴더에서 재사용할 수 있도록 구성하였습니다.

## 👥 팀원 정보
![Team Image](https://github.com/user-attachments/assets/f005bd1a-4a12-4770-8684-b6852d27bff3)

## 💻 AI 코드 리뷰 - 지승
![image](https://github.com/user-attachments/assets/d20d5e43-3cf4-4dce-8817-64526b1059eb)

[if kakao 2024 후기](https://velog.io/@rjs8833/Kakao-ifkakaoAI-2024-%EB%AA%A8%EB%93%A0-%EC%97%B0%EA%B2%B0%EC%9D%84-%EC%83%88%EB%A1%AD%EA%B2%8C-%ED%9B%84%EA%B8%B0) **kakao에서 사용하는 AI인 Code Buddy**에서 영감을 받아, 특정 브랜치에 PR이 생성될 때 OpenAI를 활용한 자동 코드 리뷰 시스템을 구축했습니다. GitHub Actions를 통해 diff된 코드만 추출하여 OpenAI에 전달하고, `팀의 네이밍 규칙, 파일 구조, 코드 가독성, TypeScript 규칙, useState 선언 위치` 등을 검토하도록 설정했습니다. 이를 통해 코드 규칙 위반 사항을 자동으로 피드백받을 수 있도록 하였으며, 팀원의 코드 리뷰 시간을 단축하여 개발에 집중할 수 있는 환경을 마련했습니다.

### 🥇 우수 팀 프로젝트 상
<img width="500" alt="award" src="https://github.com/user-attachments/assets/5157997c-7d8f-477c-b898-dd14da196f5c" />

## 🌟 트러블슈팅
### ❗️ 예슬이의 트러블슈팅 - NextAuth.js - Credentials Provider 에러 메시지 전달 이슈

#### 문제 개요
NextAuth.js의 Credentials Provider를 사용하여 로그인할 때, 서버에서 발생한 에러 메시지를 클라이언트에서 정상적으로 받을 수 없는 문제 발생

#### 발생 원인
NextAuth.js 내부적으로 `authorize` 함수의 반환값을 기반으로 세션을 생성하는데, `signIn('credentials', { ... })` 함수를 사용하여 로그인 시도 시, 오류 상황에서 단순히 `return`을 하면 NextAuth는 이를 정상적인 응답으로 해석할 수 없어 클라이언트에서 이를 직접 받지 못함

#### 해결 방법
서버에서 `CredentialsSignin` 에러 발생 시 `throw`를 사용하여 클라이언트에서 이를 감지할 수 있도록 처리

1. 잘못된 방식: `return` 사용: NextAuth.js는 이를 오류로 인식하지 않기 때문에 클라이언트에서 에러 처리가 어려움
```typescript
async authorize(credentials): Promise<any> {
  if (!credentials) return null;

  const { email, password } = credentials;

  try {
    // 생략
  } catch (error: any) {
    // ❌ 클라이언트에서 에러를 감지할 수 없음
    return error;
  }
}
```

2. 올바른 방식: `throw` 사용: 클라이언트에서 `signIn` 함수를 사용할 때 `catch`로 에러 캐치
```typescript
async authorize(credentials): Promise<any> {
  if (!credentials) return null;

  const { email, password } = credentials;

  try {
    // 생략
  } catch (error: any) {
    // ✅ throw를 사용해야 클라이언트에서 catch 가능
    throw new Error(error.response.data.message);
  }
}
```

3. 클라이언트에서 처리 (`signIn` 함수 사용)
```typescript
import { signIn } from 'next-auth/react';

async function signinFuc() {
  const result = await signIn('credentials', {
    redirect: false,
    email,
    password,
  });

  if (result?.error) {
    // 🔹 에러 메시지를 사용자에게 보여주기 위한 처리
    toast({ title: `${result?.error}... 😱`, duration: 2000 });
  } else {
    toast({ title: '로그인 성공!! 🎊', duration: 1000 });
  }
}
```

#### 정리
- **잘못된 방법**: `return error` → ❌ 클라이언트에서 에러를 정상적으로 받을 수 없음
- **올바른 방법**: `throw new Error(error.response.data.message)` → ✅ 클라이언트에서 catch로 에러를 받을 수 있음
- **클라이언트 처리**: `signIn`의 결과에서 `error`를 확인하여 사용자에게 적절한 피드백 제공
