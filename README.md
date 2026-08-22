# ⚙️ TESSERIS ERP/PMS — Main Backend

> **Team Project · Personal Fork**

TESSERIS는 소상공인과 서비스 운영자가 결제·정산 및 운영 정보를 관리할 수 있도록 구성한 ERP/PMS 팀 프로젝트입니다.

저는 Main Backend를 중심으로 운영 관련 API를 구현했으며,  
알림 기능에서는 **요구사항과 데이터 구조 정리부터 Alert Backend, User/Admin Frontend 연결까지 End-to-End 개발 과정에 참여했습니다.**

> 본 Repository는 팀 프로젝트의 개인 Fork이며,  
> 아래 `My Contribution`은 제가 직접 구현하거나 주요하게 참여한 영역을 기준으로 작성했습니다.

---

## 📌 Project

TESSERIS는 기능에 따라 Main Backend, Alert Backend와 User/Admin Frontend가 나뉘어 개발되었습니다.

저는 하나의 Repository에 한정되지 않고 다음 영역을 연결하며 개발했습니다.

<pre>
Main Backend
    │
    ├─ 운영 / 정책 관련 API
    │
    └─ Notification Flow
             │
             ▼
       Alert Backend
             │
        ┌────┴────┐
        ▼         ▼
      User      Admin
    Frontend   Frontend
</pre>

특히 알림 기능을 통해 **하나의 요구사항이 데이터 구조 → Backend → 사용자 화면으로 연결되는 전체 흐름**을 경험했습니다.

---

## 🙋‍♀️ My Contribution

### 💰 중개 수수료율 관리

- 비즈니스 등급별 중개 수수료율 조회 API
- 수수료율 일괄 수정 기능
- 민감한 정책 변경 전 관리자 비밀번호 재확인 로직

단순 설정 변경이 아니라 실제 서비스 운영 정책과 연결되는 값인 만큼,  
변경 전 관리자 확인 절차를 함께 적용했습니다.

---

### 📋 CMS 운영 이력

- 관리자 CMS 접속 기록 조회
- 접속 IP / 시간 / 유형 기반 검색
- 사용자 계정 정보 변경 이력 조회
- 변경 이력 검색 기능

운영자가 서비스 내 주요 변경과 접근 기록을 추적할 수 있도록 관련 조회 API를 구현했습니다.

---

### 📢 공지사항

- 관리자 공지 등록
- 공지 수정
- 공지 삭제
- 관련 권한 검증

Admin Frontend와 연결해 실제 운영자가 사용할 수 있는 공지 관리 흐름을 구성했습니다.

---

### 👤 My Page / PIN

- JWT 인증 사용자 기준 마이페이지 정보 조회
- 사용자 정보 관련 API
- 추천인 관련 정보 연동
- 현재 비밀번호 확인을 포함한 PIN 변경 기능

---

## 🔔 Notification Domain

TESSERIS에서 알림 기능은 Main Backend 하나에서 끝나는 기능이 아니었습니다.

초기 요구사항과 데이터 구조를 팀원들과 정리하면서,  
알림 발생 이후 **누가 실제 수신 대상인지 결정하는 과정**을 함께 설계했습니다.

<pre>
Event 발생
    ↓
역할 기반 후보 사용자 조회
    ↓
사용자별 알림 설정 확인
    ↓
최종 Receiver 결정
    ↓
알림 생성 / 전달
</pre>

### 수신 대상을 먼저 확정한 이유

역할 조건에 해당하는 모든 사용자에 대해 알림 데이터를 먼저 생성한 뒤  
수신 설정을 확인하는 것보다,

**사용자의 알림 수신 설정을 먼저 확인하고 실제 수신 대상에게만 알림을 생성하는 방식**이 더 적절하다고 판단했습니다.

이를 통해 알림을 받지 않는 사용자의 불필요한 알림 데이터가 생성되지 않도록 했습니다.

> 이 판단은 별도의 성능 측정 결과가 아니라,  
> 불필요한 데이터 생성을 줄이기 위한 설계 기준으로 적용했습니다.

---

## 🔗 End-to-End Notification Flow

알림 기능은 여러 Repository에 걸쳐 연결됩니다.

<pre>
Main Backend
알림 발생 / 대상 결정
        ↓
Alert Backend
알림 저장 / 조회 / 읽음
        ↓
User Frontend
알림 목록 / Unread 상태
        ↓
Admin Frontend
관리자 알림 설정 / 조회
</pre>

이 과정에서 Backend API만 구현하는 것이 아니라  
실제 Frontend에서 어떤 상태로 소비되는지까지 함께 확인하며 개발했습니다.

---

## 🛠 Tech Stack

- Java
- Spring Boot
- Spring Data JPA
- Spring Security
- MariaDB / MySQL
- JWT
- Gradle

---

## 🔗 TESSERIS Repositories

| Repository | 역할 |
| --- | --- |
| [Main Backend](https://github.com/hasol11/tesseris-erp-backend) | ERP/PMS Main Backend |
| [Alert Backend](https://github.com/hasol11/tesseris-erp-alert) | Notification Backend |
| [User Frontend](https://github.com/hasol11/tesseris-erp-user) | User Web Service |
| [Admin Frontend](https://github.com/hasol11/tesseris-erp-admin) | Admin Web Service |

### Original Team Repositories

- [Original Main Backend](https://github.com/7GUYZ/ERP-Tesseris-springboot)
- [Original Alert Backend](https://github.com/7GUYZ/ERP-Tesseris-Alert-Backend)
- [Original User Frontend](https://github.com/7GUYZ/ERP-Tesseris-react)
- [Original Admin Frontend](https://github.com/7GUYZ/ERP-Tesseris-react-admin)

---

## 👥 Team Project

본 프로젝트는 팀 프로젝트로 진행되었습니다.

프로젝트 전체 시스템이나 인프라를 제가 단독으로 설계한 것이 아니며,  
본 README에서는 **제가 직접 구현하거나 주요하게 참여한 영역을 중심으로 정리했습니다.**
