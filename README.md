# 🚀 SUPERNOVA Application

SUPERNOVA Application is a local-first personal AI desktop assistant for Windows with a connected Python backend, Telegram remote control, and an Android companion app. It is built for real computer use, remote monitoring, and mobile access.

## ✨ What This Project Is

- A Windows desktop assistant for everyday use.
- A Python backend that handles APIs, automation, and AI routing.
- A Telegram bot for quick remote control and alerts.
- An Android app for mobile monitoring and interaction.
- A single platform for conversation, system control, file handling, voice, vision, scheduling, and remote access.

## 🧩 Main Parts

- WPF desktop application for the Windows UI.
- Python FastAPI backend for core logic and APIs.
- Telegram bot for quick remote commands and alerts.
- Android Flutter app for mobile control and monitoring.

## 🎯 Why This Project Exists

- To make everyday computer work easier.
- To reduce switching between many separate tools.
- To let the user interact with one connected assistant.
- To route each request to the right service and return useful results in simple language.

## ⭐ Key Features

### 🖥️ Desktop Application (WPF)
- Clean chat interface with WebView2 rendering
- Real-time token streaming for AI responses
- Voice control (Ctrl+Shift+Space hotkey)
- System tray integration with quick access
- Modern theming (dark, light, faded, shaded)
- Settings panel with model and voice configuration
- Connection status monitoring

### ⚙️ Backend Services (Python/FastAPI)
- **AI Models:** Ollama (local), TypeGPT (cloud), INFIP (image generation)
- **Voice:** Faster-Whisper STT, Piper/Melo TTS
- **Vision:** Screenshot, OCR, element detection, find-and-click
- **13 Tool Groups:** System control, files, browser, terminal, memory, scheduling, messaging, and more
- **60+ Deterministic Commands** + LLM fallback routing
- **Telegram Commands:** 20+ remote control actions (`/screenshot`, `/stats`, `/kill`, `/type`, `/click`, `/memory`, etc.)
- **WebSocket Streaming:** Real-time metrics and responses
- **SQLite Persistence:** Task scheduling, facts, history

### 📱 Telegram Bot Remote Control
- System monitoring (`/stats`, `/ps`)
- Device control (`/mute`, `/unmute`, `/sleep`, `/lock`, `/restart`)
- Application management (`/open`, `/close`)
- Screen interaction (`/screenshot`, `/click`, `/type`)
- File transfer and search
- Task scheduling (`/schedule`, `/tasks`, `/cancel`)
- Memory operations (`/memory`, `/forget`)
- Voice message transcription
- Model management (`/models`, `/setmodel`)
- Rate limiting and security

### 🤖 Android Companion App (Flutter)
- QR code pairing with desktop
- Real-time chat via WebSocket
- Desktop screenshot streaming (MJPEG)
- Remote control (click, type, keyboard events)
- File browser and transfer
- System health dashboard
- Settings management
- JWT token authentication
- Automatic reconnection

### 🧠 Supported LLM Providers
- **Ollama:** qwen2.5:7b, qwen3:8b, gemma4:e4b, qwen3-vl:4b (vision)
- **TypeGPT:** openai/gpt-oss-120b, gpt-oss-20b, kimi-k2, deepseek-v3.1, ministral-14b, and more
- **Image Generation:** INFIP with 8 models (img4, img3, qwen, lucid-origin, phoenix, sdxl, flux-schnell, sdxl-lite)

### 👁️ Vision & Click Automation
- Screenshot capture with region selection
- PaddleOCR text extraction
- Element detection with confidence scoring
- 3 click strategies: confidence_first, exact_first, nearest_center
- Configurable confidence thresholds

### 🛠️ System Control & Automation
- CPU, RAM, disk, battery monitoring
- Volume and brightness control
- Window management and app launching
- Process enumeration and termination
- PowerShell execution with safety validation
- Clipboard operations
- Safe file deletion

### 📂 File Management
- Recursive file search with query matching
- Create, read, delete, rename, move operations
- Archive/unzip support
- Upload/download via REST API
- File metadata retrieval

### 🗓️ Scheduling & Memory
- APScheduler-backed task scheduling
- Persistent SQLite job store
- Fact storage and retrieval
- Conversation history archival
- Task status tracking and cancellation

