# AGENTS.md - 프랭클린 타임박싱 플래너 AI Agent 지침서

이 문서는 **프랭클린 타임박싱 플래너 (Franklin Timeboxing Planner)** 개발 프로젝트에 참여하는 모든 AI Agent의 역할, 아키텍처 원칙, 행동 기준을 정의합니다.

---

## 📌 1. 프로젝트 개요 및 핵심 아키텍처

* **프로젝트명**: 프랭클린 타임박싱 플래너 (Franklin Timeboxing Planner)
* **목표**: 개인 사용자의 일일 할 일, 타임박싱, 목표 및 사명을 관리하는 서포트형 로컬 영구 보존 플래너
* **핵심 철학**:
  1. **개인정보 보호 최우선 (Privacy-First)**: 사용자 플래너 데이터는 클라이언트(브라우저) 측에서 Web Crypto API(AES-GCM)로 강력하게 암호화되어 로컬(IndexedDB)에만 저장됩니다.
  2. **무서버 / 서버 유지비 Zero (Zero Server Cost)**: 중앙 서버 DB 없이 클라이언트 로컬 저장소 및 유저 개인 클라우드 연동을 지향합니다.
  3. **3단계 라이선스 체계 (Free / Essential / Unlimited)**: 린(Lean)한 비즈니스 모델을 적용하여 백업 및 통계 기능에 제한을 두고 라이선스로 기능을 해금합니다.

---

## 🛠️ 2. 기술 스택 (Technology Stack)

* **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
* **Local Storage & Security**:
  * **Web Crypto API**: 사용자 PIN 기반 AES-GCM 마스터 키 생성 및 암호화/복호화
  * **IndexedDB**: 일일 작성 데이터 영구 보존
* **Backend / Cloud Services**:
  * **Firebase Firestore**: Essential 라이선스 키 검증 및 기기 귀속(UUID) 방지
  * **Firebase Hosting**: 정적 웹 앱 배포
* **Build / Deploy**: 별도의 거대한 번들러 없이 경량 단일 HTML/Asset 중심 구조 (`public/index.html`)

---

## 🤖 3. AI Agent 행동 지침 (Behavioral Rules)

1. **데이터 보안 준수**:
   * 사용자의 플래너 데이터나 개인 식별 정보(PII)를 평문(Plaintext) 상태로 외부 서버로 전송하거나 로그로 출력하는 코드를 절대 작성하지 마십시오.
2. **코드 및 기능 수정 전 영향도 검토**:
   * `public/index.html` 수정 시 로컬 암호화/복호화 파이프라인(PIN 인증 -> IndexedDB 읽기/쓰기 -> 백업/복원)이 손상되지 않도록 주의하십시오.
3. **검증 없는 작업 완료 금지**:
   * 코드 작성 후에는 반드시 데이터 저장/복원, 통계 차트, 요금제 제한(Paywall) 로직이 정상 작동하는지 수동/자동 검증 절차를 이행하고 보고하십시오.
4. **개발 이력 관리 지침**:
   * 중요한 기능 추가나 구조 변경 시 작업 완료 후 `history/` 폴더 내에 날짜별 기록 문서(`YYYY-MM-DD.md`)를 작성하고 `history/INDEX.md`를 업데이트하십시오.
5. **Git 명령어 자동 실행 규칙 (필수)**:
   * `git status`, `git pull`, `git add`, `git commit`, `git push` 등 모든 Git 관련 명령어는 **사용자 승인 확인 절차 없이 즉시 자동 수행**합니다.
   * 작업 단위가 완료될 때마다 의미 있는 커밋 메시지와 함께 GitHub 원격 저장소(`origin/main`)에 즉시 자동 푸시합니다.

