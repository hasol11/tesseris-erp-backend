# ⚙️ TESSERIS ERP-PMS 서버 (Main Server)

> TESSERIS 프로젝트의 핵심 백엔드 서버입니다. 소상공인의 결제 시스템 도입 장벽을 낮추고, 통합 결제 관리(PMS)와 전사적 자원 관리(ERP) 기능을 제공하여 비즈니스 효율성을 극대화하는 것을 목표로 합니다.

### 🏛️ TESSERIS 전체 프로젝트 구조
- **[Main Server (ERP-PMS)](https://github.com/hasol11/tesseris-erp-backend) (👈 현재 레포지토리)**
- [Alert Server](https://github.com/hasol11/tesseris-erp-alert)
- [User Frontend](https://github.com/hasol11/tesseris-erp-user)
- [Admin Frontend](https://github.com/hasol11/tesseris-erp-admin)

<br>

## ✨ 주요 기능
- **ERP (전사적 자원 관리)**: 회원, 인사, 급여 등 기업의 핵심 자원을 통합 관리합니다.
- **PMS (결제 관리 시스템)**: 외부 PG사와 연동하여 결제, 정산, 가맹점 관리 등 복잡한 결제 관련 업무를 처리합니다.
- **API Gateway**: MSA 환경에서 모든 클라이언트의 요청을 받아 적절한 내부 서비스로 라우팅하는 관문 역할을 수행합니다.

<br>

## 🙋‍♀️ My Contribution
이 프로젝트에서 다음과 같은 핵심 백엔드 API 및 비즈니스 로직을 설계하고 개발했습니다.

- **중개 수수료율 설정 관리 (`/api/commission-setting`)**
  - 비즈니스 등급별 수수료율을 설정하고 일괄 수정하는 기능을 구현했습니다.
  - 민감한 정보 변경 시, 관리자 비밀번호를 한 번 더 확인하는 보안 검증 로직을 추가했습니다.

- **로그 관리 시스템**
  - **CMS 접속 기록 로그 (`/api/cms-access-log`)**: 관리자별 CMS 접속 기록을 IP, 시간, 타입별로 필터링하여 조회하는 기능을 개발했습니다.
  - **계정 수정 이력 관리 (`/api/update-log`)**: 사용자 계정 정보의 변경 이력을 추적하고, 수정자, 변경 데이터 등 다양한 조건으로 검색하는 기능을 구현했습니다.

- **콘텐츠 및 사용자 관리**
  - **공지사항 관리 시스템 (`/api/notice`)**: 권한 기반 접근 제어를 포함한 공지사항 CRUD API를 개발했습니다.
  - **마이페이지 기능 (`/api/general/mypage`)**: JWT 기반 인증을 통해 사용자 닉네임, 추천인 목록 등 개인화된 정보를 관리하는 API를 구현했습니다.
  - **PIN 번호 변경 시스템 (`/api/pinChange`)**: 보안 강화를 위해 비밀번호 확인 절차를 포함한 PIN 번호 변경 API를 개발했습니다.

<br>

## 🛠️ 기술 스택
- **Language**: `Java`
- **Framework**: `Spring Boot`, `Spring Data JPA`
- **Database**: `MariaDB/MySQL`
- **Authentication**: `JWT`

<br>

## 🚀 실행 방법 (Getting Started)

### 사전 요구사항
- Java: JDK 17 이상
- Gradle: 7.0 이상 (프로젝트에 포함된 Gradle Wrapper 사용 권장)
- 데이터베이스: MariaDB/MySQL 8.0 이상

### 1. 프로젝트 클론
```bash
git clone [https://github.com/your-username/ERP-Tesseris-springboot.git](https://github.com/your-username/ERP-Tesseris-springboot.git)
cd ERP-Tesseris-springboot
```

### 2. 의존성 패키지 설치 및 빌드
```bash
# Linux/Mac
./gradlew build

# Windows
gradlew.bat build
```

### 3. 로컬 개발 서버 실행
```bash
# Linux/Mac
./gradlew bootRun

# Windows
gradlew.bat bootRun
```

### 4. 환경 변수 설정
`src/main/resources/application.yml` 파일에 아래와 같은 형식으로 환경 변수를 설정해야 합니다.
```yaml
spring:
  datasource:
    url: jdbc:mariadb://{DB_HOST}:{DB_PORT}/{DB_NAME}
    username: {DB_USERNAME}
    password: {DB_PASSWORD}

jwt:
  secret: {JWT_SECRET}
  expiration: {JWT_EXPIRATION}

jasypt:
  encryptor:
    password: {JASYPT_ENCRYPTOR_PASSWORD}
```

<br>

## 📂 폴더 구조 (Directory Structure)
```
ERP-Tesseris-springboot/
└── src/
    └── main/
        ├── java/
        │   └── com/jakdang/labs/
        │       ├── api/              # API 컨트롤러 및 서비스
        │       ├── config/           # 설정 클래스
        │       ├── entity/           # JPA 엔티티
        │       ├── global/           # 전역 설정
        │       └── security/         # 보안 설정
        └── resources/
            ├── application.yml   # 애플리케이션 설정
            └── sql/              # SQL 스크립트
