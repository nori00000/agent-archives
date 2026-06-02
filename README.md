# Agent Archives

> **한눈에 / At a glance**  
> Forked desktop app for browsing Claude Code and OpenCode session history.  
> 자세한 한영 프로젝트 설명, 검색 키워드, 저작권 범위: [PROJECT.md](./PROJECT.md) · [NOTICE.md](./NOTICE.md)


Claude Code와 OpenCode 세션 히스토리를 탐색하는 macOS 데스크톱 앱.

## 스크린샷

### 세션 뷰어
| Light Mode | Dark Mode |
|------------|-----------|
| ![Sessions Light](assets/screenshot-sessions-light.png) | ![Sessions Dark](assets/screenshot-sessions-dark.png) |

### 대시보드
| Light Mode | Dark Mode |
|------------|-----------|
| ![Dashboard Light](assets/screenshot-dashboard-light.png) | ![Dashboard Dark](assets/screenshot-dashboard-dark.png) |

## 설치

### DMG 다운로드 (권장)

**[📦 Releases 페이지에서 다운로드](https://github.com/johnfkoo951/agent-archives/releases/latest)**

| 파일 | Mac 종류 |
|------|----------|
| `Agent-Archives-x.x.x-mac-arm64.dmg` | Apple Silicon (M1/M2/M3/M4) |
| `Agent-Archives-x.x.x-mac-x64.dmg` | Intel Mac |

> **Mac 종류 확인**: 메뉴바 →  → "이 Mac에 관하여" → 칩 확인

### 설치 방법

1. DMG 파일 다운로드
2. DMG 열고 `Agent Archives.app`을 Applications 폴더로 드래그
3. 앱 실행

### ⚠️ macOS 보안 경고 해결

이 앱은 Apple 개발자 인증서로 서명되지 않은 오픈소스 프로젝트입니다. macOS Gatekeeper가 실행을 차단할 수 있습니다.

**"개발자를 확인할 수 없습니다"** 또는 **"앱이 손상되었습니다"** 경고가 나타나면:

#### 방법 1: 우클릭으로 열기 (가장 간단)
1. Applications 폴더에서 `Agent Archives.app` **우클릭** (또는 Control+클릭)
2. **열기** 선택
3. 경고창에서 **열기** 클릭

#### 방법 2: 터미널에서 Gatekeeper 우회
```bash
xattr -cr "/Applications/Agent Archives.app"
open "/Applications/Agent Archives.app"
```

#### 방법 3: 시스템 설정에서 허용
1. 앱 실행 시도 (경고 발생)
2. **시스템 설정** → **개인정보 보호 및 보안**
3. 하단 **"Agent Archives" 앱이 차단됨** 메시지 옆 **"확인 없이 열기"** 클릭

> 💡 이는 보안 취약점이 아닌 Apple의 앱 배포 정책 때문입니다. 오픈소스이므로 [소스코드](https://github.com/johnfkoo951/agent-archives)를 직접 확인할 수 있습니다.

## 기능

- **세션 탐색**: Claude Code / OpenCode 대화 히스토리 검색 및 탐색
- **태그 & 이름**: 세션에 태그 추가, 이름 지정
- **대시보드**: 활동 통계, 프로젝트별 분석
- **Resume**: 터미널에서 세션 이어서 작업 (iTerm2, Terminal, Warp 지원)
- **Hookmark 연동**: `agentarchives://session/{id}` 딥링크 지원

## 요구사항

- macOS 10.15 (Catalina) 이상
- Python 3.8+ (앱 내장 서버용)
- Claude Code 또는 OpenCode 설치됨

---

## 개발자용

### 소스에서 실행

```bash
# 저장소 클론
git clone https://github.com/johnfkoo951/agent-archives.git
cd agent-archives

# Python 의존성 설치
pip3 install fastapi uvicorn pydantic

# Node.js 의존성 설치
cd app && npm install && cd ..

# 개발 모드 실행
cd app && npm start
```

### 빌드

```bash
cd app
npm run build

# 결과물: dist/Agent-Archives-x.x.x-mac-arm64.dmg, dist/Agent-Archives-x.x.x-mac-x64.dmg
```

### 프로젝트 구조

```
agent-archives/
├── history-server.py       # FastAPI 백엔드 (Python)
├── history-viewer.html     # Vue.js 프론트엔드 (Single HTML)
├── update-index.py         # 세션 인덱스 생성
├── app/
│   ├── src/main.js         # Electron 메인 프로세스
│   ├── src/preload.js      # IPC 브릿지
│   └── package.json        # Electron 설정
└── assets/                 # 로고, 아이콘
```

### 기술 스택

| 구성요소 | 기술 |
|----------|------|
| Backend | Python 3, FastAPI, Uvicorn |
| Frontend | Vue.js 3, Tailwind CSS, Chart.js |
| Desktop | Electron 28, electron-builder |

## 라이선스

MIT
