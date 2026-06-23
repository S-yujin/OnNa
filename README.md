# OnNa 온나

> 어르신의 손재주와 청년의 배움을 연결하는 부울경 지역 기반 원데이 클래스 플랫폼

## 프로젝트 소개

**OnNa**는 부산·울산·경남 지역의 어르신이 가진 경험과 손기술을  
청년들에게 원데이 클래스로 공유할 수 있도록 연결하는 세대 상생형 서비스입니다.

어르신에게는 자신의 기술을 활용한 소득 창출과 지역사회 참여 기회를 제공하고,  
청년에게는 합리적인 가격으로 지역 기반의 실용적인 기술을 배울 수 있는 기회를 제공합니다.

## 주요 사용자

### 청년 수강생

- 지역과 카테고리를 기준으로 원데이 클래스 탐색
- 클래스 상세 정보 확인
- 클래스 예약
- 자신의 예약 목록 및 예약 상세 확인

### 어르신 강사

- 자신의 경험과 손기술을 활용한 클래스 운영
- 클래스 정보 등록
- 강사 전용 대시보드 확인
- 클래스별 신청자 및 예약 현황 관리

## 주요 기능

### 현재 구현된 기능

- 청년·어르신 역할을 구분한 회원가입 및 로그인
- 원데이 클래스 목록 조회
- 지역 및 카테고리별 클래스 필터링
- 클래스 상세 정보 조회
- 새로운 클래스 등록
- 클래스 예약 생성
- 사용자별 예약 목록 조회
- 예약 상세 정보 조회
- 클래스별 예약자 목록 조회
- 어르신 강사 목록 및 강사 대시보드 화면
- 프론트엔드와 백엔드 API 연동 상태 확인

### 향후 개발 예정

- JWT 기반 인증 및 역할별 접근 제어
- 예약 데이터의 완전한 DB 영속화
- 클래스 수정 및 삭제
- 예약 취소 및 상태 변경
- 수업 후기와 평점 기능
- 결제 기능
- 이미지 업로드 및 프로필 관리
- 관리자 페이지
- 운영 서버 배포 및 CI/CD 구성

## 기술 스택

### Frontend

| 구분 | 기술 |
|---|---|
| Language | TypeScript |
| Framework | React 18 |
| Build Tool | Vite |
| Styling | Tailwind CSS |
| UI | shadcn/ui, Radix UI |
| Routing | React Router |
| Server State | TanStack Query |
| HTTP Client | Axios, Fetch API |
| Form | React Hook Form, Zod |
| External Service | Supabase Client |

### Backend

| 구분 | 기술 |
|---|---|
| Language | Java 17 |
| Framework | Spring Boot 4 |
| Web | Spring Web MVC |
| Database Access | Spring Data JPA |
| Security | Spring Security |
| Database | MySQL |
| Build Tool | Gradle |
| Utility | Lombok |

## 시스템 구조

```text
┌──────────────────────────────┐
│          Web Browser         │
└──────────────┬───────────────┘
               │ HTTP / JSON
┌──────────────▼───────────────┐
│ Frontend                     │
│ React + TypeScript + Vite    │
│ localhost:5173               │
└──────────────┬───────────────┘
               │ REST API
┌──────────────▼───────────────┐
│ Backend                      │
│ Spring Boot + Spring Data JPA│
│ localhost:9090               │
└──────────────┬───────────────┘
               │ JPA
┌──────────────▼───────────────┐
│ MySQL Database               │
└──────────────────────────────┘
```

## 프로젝트 구조

```text
OnNa/
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── contexts/
│   │   ├── hooks/
│   │   ├── integrations/
│   │   ├── lib/
│   │   └── pages/
│   ├── package.json
│   └── vite.config.ts
│
├── backend/
│   ├── gradle/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/onna/onnaback/
│   │   │   │   ├── config/
│   │   │   │   ├── controller/
│   │   │   │   ├── domain/
│   │   │   │   ├── dto/
│   │   │   │   ├── repository/
│   │   │   │   └── service/
│   │   │   └── resources/
│   │   └── test/
│   ├── build.gradle
│   └── gradlew
│
├── README.md
└── LICENSE
```

