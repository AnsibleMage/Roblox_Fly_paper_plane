# Fly Paper Plane

> A Roblox paper airplane flight simulation game where players board and fly a paper plane in first-person perspective.

**Status**: In Development | **Developer**: @AnsibleMage | **Engine**: Roblox Studio

---

## Key Features

- **Paper Airplane Flight** -- Create and board a paper airplane with realistic physics
- **WASD Flight Control** -- Full directional control using keyboard input
- **First/Third-Person Camera** -- Toggle between camera perspectives during flight
- **Physics Engine** -- BodyVelocity and BodyGyro-based flight mechanics
- **Lobby System** -- Start button UI for launching flight sessions

---

## Tech Stack

| Category | Tool / Version |
|----------|---------------|
| Engine | Roblox Studio |
| Sync | Rojo 7.7.0-rc.1 |
| Language | Lua / Luau |
| Architecture | Client-Server with RemoteEvents |

---

## Project Structure

```
Roblox_Fly_paper_plane/
├── default.project.json              # Rojo project configuration
├── src/
│   ├── StarterGui/
│   │   └── LobbyUI.client.lua       # Lobby UI + airplane creation + boarding
│   ├── client/
│   │   ├── init.client.lua           # Client entry point
│   │   ├── Block1_FlightControl/
│   │   │   ├── init.lua              # Flight controller main module
│   │   │   ├── FlightPhysics.lua     # Flight physics (BodyVelocity/BodyGyro)
│   │   │   ├── FlightCamera.lua      # First/third-person camera
│   │   │   └── InputHandler.lua      # Keyboard/mouse input handling
│   │   ├── Block2_GameClient/
│   │   │   └── init.lua              # Game client state management
│   │   └── Block4_UI/
│   │       └── init.lua              # In-game UI module
│   ├── server/
│   │   ├── init.server.lua           # Server entry point + RemoteEvents
│   │   ├── Block1_FlightControl/
│   │   │   └── init.lua              # Server-side flight logic
│   │   ├── Block2_GameCore/
│   │   │   └── init.lua              # Core game loop
│   │   └── Block3_Social/
│   │       └── init.lua              # Social features
│   └── shared/
│       ├── Config.lua                # Global configuration
│       ├── PlaneModel.lua            # Airplane model generation
│       ├── CourseBuilder.lua         # Flight course builder
│       ├── EffectsManager.lua        # Visual effects
│       └── SoundManager.lua          # Audio management
└── doc/
    ├── 100_Product_PRD_Roblox_Fly_Paper_Plane.md
    ├── 110_Block1_FlightControl.md
    ├── 120_Block2_GameCore.md
    ├── 130_Block3_Social.md
    ├── 140_Block4_UI_Integration.md
    └── 150_Debugging_Log.md
```

---

## Getting Started

### Prerequisites

1. Roblox Studio (latest version)
2. [Rojo](https://rojo.space/) 7.7.0+
3. [Rojo Plugin](https://www.roblox.com/library/13916111004) for Roblox Studio

### Running Locally

```bash
# Start Rojo sync server
rojo serve default.project.json

# In Roblox Studio:
# 1. Open a new place
# 2. Plugins > Rojo > Connect
# 3. Click Play to test
```

---

## Architecture

The project follows a **Block-based modular architecture**:

| Block | Responsibility |
|-------|---------------|
| Block1 - FlightControl | Airplane physics, camera, and input handling |
| Block2 - GameCore/Client | Game state management and core loop |
| Block3 - Social | Social and multiplayer features |
| Block4 - UI | In-game UI elements and HUD |

Communication between client and server uses Roblox **RemoteEvents** through ReplicatedStorage.

---

## Documentation

| Document | Description |
|----------|-------------|
| [PRD](./doc/100_Product_PRD_Roblox_Fly_Paper_Plane.md) | Product Requirements Document |
| [Flight Control](./doc/110_Block1_FlightControl.md) | Block 1 design specification |
| [Game Core](./doc/120_Block2_GameCore.md) | Block 2 design specification |
| [Social](./doc/130_Block3_Social.md) | Block 3 design specification |
| [UI Integration](./doc/140_Block4_UI_Integration.md) | Block 4 design specification |
| [Debugging Log](./doc/150_Debugging_Log.md) | Bug tracking and debugging history |

---

## License

This project is licensed under the [MIT License](LICENSE).
