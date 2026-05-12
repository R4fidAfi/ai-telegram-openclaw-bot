# Architecture

Repository ini mendokumentasikan integrasi chatbot Telegram dengan OpenClaw dan OpenRouter.

## Flow

```txt
User Telegram
  -> Telegram Bot API
  -> Bot Backend
  -> OpenClaw Agent
  -> OpenRouter
  -> Selected LLM Model
  -> OpenRouter
  -> OpenClaw Agent
  -> Bot Backend
  -> Telegram Bot API
  -> User Telegram
```

## Komponen

- Telegram Bot: menerima pesan user dan mengirim balasan.
- Bot Backend: memvalidasi pesan, menjalankan command, dan menghubungkan request ke agent.
- OpenClaw Agent: mengatur workflow agent, tool, dan instruksi.
- OpenRouter: gateway untuk memilih model LLM dari beberapa provider.
- LLM Model: model yang menghasilkan response akhir.

## Catatan Portfolio

Bagian ini bisa diperluas dengan diagram deployment, screenshot flow, dan alasan teknis memilih OpenClaw serta OpenRouter.