## 실행 방법

### 1. 저장소 복제

```bash
git clone https://github.com/S-yujin/OnNa.git
cd OnNa
```

### 2. 환경 변수 설정

#### Frontend

`frontend/.env` 파일을 생성합니다.

```env
VITE_API_BASE_URL=http://localhost:9090
VITE_SUPABASE_URL=YOUR_SUPABASE_URL
VITE_SUPABASE_PUBLISHABLE_KEY=YOUR_SUPABASE_PUBLISHABLE_KEY
```

#### Backend

다음 환경 변수를 설정합니다.

```env
DB_URL=jdbc:mysql://localhost:3306/onna?serverTimezone=Asia/Seoul&characterEncoding=UTF-8
DB_USERNAME=YOUR_DB_USERNAME
DB_PASSWORD=YOUR_DB_PASSWORD
```

`application.properties`에서는 환경 변수를 사용합니다.

```properties
spring.datasource.url=${DB_URL}
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}
```

### 3. Backend 실행

Git Bash 또는 macOS/Linux:

```bash
cd backend
./gradlew bootRun
```

Windows CMD 또는 PowerShell:

```powershell
cd backend
.\gradlew.bat bootRun
```

Backend 기본 주소:

```text
http://localhost:9090
```

### 4. Frontend 실행

새 터미널에서 실행합니다.

```bash
cd frontend
npm install
npm run dev
```

Frontend 기본 주소:

```text
http://localhost:5173
```

## 주요 API

### 인증

| Method | Endpoint | 설명 |
|---|---|---|
| POST | `/api/auth/signup` | 회원가입 |
| POST | `/api/auth/login` | 로그인 |

### 클래스

| Method | Endpoint | 설명 |
|---|---|---|
| GET | `/api/classes` | 클래스 목록 조회 |
| GET | `/api/classes?region={지역}` | 지역별 클래스 조회 |
| GET | `/api/classes?category={카테고리}` | 카테고리별 클래스 조회 |
| GET | `/api/classes/{id}` | 클래스 상세 조회 |
| POST | `/api/classes` | 클래스 생성 |

### 예약

| Method | Endpoint | 설명 |
|---|---|---|
| POST | `/api/reservations` | 예약 생성 |
| GET | `/api/reservations/{id}` | 예약 상세 조회 |
| GET | `/api/reservations/my?userId={id}` | 사용자 예약 목록 조회 |
| GET | `/api/reservations/class?classId={id}` | 클래스별 예약 목록 조회 |

### 서버 확인

| Method | Endpoint | 설명 |
|---|---|---|
| GET | `/api/hello` | 프론트엔드·백엔드 연결 확인 |

## 화면 경로

| 경로 | 화면 |
|---|---|
| `/` | 메인 화면 |
| `/auth` | 로그인 및 회원가입 |
| `/classes` | 전체 클래스 |
| `/classes/:id` | 클래스 상세 |
| `/reservations` | 내 예약 목록 |
| `/reservations/:id` | 예약 상세 |
| `/teachers` | 어르신 강사 목록 |
| `/dashboard` | 강사 대시보드 |

## 개발 시 주의사항

- `.env`와 데이터베이스 비밀번호는 GitHub에 업로드하지 않습니다.
- 실제 환경 변수 대신 `.env.example` 파일만 공유합니다.
- 기능 개발은 별도의 브랜치에서 진행합니다.
- `main` 브랜치에 병합하기 전 빌드와 실행 여부를 확인합니다.
- API 형식이 변경되면 프론트엔드와 백엔드를 함께 수정합니다.

## 팀원

| 이름 | 역할 | 담당 기능 |
|---|---|---|
| 이름 입력 | Frontend | 담당 내용 입력 |
| 이름 입력 | Backend | 담당 내용 입력 |
| 이름 입력 | Design / Planning | 담당 내용 입력 |

## License

이 프로젝트는 [MIT License](LICENSE)를 따릅니다.
