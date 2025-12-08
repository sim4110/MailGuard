# 🛡️ MailGuard  
지능형 이메일 보안 플랫폼 – 악성 URL 탐지, 도메인 차단 관리, 메일 분석 자동화

MailGuard는 이메일 내 포함된 **악성 URL, 피싱 콘텐츠, 스팸 패턴, 첨부파일 위협**을 자동으로 분석하여  
사용자의 이메일 보안을 향상시키는 Spring Boot 기반의 보안 플랫폼입니다.

Gmail OAuth 기반 메일 연동, 정적 룰 기반 탐지, LLM(OpenAI) 분석, VirusTotal 파일 스캔을 결합하여  
**위험도 3단계(안전/의심/위험)**로 메일을 종합 평가합니다.  
또한, 분석 결과를 **PDF 보고서로 생성·다운로드**할 수 있는 기능을 제공합니다.  

---


## 🚀 주요 기능

### 1️⃣ **회원 관리**
- 회원가입 / 로그인 / 로그아웃  
- 비밀번호 해싱(BCrypt) 저장  
- 이메일 인증 & 계정 활성화 기능  
- 프로필 수정 / 탈퇴  

---

### 2️⃣ **메일 연동 (Gmail / Naver)**
- OAuth 2.0 기반 Gmail 메일 동기화  
- Naver IMAP 기반 메일 로딩  
- 메일 목록 조회 / 열람 / 첨부파일 확인  

---

### 3️⃣ **메일 악성 분석 엔진**

#### 🔹 본문/제목 분석 (Rule + LLM)
- 피싱 키워드 기반 정적 탐지  
- GPT 기반 악성 가능성 평가 (발표자료 Page 22 참고)  
- 위험도 **3단계(안전/의심/위험)** 분류  

#### 🔹 첨부파일 검사
- 파일 확장자 유형별 분류  
- 압축파일 내부 분석  
- VirusTotal API 통한 악성 여부 판단 (발표자료 Page 23 참고)  

#### 🔹 URL 검사
- URL 패턴 분석 및 정적 룰 기반 위험도 평가  
- Blocked Domain DB 기반 즉시 차단  

#### 🔹 종합 분석 로직
- Rule 기반 점수  
- GPT 분석 점수  
- 첨부파일 검사 결과  
→ **단일 종합 점수로 통합**

---

### 4️⃣ **📄 분석 리포트(PDF) 생성 기능**
(발표자료 Page 24 참고)

- 특정 메일 선택 → **분석 보고서 자동 생성**
- 종합 점수 / 본문 분석 / 첨부파일 분석 / URL 위험 결과 포함
- **PDF 다운로드 기능 제공**
- 보고서 UI 및 데이터 매핑 완성(T17-1~T17-3 완료)  

---

### 5️⃣ **관리자 페이지 (Admin)**
- 악성 도메인 추가 / 수정 / 삭제  
- HTTP / HTTPS / BOTH 스킴 관리  
- 관리자 계정 여부 검증  
- URL DB 업데이트 기능  

---

## 📂 프로젝트 구조

```
MailGuard/
├─ src/main/java/com/example/MailGuard
│ ├─ config/ # Security / OAuth 설정
│ ├─ controller/ # Auth, Gmail, Report, Domain, Profile Controller
│ ├─ service/ # 분석 로직, 이메일 인증, 파일 스캔, 리포트 생성
│ ├─ repository/ # User, Domain, Token Repository
│ └─  domain/ # Entity 클래스
│
├─ src/main/resources
│ ├─ templates/ # Thymeleaf 템플릿
│ ├─ static/ # CSS / JS / 이미지
│ └─ application.properties
│
└─ README.md
```

---
## 🧰 기술 스택

| 분야 | 기술 |
|------|------|
| Backend | Spring Boot, Spring Security, Spring MVC |
| DB | MySQL, JPA/Hibernate |
| Frontend | Thymeleaf, Bootstrap |
| Auth | OAuth 2.0 (Google), BCrypt |
| Email | Gmail SMTP / IMAP |
| Security | VirusTotal API(옵션), URL Pattern 분석 |

---

## ▶️ 실행 방법
Gradle 실행:
./gradlew bootRun

또는
STS4 → Run As → Spring Boot App

---

## 📌 향후 개발 예정 (Roadmap)

시스템 최적화 / 분석 속도 개선

API 키 사용량 자동 모니터링

Chrome 확장 프로그램 개발

외부 API 의존성 완화

---

## 📄 License

본 프로젝트는 개인/교육/연구 목적으로 작성되었으며
필요 시 라이선스를 지정할 예정입니다.