### 🌐 Remote Access
- Local WiFi network support
- Optional ngrok HTTPS tunneling for internet access
- JWT token-based authentication (30-day expiration)
- QR code pairing flow
- Session isolation per client

## 🏗️ Technical Architecture

**Frontend:** C# WPF with WebView2 for modern web UI rendering
**Backend:** Python 3.9+ with FastAPI (Uvicorn on port 8765)
**Communication:** HTTP REST + WebSocket, YAML configuration
**Database:** SQLite with WAL mode for persistence
**Task Scheduler:** APScheduler with async support
**Automation:** PyAutoGUI, PyWinAuto, Playwright for browser control
**Voice Processing:** Faster-Whisper + Piper/Melo TTS engines
**Mobile:** Flutter with provider state management, dio/websockets networking
**Deployment:** Standalone Python backend + WPF desktop + Flutter APK
**Security:** JWT tokens, AES-256 encryption, environment-based secrets

## 💡 Product Highlights

- **Unified Platform:** Desktop + Backend + Telegram + Android as one system
- **Local-First Privacy:** Runs locally on Windows with optional cloud services
- **AI-Powered:** Deterministic routing + LLM fallback for command understanding
- **Multi-Channel Access:** Chat on desktop, control via Telegram, manage from phone
- **Real-World Automation:** 60+ tools across system, files, browser, voice, vision
- **Extensible Architecture:** Modular services for future growth
- **Production-Ready:** Error handling, logging, rate limiting, security

## 📌 Project Status

The project already includes the core system architecture and major application surfaces. The Windows application, backend services, Telegram integration, and Android companion app are part of the same product vision, with the Windows `.exe` package and Android APK release planned next.

## 🧰 System Requirements

- **Windows 10/11** (64-bit)
- **8 GB RAM** minimum (16 GB recommended for local LLMs)
- **10 GB disk space** (20+ GB with Ollama models)
- **Python 3.9+** for backend
- **.NET 6/7** for desktop app
- **Flutter SDK** for Android app (optional)

## 🔗 Repository Links

- This is the GitHub repo: https://github.com/manojkumarfade/SUPERNOVA
- Windows release file: [Insert .exe release link here]
- Android release file: [Insert APK release link here]
- Documentation: See REPORT.md for detailed architecture guide

## ⚡ Quick Start

### Backend Setup
```bash
git clone https://github.com/manojkumarfade/SUPERNOVA.git
cd SUPERNOVA
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements/base.txt
cp config.yaml.example config.yaml
# Edit config.yaml with API keys and settings
python main.py
# Backend runs on http://127.0.0.1:8765
```

### Desktop App
```bash
# In Visual Studio or command line
cd NOVA_WPF
dotnet restore
dotnet build
dotnet run
```

### Telegram Bot
1. Create bot with @BotFather
2. Add token and user ID to config.yaml
3. Backend auto-registers on startup

### Android App
```bash
cd Android\flutter\supernova_remote
flutter pub get
flutter build apk --release
flutter install
```

### Local Access
- Desktop: `http://127.0.0.1:8765` (backend)
- Telegram: @YourBotName commands
- Android: Pair via QR code (Settings -> Show Pairing QR)

### Remote Access (Optional)
1. Get ngrok token from https://ngrok.com
2. Set in config.yaml: `ngrok_token: "your-token"`
3. Backend auto-creates tunnel on startup
4. Share tunnel URL with remote clients

## ⚙️ Configuration Options

Key settings in `config.yaml`:
- `OLLAMA_PRIORITY_MODELS`: Local LLM selection
- `voice_hotkey`: Voice activation key (default: Ctrl+Shift+Space)
- `vision_click_strategy`: UI automation strategy (confidence_first, exact_first, nearest_center)
- `screen_stream_fps`: MJPEG stream frame rate (default: 15)
- `android_pairing_enabled`: Enable QR code pairing
- `telegram_enabled`: Enable Telegram bot
- `ngrok_enabled`: Enable remote tunnel (requires token)

## 🚀 Future Enhancements

- Standalone Windows `.exe` release package
- Android APK release on Play Store
- Enhanced mobile UI with more dashboard widgets
- Advanced task automation workflows
- Additional safety and access controls
- Better notifications and status updates
- Cross-platform support (macOS, Linux backend)

## 📄 License

Add your chosen license here before publishing the repository.

