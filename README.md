# AI Telegram OpenClaw Bot

AI Telegram chatbot yang menggunakan OpenClaw sebagai agent orchestration layer dan OpenRouter sebagai LLM gateway. Project ini dibuat untuk membangun chatbot yang bisa diakses melalui Telegram, menjalankan workflow agent, dan memilih model LLM secara fleksibel melalui OpenRouter.

## Dokumentasi Project

### Telegram Chat


![Telegram chat demo](docs/screenshots/telegram-chat-demo.png)

### OpenRouter Model Selection


![OpenRouter model selection](docs/screenshots/openrouter-model-selection.png)

### Demo Video



[Watch Telegram bot demo](docs/videos/telegram-bot-demo.mp4)

## Project Overview

Project ini menghubungkan tiga komponen utama:

- Telegram sebagai interface chat untuk user.
- OpenClaw sebagai runtime/orchestration layer untuk agent, tools, dan workflow.
- OpenRouter sebagai gateway untuk memilih berbagai model LLM tanpa mengubah core logic aplikasi.

Dengan arsitektur ini, chatbot bisa dikembangkan menjadi assistant yang lebih fleksibel, misalnya untuk customer support, personal assistant, automation bot, atau agent berbasis tool calling.

## Key Features

- Chatbot dapat diakses langsung dari Telegram.
- Integrasi OpenClaw untuk menjalankan AI agent workflow.
- Integrasi OpenRouter untuk routing model LLM.
- Konfigurasi aman melalui environment variables.
- Struktur repository siap untuk portfolio GitHub.
- Dokumentasi setup tanpa menyimpan token/API key pribadi.
- Slot dokumentasi untuk screenshot dan video demo.

## Tech Stack

- Telegram Bot API
- OpenClaw
- OpenRouter
- Node.js
- JavaScript / TypeScript
- GitHub

## Architecture

```mermaid
flowchart LR
  user["User Telegram"] --> telegram["Telegram Bot API"]
  telegram --> backend["Bot Backend"]
  backend --> openclaw["OpenClaw Agent"]
  openclaw --> tools["Agent Tools / Workflow"]
  openclaw --> openrouter["OpenRouter Gateway"]
  openrouter --> model["Selected LLM Model"]
  model --> openrouter
  openrouter --> openclaw
  openclaw --> backend
  backend --> telegram
  telegram --> user
```

## How It Works

1. User mengirim pesan ke bot melalui Telegram.
2. Telegram Bot API meneruskan pesan ke backend aplikasi.
3. Backend memproses pesan dan meneruskannya ke OpenClaw agent.
4. OpenClaw menjalankan instruksi, tools, atau workflow agent yang dibutuhkan.
5. Request LLM dikirim ke OpenRouter.
6. OpenRouter meneruskan request ke model yang dipilih.
7. Response model dikembalikan ke OpenClaw, lalu dikirim kembali ke user Telegram.

## Repository Structure

```txt
src/
  bot/        Telegram handler, command, dan message routing.
  agent/      Integrasi OpenClaw agent dan tools.
  llm/        Integrasi OpenRouter dan daftar model.
  config/     Validasi environment variables dan runtime config.
docs/
  screenshots/
    telegram-chat-demo.png
    openrouter-model-selection.png
  videos/
    telegram-bot-demo.mp4
  architecture.md
  setup-openclaw.md
  demo.md
tests/
.env.example
.gitignore
openclaw.example.json
README.md
```



## OpenRouter Model Routing

OpenRouter digunakan agar bot bisa mengganti model LLM tanpa mengubah integrasi utama dengan Telegram dan OpenClaw.

Contoh model yang bisa dikonfigurasi:

- `openai/gpt-4.1-mini`
- `anthropic/claude-3.7-sonnet`
- `deepseek/deepseek-chat`
- `google/gemini-pro`

Model default disimpan melalui environment variable:

```env
DEFAULT_MODEL=openai/gpt-4.1-mini
```
