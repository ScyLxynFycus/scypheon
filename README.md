<p align="center">
  <img src="assets/logo.jpg" width="200" alt="Scypheon">
</p>

<h1 align="center">Scypheon</h1>

<p align="center">
  <strong>On-Device Agentic AI Framework for Android</strong>
</p>

<p align="center">
  <a href="#architecture">Architecture</a> •
  <a href="#features">Features</a> •
  <a href="#technical-specs">Technical Specs</a> •
  <a href="#roadmap">Roadmap</a> •
  <a href="#limitations">Limitations</a>
</p>

---

## Overview

Scypheon is an on-device AI agent framework that runs entirely on Android devices without cloud dependencies. The system implements a complete agent loop with tool calling, memory persistence, and accessibility integrations.

**Core Philosophy:** All AI inference happens locally. Zero telemetry. User data never leaves the device.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      Scypheon Agent Core                     │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │   Router    │→ │   Planner   │→ │  Agentic Executor   │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
│         ↓               ↓                    ↓              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │  Memory DB  │  │ Tool Router │  │  Reflection Engine  │  │
│  │ (SQLCipher) │  │             │  │                     │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
├─────────────────────────────────────────────────────────────┤
│                    LLM Inference Layer                       │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  llama.cpp (GGUF) / MediaPipe GenAI (GPU accelerated) │   │
│  │  Supported: Qwen 0.5B-3B, DeepSeek, Llama 3.2         │   │
│  └──────────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────────┤
│                   Accessibility Layer                        │
│  ┌────────────┐  ┌────────────┐  ┌────────────────────┐    │
│  │ Navigation │  │  Live      │  │  Motor Assistant   │    │
│  │ Assistant  │  │  Captioner │  │  (Head Tracking)   │    │
│  └────────────┘  └────────────┘  └────────────────────┘    │
└─────────────────────────────────────────────────────────────┘
```

## Features

### Agent System
| Component | Status | Description |
|-----------|--------|-------------|
| Agent Loop | ✅ Implemented | Observe → Plan → Execute → Reflect cycle |
| Tool Calling | ✅ Implemented | 15+ integrated tools (calendar, search, math, etc.) |
| Memory System | ✅ Implemented | Hybrid keyword + vector search with SQLCipher |
| Context Management | ✅ Implemented | Token-aware sliding window with priority |
| Failure Recovery | ✅ Implemented | Recursion guard, error handling, graceful degradation |

### On-Device Inference
| Component | Status | Description |
|-----------|--------|-------------|
| llama.cpp Integration | ✅ Implemented | GGUF model loading via JNI |
| MediaPipe GenAI | ✅ Implemented | GPU acceleration on supported devices |
| Model Support | ✅ Tested | Qwen 3B, DeepSeek 1.5B, Llama 3.2 1B |
| Memory Footprint | ✅ Optimized | ~2GB RAM for 3B model |

### Accessibility Suite
| Feature | Target Users | Status |
|---------|-------------|--------|
| Aether Navigator | Blind/Low Vision | ✅ Implemented |
| Live Captioner | Deaf/Hard of Hearing | ✅ Implemented |
| Motor Assistant | Motor Impairments | ✅ Implemented |
| Sound Event Detector | Deaf/Hard of Hearing | ✅ Implemented |
| Medicine Guard | Elderly/Chronic Illness | ✅ Implemented |

## Technical Specifications

| Spec | Value |
|------|-------|
| **Min Android SDK** | 28 (Android 9.0) |
| **Target SDK** | 35 (Android 15) |
| **LLM Backend** | llama.cpp (ARM64 NEON + GPU) |
| **Database** | Room + SQLCipher (AES-256) |
| **Vision** | MediaPipe Vision, ML Kit |
| **Audio** | MediaPipe Audio Classifier |
| **Architecture** | arm64-v8a only |

## Roadmap

### Current Version (v1.0-alpha)
- [x] Core agent loop with tool calling
- [x] On-device LLM inference
- [x] Encrypted memory persistence
- [x] Accessibility suite (blind, deaf, motor)
- [x] Agentic app control (AccessibilityService)

### Next Release (v1.1)
- [ ] Vision Language Model integration
- [ ] Multi-turn planning improvements
- [ ] Benchmark suite for agent evaluation
- [ ] Plugin architecture for community tools

### Future
- [ ] Cross-device sync (encrypted)
- [ ] Custom model fine-tuning pipeline
- [ ] Federated learning for accessibility models

## Known Limitations

> Transparency about limitations is essential for trust.

| Limitation | Details |
|------------|---------|
| **Model Size** | Limited to 3B parameters due to mobile memory constraints |
| **Context Length** | 4K tokens max for stable performance |
| **Tool Reliability** | Web search depends on external APIs |
| **Accessibility** | Some features require specific hardware (e.g., head tracking needs front camera) |
| **Language Support** | Optimized for English and Indonesian |

## Benchmarks

*Coming soon: Agent task completion benchmarks on custom evaluation suite.*

Planned metrics:
- Task completion rate (3-step, 5-step, 10-step)
- Latency (first token, total response)
- Memory efficiency
- Accessibility feature accuracy

## License

Scypheon is proprietary software. This repository is for project documentation only.

© 2025-2026 ScyLxynFycus. All rights reserved.

---

<p align="center">
  <sub>Built with engineering discipline. Designed for accessibility. Powered by on-device AI.</sub>
</p>
