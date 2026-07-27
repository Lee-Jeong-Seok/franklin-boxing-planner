# ⌛ 프랭클린 타임박싱 플래너 (Franklin Timeboxing Planner)

> 개인 사용자의 일일 할 일(Task), 타임박싱(Timebox), 목표 및 통계를 관리하는 서포트형 로컬 영구 보존 웹 플래너입니다.

---

## ✨ 주요 특징 (Features)

* 🔒 **개인정보 보호 최우선 (Privacy-First)**: 사용자의 플래너 데이터는 클라이언트(브라우저) 측에서 **Web Crypto API(AES-GCM)**로 강력하게 암호화되어 로컬(IndexedDB)에만 저장됩니다.
* 💾 **영구 데이터 보존 & 암호화 백업**: 브라우저 내 데이터 저장과 함께 PIN 기반 암호화된 JSON 백업/복원 기능을 제공합니다.
* 📊 **로컬 데이터 통계 대시보드**: 업무 완료율 및 타임박스 실행 현황을 차트로 시각화하며, 외부 서버 전송 없이 100% 로컬에서 가공됩니다.
* ⚡ **Zero Server Cost**: 별도의 서버 유지비 없이 정적 웹 호스팅(Firebase Hosting)과 클라이언트 측 컴퓨팅으로 동작합니다.
* 💳 **3단계 린(Lean) 비즈니스 체계**: Free, Essential(1회 결제), Unlimited(구독) 요금제별 백업 및 통계 해금 지원.

---

## 🛠️ 기술 스택 (Tech Stack)

* **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
* **Security & Storage**: Web Crypto API (AES-GCM), IndexedDB
* **Cloud & Hosting**: Firebase Hosting, Firebase Firestore (Essential 라이선스 검증 및 기기 귀속)

---

## 📁 프로젝트 구조 (Project Structure)

```
franklin_boxing_planner/
├── public/
│   └── index.html        # 정적 배포 메인 애플리케이션
├── history/              # 개발 이력 및 마일스톤 로그
│   ├── INDEX.md
│   ├── 2026-06-09.md
│   ├── 2026-06-11.md
│   └── 2026-06-15.md
├── AGENTS.md             # AI Agent 개발 지침서
├── ROUTINES.md           # 표준 개발/배포/QA 루틴
├── RULES.md              # 코딩 & 보안 컨벤션
├── firebase.json         # Firebase Hosting 설정
└── README.md             # 프로젝트 소개 문서
```
