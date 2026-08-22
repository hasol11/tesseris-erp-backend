# ⚙️ TESSERIS ERP-PMS — Main Backend

> **Team Project · Personal Fork**

TESSERIS는 소상공인의 결제·정산과 기업 운영 정보를 통합 관리하는 ERP/PMS 서비스입니다.

저는 Main Backend, Alert Backend, User Frontend, Admin Frontend 전반의 개발에 참여했으며,  
특히 **알림 도메인을 포함해 Backend API와 사용자·관리자 화면을 연결하는 End-to-End 개발 경험**을 쌓았습니다.

---

## 🙋‍♀️ My Contribution

### 💰 중개 수수료율 관리

- 비즈니스 등급별 중개 수수료율 조회 및 일괄 수정 API 구현
- 민감한 설정을 변경하기 전 관리자 비밀번호를 다시 확인하는 검증 로직 적용

### 📋 운영 로그 및 이력

- 관리자 CMS 접속 기록 조회 API 구현
- IP, 시간, 접속 유형 등의 조건 기반 검색 기능 구현
- 사용자 계정 정보 변경 이력 조회 및 검색 기능 구현

### 📢 공지사항

- 관리자 공지사항 등록 / 수정 / 삭제 API 구현
- 권한에 따른 접근 제어 적용

### 👤 My Page / PIN

- JWT 인증 정보를 기반으로 사용자 마이페이지 데이터 조회
- 사용자 정보 및 추천인 관련 API 구현
- 현재 비밀번호 확인을 포함한 PIN 변경 기능 구현

---

## 🔔 Notification Domain

TESSERIS에서는 알림 기능을 하나의 화면에 한정하지 않고  
Main Backend, Alert Backend, User/Admin Frontend가 연결되는 흐름으로 개발했습니다.

알림 요구사항과 초기 데이터 구조를 팀원들과 정리하면서  
역할뿐 아니라 **사용자가 실제로 해당 알림을 수신하도록 설정했는지까지 확인한 뒤 최종 수신 대상을 결정**하는 방향으로 설계했습니다.

```text
Event 발생
    ↓
역할 기반 대상 조회
    ↓
사용자 알림 설정 확인
    ↓
최종 Receiver 결정
    ↓
알림 저장 / 전달
```

알림을 받지 않을 사용자까지 먼저 알림 데이터를 생성하기보다  
**실제 수신 대상을 먼저 확정한 뒤 필요한 알림만 생성하는 것**을 기준으로 했습니다.

알림 조회와 읽음 처리 자체는 별도의 Alert Backend에서 구현했습니다.

---

## 🛠 Tech Stack

- Java
- Spring Boot
- Spring Data JPA
- MariaDB / MySQL
- JWT
- Gradle

---

## 🔗 TESSERIS Repositories

- `hasol11/tesseris-erp-backend` — Main Backend
- `hasol11/tesseris-erp-alert` — Alert Backend
- `hasol11/tesseris-erp-user` — User Frontend
- `hasol11/tesseris-erp-admin` — Admin Frontend

---

## 👥 Team Project

본 프로젝트는 팀 프로젝트로 진행되었습니다.

본 README에서는 프로젝트 전체 기능을 제가 구현한 것처럼 표현하지 않고,  
**제가 직접 개발하거나 주요하게 참여한 영역을 중심으로 정리했습니다.**
