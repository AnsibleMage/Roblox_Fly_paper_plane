# Fly Paper Plane

> 종이비행기를 만들어 탑승하고 1인칭 시점으로 비행하는 Roblox 비행 시뮬레이션 게임입니다.

**상태**: 개발 중 | **개발자**: @AnsibleMage | **엔진**: Roblox Studio

---

## 주요 특징

- **종이비행기 비행** -- 실제 물리 엔진 기반의 종이비행기 생성 및 탑승
- **WASD 비행 컨트롤** -- 키보드 입력을 통한 전방향 비행 제어
- **1인칭/3인칭 카메라** -- 비행 중 카메라 시점 전환 기능
- **물리 엔진** -- BodyVelocity와 BodyGyro 기반 비행 역학
- **로비 시스템** -- 비행 세션을 시작하는 스타트 버튼 UI

---

## 기술 스택

| 분류 | 도구 / 버전 |
|------|------------|
| 엔진 | Roblox Studio |
| 동기화 | Rojo 7.7.0-rc.1 |
| 언어 | Lua / Luau |
| 아키텍처 | RemoteEvents 기반 클라이언트-서버 구조 |

---

## 프로젝트 구조

```
Roblox_Fly_paper_plane/
├── default.project.json              # Rojo 프로젝트 설정
├── src/
│   ├── StarterGui/
│   │   └── LobbyUI.client.lua       # 로비 UI + 비행기 생성 + 탑승 로직
│   ├── client/
│   │   ├── init.client.lua           # 클라이언트 진입점
│   │   ├── Block1_FlightControl/
│   │   │   ├── init.lua              # 비행 컨트롤러 메인 모듈
│   │   │   ├── FlightPhysics.lua     # 비행 물리 엔진 (BodyVelocity/BodyGyro)
│   │   │   ├── FlightCamera.lua      # 1인칭/3인칭 카메라
│   │   │   └── InputHandler.lua      # 키보드/마우스 입력 처리
│   │   ├── Block2_GameClient/
│   │   │   └── init.lua              # 게임 클라이언트 상태 관리
│   │   └── Block4_UI/
│   │       └── init.lua              # 인게임 UI 모듈
│   ├── server/
│   │   ├── init.server.lua           # 서버 진입점 + RemoteEvents
│   │   ├── Block1_FlightControl/
│   │   │   └── init.lua              # 서버 측 비행 로직
│   │   ├── Block2_GameCore/
│   │   │   └── init.lua              # 코어 게임 루프
│   │   └── Block3_Social/
│   │       └── init.lua              # 소셜 기능
│   └── shared/
│       ├── Config.lua                # 글로벌 설정
│       ├── PlaneModel.lua            # 비행기 모델 생성
│       ├── CourseBuilder.lua         # 비행 코스 빌더
│       ├── EffectsManager.lua        # 시각 효과
│       └── SoundManager.lua          # 오디오 관리
└── doc/
    ├── 100_Product_PRD_Roblox_Fly_Paper_Plane.md
    ├── 110_Block1_FlightControl.md
    ├── 120_Block2_GameCore.md
    ├── 130_Block3_Social.md
    ├── 140_Block4_UI_Integration.md
    └── 150_Debugging_Log.md
```

---

## 시작하기

### 필수 도구

1. Roblox Studio (최신 버전)
2. [Rojo](https://rojo.space/) 7.7.0+
3. Roblox Studio용 [Rojo 플러그인](https://www.roblox.com/library/13916111004)

### 로컬 실행 방법

```bash
# Rojo 동기화 서버 시작
rojo serve default.project.json

# Roblox Studio에서:
# 1. 새로운 Place 열기
# 2. Plugins > Rojo > Connect
# 3. Play 버튼으로 테스트
```

---

## 아키텍처

프로젝트는 **Block 기반 모듈형 아키텍처**를 따릅니다:

| Block | 책임 |
|-------|------|
| Block1 - FlightControl | 비행기 물리, 카메라, 입력 처리 |
| Block2 - GameCore/Client | 게임 상태 관리 및 코어 루프 |
| Block3 - Social | 소셜 및 멀티플레이어 기능 |
| Block4 - UI | 인게임 UI 요소 및 HUD |

클라이언트와 서버 간 통신은 ReplicatedStorage의 Roblox **RemoteEvents**를 사용합니다.

---

## 문서

| 문서 | 설명 |
|------|------|
| [PRD](./doc/100_Product_PRD_Roblox_Fly_Paper_Plane.md) | 제품 요구사항 문서 |
| [비행 컨트롤](./doc/110_Block1_FlightControl.md) | Block 1 설계 명세 |
| [게임 코어](./doc/120_Block2_GameCore.md) | Block 2 설계 명세 |
| [소셜](./doc/130_Block3_Social.md) | Block 3 설계 명세 |
| [UI 통합](./doc/140_Block4_UI_Integration.md) | Block 4 설계 명세 |
| [디버깅 로그](./doc/150_Debugging_Log.md) | 버그 추적 및 디버깅 기록 |

---

## 라이선스

이 프로젝트는 [MIT 라이선스](LICENSE)에 따라 배포됩니다.
