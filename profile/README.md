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

## 📜 컨트리뷰션 가이드
### 1. Git 브랜치 전략
- **main**: 원격 저장소의 주요 브랜치로, 최종 배포가 진행되는 브랜치입니다.
- **dev**: 개발 브랜치로, 기능이 완성되면 개인 브랜치에서 PR을 통해 병합됩니다.
- **feature/기능명**: 기능 개발을 위한 개인 브랜치로, dev 브랜치에서 분기하여 작업합니다.

#### 브랜치 생성 및 관리 흐름
1. `dev` 브랜치를 로컬로 가져옵니다: `git pull origin dev`
2. 새로운 기능 브랜치를 생성합니다: `git checkout -b feature/새기능 dev`
3. 작업 후 `dev` 브랜치로 PR을 보냅니다.
4. 충돌을 해결한 후 `dev` 브랜치에 병합합니다.
5. `main` 브랜치로 최종 병합 후 배포합니다.

### 2. Git 커밋 메시지 규칙
#### 커밋 메시지 형식
```
<타입>: <간단한 설명>

- <변경 사항 상세>
```
#### 커밋 타입
- `feat`: 새로운 기능 추가
- `fix`: 버그 수정
- `docs`: 문서 변경
- `style`: 코드 스타일 변경 (기능에 영향 없음)
- `refactor`: 코드 리팩토링
- `test`: 테스트 코드 추가 또는 변경
- `chore`: 기타 수정 (빌드 스크립트, 패키지 변경 등)

예시:
```
feat: 로그인 기능 추가

- 사용자 이메일, 비밀번호 입력
- 로그인 API 호출 후 토큰 저장
```

### 3. Pull Request (PR) 규칙
- **PR 제목**: 변경 사항을 간략히 설명 (예: `feat: 로그인 기능 추가`)
- **PR 설명**: 변경 사항 요약 및 추가 설명
- **리뷰어 지정**: 팀원이 PR을 검토할 수 있도록 리뷰어를 지정합니다.
- **충돌 해결**: PR 병합 전 충돌을 해결해야 합니다.
- **테스트**: PR을 올리기 전에 로컬 테스트를 완료해야 합니다.

### 4. Git 충돌 해결 규칙
1. 충돌 발생 시 `git status`로 충돌 파일을 확인합니다.
2. 충돌을 해결하고 해당 파일을 `git add` 합니다.
3. `git commit` 후 PR을 업데이트합니다.

<img width="100" alt="award" src="https://github.com/user-attachments/assets/5157997c-7d8f-477c-b898-dd14da196f5c" />
