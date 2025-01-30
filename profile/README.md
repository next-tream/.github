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

### 우수 팀 프로젝트 상
<img width="500" alt="award" src="https://github.com/user-attachments/assets/5157997c-7d8f-477c-b898-dd14da196f5c" />
