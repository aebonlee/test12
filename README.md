<<<<<<< HEAD
# ValueLink - 기업가치평가 플랫폼

**실제 검증 사례 5건을 포함한 완전 작동 시스템**

---

## 🎯 프로젝트 개요

5가지 평가법(DCF, 상대가치, 자산가치, 본질가치, 상증세법)을 활용한 AI 기반 기업가치평가 플랫폼입니다.

---

## 🚀 Quick Start

### Valuation Platform (메인 프로젝트)
```bash
cd Valuation_Company/valuation-platform/frontend
python -m http.server 3000
```

브라우저에서 열기: `http://localhost:3000/app/valuation-list.html`

---

## 📁 프로젝트 구조

```
ValueLink/
├── Valuation_Company/              ← 평가 플랫폼 (메인)
│   └── valuation-platform/
│       ├── backend/                ← FastAPI + SQLAlchemy
│       │   ├── models/             ← DB 모델 (9개)
│       │   ├── schemas/            ← Pydantic 스키마 (9개)
│       │   ├── routers/            ← API 라우터
│       │   └── services/           ← 비즈니스 로직
│       ├── frontend/               ← Next.js + React
│       │   ├── app/                ← 페이지
│       │   └── components/         ← UI 컴포넌트
│       └── docs/                   ← 프로젝트 문서
│
├── Process/                        ← Dev Package 구조
│   ├── P0_작업_디렉토리_구조_생성/
│   ├── S0_Project-SAL-Grid_생성/   ← SAL Grid 시스템
│   └── S1_개발_준비/ ~ S5_개발_마무리/
│
├── .claude/                        ← Claude Code 설정
│   ├── CLAUDE.md                   ← 핵심 규칙 (필독!)
│   ├── rules/                      ← 7대 작업 규칙
│   ├── methods/                    ← 작업 방법
│   └── work_logs/                  ← 작업 기록
│
├── scripts/                        ← 자동화 스크립트
│   ├── auto-commit.ps1             ← 5분마다 자동 커밋
│   ├── sync-to-root.js             ← Stage → Root 동기화
│   └── build-web-assets.js         ← 통합 빌드
│
└── Human_ClaudeCode_Bridge/        ← Orders/Reports
```

---

## 🏗️ 개발 현황

### ✅ 완료
- Backend 스키마 및 모델 정의 (Pydantic + SQLAlchemy)
- Frontend 프로젝트 목록 페이지
- 5가지 평가 엔진 통합
- Supabase 데이터베이스 구축
- 자동 커밋 시스템 (5분마다)

### ⏳ 진행 중
- FastAPI 라우터 구현
- Frontend 추가 페이지 개발
- API 통합 테스트

---

## 📖 Rules Location

**모든 작업 규칙은 `.claude/CLAUDE.md`에 있습니다.**

```
.claude/
├── CLAUDE.md              ← 핵심 규칙 (반드시 먼저 읽기!)
├── rules/                 ← 7대 작업 규칙
│   ├── 01_file-naming.md
│   ├── 02_save-location.md
│   ├── 03_area-stage.md
│   ├── 04_grid-writing-json.md
│   ├── 05_execution-process.md
│   ├── 06_verification.md
│   └── 07_task-crud.md
├── methods/               ← 작업 방법
│   ├── 00_initial-setup.md
│   └── 01_json-crud.md
└── work_logs/             ← 작업 기록
    └── current.md         ← 최신 작업 로그
```

---

## 🔧 Environment Setup

### 필수 도구
- Git
- Node.js 18+
- Python 3.8+
- PostgreSQL (Supabase)

### 초기 설정
```bash
# Backend
cd Valuation_Company/valuation-platform/backend
pip install -r requirements.txt
cp .env.example .env  # 환경 변수 설정

# Frontend
cd Valuation_Company/valuation-platform/frontend
npm install  # package.json 있는 경우
```

---

## 🤖 자동 커밋 시스템

**5분마다 자동으로 GitHub에 백업**

- 작업 이름: `ValueLink_AutoCommit`
- 실행 주기: 5분마다
- 로그 파일: `scripts/auto-commit.log`

### 관리 명령어
```powershell
# 작업 상태 확인
Get-ScheduledTask -TaskName "ValueLink_AutoCommit"

# 수동 실행
Start-ScheduledTask -TaskName "ValueLink_AutoCommit"

# 로그 확인
Get-Content scripts/auto-commit.log -Tail 20
```

---

## 📊 Data Files (JSON Method - 개별 파일 방식)

**위치:** `Process/S0_Project-SAL-Grid_생성/method/json/data/`

### 폴더 구조 (Dev Package 표준)
```
method/json/data/
├── index.json             ← 프로젝트 메타데이터 + task_ids 배열
├── grid_records/          ← 개별 Task JSON 파일
│   ├── S1BI1.json
│   ├── S1BI2.json
│   ├── S2F1.json
│   └── ... (Task ID별 파일)
├── completed/             ← 완료된 프로젝트 보관
└── users/                 ← 사용자별 데이터
```

**핵심:**
- `index.json` = 프로젝트 정보 + Task ID 목록
- `grid_records/{TaskID}.json` = 개별 Task 데이터
- Viewer는 `index.json` 먼저 로드 → `task_ids`로 개별 파일 병렬 로드

---

## 🔗 Related Documentation

| 문서 | 위치 | 내용 |
|------|------|------|
| **핵심 규칙** | `.claude/CLAUDE.md` | 7대 규칙, 절대 규칙, 작업 방법 |
| **작업 로그** | `.claude/work_logs/current.md` | 최신 작업 기록 |
| **Dev Package 원본** | `README_DevPackage.md` | Dev Package 표준 가이드 |
| **평가 플랫폼** | `Valuation_Company/valuation-platform/` | 메인 프로젝트 |
| **API 설계** | `Valuation_Company/valuation-platform/docs/` | API 명세서 |

---

## 🌐 GitHub Repository

https://github.com/SUNWOONGKYU/ValueLink

### Git 설정
```bash
git config user.email "wksun999@hanmail.net"
git config user.name "SUNWOONGKYU"
```

---

## 📝 Session Start Checklist

1. **`.claude/work_logs/current.md`** - 이전 작업 기록 확인
2. **`Human_ClaudeCode_Bridge/Reports/`** - 이전 작업 결과 확인
3. **`.claude/CLAUDE.md`** - 규칙 확인

---

## 🎯 Quick Reference

**작업 전 필수 확인:** `.claude/CLAUDE.md`

| 상황 | CLAUDE.md 섹션 |
|------|---------------|
| Task 실행할 때 | "절대 규칙 3: Project SAL Grid Task" |
| 파일 저장할 때 | "절대 규칙 4: Stage 폴더에 먼저 저장" |
| JSON 수정할 때 | "JSON CRUD 작업 시 필수 준수" |
| 새 폴더 만들 때 | "절대 규칙 1: 폴더 임의 생성 금지" |

---

**Made with ❤️ by Claude Code**
=======
# test12
ValueLink
>>>>>>> 71a93bfe5c114dfec61e3a7ecbcd41355ef81173
