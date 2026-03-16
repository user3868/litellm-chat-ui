# 🤖 LiteLLM Chat UI

A clean, **single-file** AI chat web app that works with any **LiteLLM** or **OpenAI-compatible** API. No build step, no dependencies — just open `index.html`.

---

## 📸 Preview

| Desktop | Mobile Chat | Mobile Sidebar |
|---------|-------------|----------------|
| ![desktop](https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/docs/desktop.png) | ![mobile](https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/docs/mobile.png) | ![mobile-sidebar](https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/docs/mobile-sidebar.png) |

---

## ✨ Features

- 📎 **Image upload** — vision model support, multi-image, base64
- 🧠 **Think block folding** — `<think>` reasoning collapsed by default, click to expand
- 💬 **Multi-session** — full chat history in browser localStorage, nothing leaves your device
- 🔽 **Live model list** — click ↺ to fetch models from your API
- 📱 **Responsive** — desktop sidebar + mobile slide-out drawer
- 🌐 **Zero backend** — static HTML, host anywhere (Nginx, S3, GitHub Pages…)
- 🔌 **Universal** — LiteLLM · Ollama · vLLM · OpenRouter · OpenAI · any OpenAI-compatible API

---

## 🚀 Usage

### 1. Download

```bash
curl -O https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/index.html
# or just download index.html from this repo
```

### 2. Open & configure

Open `index.html` in any browser, then click **⚙️ API Settings** in the sidebar:

| Field | Example |
|-------|---------|
| API Address | `http://localhost:4000/v1` |
| API Key | `sk-...` |

Settings are saved to `localStorage` — no account, no server, no tracking.

### 3. Start chatting

Click **✏️ 新建对话**, select a model, optionally attach images, and send.

---

## 🔌 Compatible APIs

| Service | API Address | Key |
|---------|-------------|-----|
| **LiteLLM** | `http://your-host:4000/v1` | your litellm key |
| **Ollama** | `http://localhost:11434/v1` | `ollama` |
| **OpenAI** | `https://api.openai.com/v1` | `sk-...` |
| **OpenRouter** | `https://openrouter.ai/api/v1` | `sk-or-...` |
| **vLLM** | `http://your-host:8000/v1` | any string |

---

## 🖼️ Vision / Image support

Click **📎** to attach images before sending. Uses the standard OpenAI `image_url` format (base64 inline), compatible with any vision model exposed through LiteLLM.

---

## 🧠 Think / Reasoning blocks

Models like DeepSeek-R1 or QwQ wrap chain-of-thought in `<think>…</think>`. The UI collapses these automatically — click to expand.

---

## ⚠️ HTTPS + HTTP note

If you host this page on an HTTPS site (e.g. GitHub Pages) and your API runs on plain HTTP, the browser will block requests due to mixed-content policy. Options:

- Run the page locally (double-click the file, or `python -m http.server`)
- Put your API behind HTTPS (Nginx + cert, or Cloudflare Tunnel)

---

## 📁 Files

```
index.html   ← the entire app, one file
```

---

## 📄 License

MIT
