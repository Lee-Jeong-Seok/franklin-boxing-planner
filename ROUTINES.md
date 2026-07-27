# ROUTINES.md - 프랭클린 타임박싱 플래너 개발 및 운영 루틴

이 문서는 개발 프로젝트의 반복적인 작업(개발 프로세스, QA 검증, 이력 관리, 배포)을 체계적으로 수행하기 위한 표준 절차(Standard Operating Procedures)를 정의합니다.

---

## 🔄 1. 기능 개발 루틴 (Development Workflow Routine)

1. **요구사항 분석 및 영향도 체크**:
   * 수정할 기능이 **로컬 암호화(Web Crypto API)**, **IndexedDB 저장**, **통계**, 또는 **라이선스(Firebase)** 영역 중 어디에 해당하는지 파악합니다.
2. **코드 변경 구현**:
   * `public/index.html` (또는 프로젝트 소스 파일)에 변경 사항을 구현합니다.
   * `franklin timeboxing planner.html`과 `public/index.html` 간의 동기화 상태를 확인합니다.
3. **기능 검증 (QA)**:
   * 아래 [3. QA 및 검증 루틴] 절차에 따라 동작을 테스트합니다.
4. **이력 기록 및 정리**:
   * 개발이 완료되면 아래 [4. 개발 이력 관리 루틴]에 따라 `history/` 폴더에 작업 내역을 작성합니다.

---

## 🚀 2. 배포 루틴 (Deployment Routine)

1. **사전 검증**:
   * 브라우저 개발자 도구(F12) 콘솔에 자바스크립트 에러가 없는지 확인합니다.
   * Free / Essential 요금제 제한 로직 및 Firebase Firestore 라이선스 검증이 정상 작동하는지 점검합니다.
2. **Firebase Hosting 배포**:
   ```bash
   firebase deploy --only hosting
   ```
3. **배포 후 라이브 점검**:
   * 배포된 웹 URL에 접속하여 PIN 생성, 데이터 작성, 백업/복원 기능이 올바르게 구동되는지 최종 점검합니다.

---

## 🧪 3. QA 및 검증 루틴 (Quality Assurance Routine)

### A. 암호화 및 영구 저장 검증
1. **PIN 생성/인증**: 브라우저에서 앱 접속 후 4자리 이상 PIN 입력 시 올바르게 마스터 키가 생성되는지 확인.
2. **IndexedDB 자동 저장**: 할 일 추가/수정/삭제, 타임박스 입력 시 IndexedDB에 데이터가 수시로 저장되는지 확인.
3. **JSON 백업/복원**:
   * 상단 [데이터 백업] 클릭 시 암호화된 JSON 파일이 다운로드되는지 확인.
   * DevTools `Application Storage`에서 IndexedDB 데이터를 비운 뒤, [데이터 복원]으로 백업 파일을 불러와 완벽 복원되는지 확인.

### B. 라이선스 및 Paywall 검증
1. **Free 요금제 제한**:
   * 일일 백업 2회 시도 시 제한 모달창이 뜨는지 확인.
   * 통계 대시보드에서 30일/90일 클릭 시 차단 및 알림이 발생하는지 확인.
2. **Essential 요금제 인증**:
   * [라이선스 등록하기] 모달에서 등록된 테스트 키(예: `ESS-A1B2C3D4`) 입력.
   * Firebase Firestore와 연동되어 라이선스가 `used`로 바뀌고, 현재 브라우저의 UUID가 `deviceId`로 귀속되는지 확인.
   * 백업 무제한 및 30일 통계 탭이 해금되는지 확인.

---

## 📝 4. 개발 이력 관리 루틴 (History Logging Routine)

새로운 개발 단위나 마일스톤이 완료될 때마다 다음 루틴을 이행합니다:

1. **일자별 이력 파일 작성**:
   * `history/YYYY-MM-DD.md` 파일 생성
   * 포함 내용:
     * 주요 구현 내용 (기능 설명, 보안/아키텍처 변경점)
     * 검증(Verification) 결과
     * 향후 계획 및 유의사항
2. **인덱스 업데이트**:
   * `history/INDEX.md` 문서의 타임라인 및 변경 이력 요약에 신규 파일과 주요 변경 사항을 반영.
