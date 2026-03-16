# 🤖 LiteLLM Chat UI

A clean, single-file AI chat web app that works with any **LiteLLM** or **OpenAI-compatible** API endpoint. No installation, no build step — just open `index.html` in a browser.

**[🚀 Live Demo (GitHub Pages)](https://user3868.github.io/litellm-chat-ui)**

---

## ✨ Features

- 📎 **Image upload** — send photos directly to vision models (base64, multi-image)
- 🧠 **Think block folding** — `<think>` reasoning blocks are collapsed by default, click to expand
- 💬 **Multi-session chat** — sidebar keeps full conversation history (browser localStorage, nothing sent to any server)
- 🔽 **Model selector** — click ↺ to fetch the live model list from your API
- 🔐 **Obfuscated credentials** — API key & endpoint are XOR-encoded in the source, not plain text
- 📱 **Responsive** — desktop sidebar + mobile slide-out drawer, works on phone and PC
- 🌐 **Zero backend** — pure HTML + JS, deployable on GitHub Pages or any static host
- 🔌 **OpenAI-compatible** — works with LiteLLM, Ollama, vLLM, Xinference, OpenRouter, or the real OpenAI API

---

## 📸 Preview

| Desktop | Mobile Chat | Mobile Sidebar |
|---------|-------------|----------------|
| ![desktop](https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/docs/desktop.png) | ![mobile](https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/docs/mobile.png) | ![mobile-sidebar](https://raw.githubusercontent.com/user3868/litellm-chat-ui/master/docs/mobile-sidebar.png) |

---

## 🚀 Quick Start

### Option 1 — GitHub Pages (recommended)

1. Fork this repo
2. Go to **Settings → Pages → Source** → select `main` branch → `/root`
3. Done — your chat UI is live at `https://<you>.github.io/litellm-chat-ui`
4. Open the page, click ⚙️ in the sidebar, enter your API address

### Option 2 — Local (one command)

```bash
python server.py
# opens http://localhost:5000 automatically
```

> `server.py` is a tiny stdlib HTTP server (~30 lines). No pip install needed.

### Option 3 — Direct file

Just double-click `index.html`. Chrome/Edge work fine; Firefox may block `file://` cross-origin requests.

---

## ⚙️ Configuration

Click the **⚙️ API Settings** button at the bottom of the sidebar:

| Field | Description |
|-------|-------------|
| API Address | Your LiteLLM/OpenAI base URL, e.g. `http://localhost:4000/v1` |
| API Key | Your `sk-...` key |

Settings are saved to `localStorage` — no account, no server, no tracking.

### LiteLLM example

```bash
litellm --model ollama/llava --port 4000
# then set API Address to: http://localhost:4000/v1
```

### OpenAI example

```
API Address : https://api.openai.com/v1
API Key     : sk-...
```

### Ollama (direct) example

```
API Address : http://localhost:11434/v1
API Key     : ollama
```

---

## 🖼️ Image / Vision support

Click **📎** to attach one or more images before sending. Images are sent as base64 `image_url` content — the standard OpenAI vision format, supported by:

- LiteLLM (proxying any vision model)
- Ollama (`llava`, `minicpm-v`, `moondream`, …)
- OpenAI (`gpt-4o`, `gpt-4-turbo`, …)
- Google Gemini (via LiteLLM)
- Anthropic Claude (via LiteLLM)

---

## 🧠 Think / Reasoning block

Models like DeepSeek-R1, QwQ, or MiniCPM sometimes wrap their chain-of-thought in `<think>…</think>` tags. The UI collapses these automatically:

```
▶ 思考过程          ← click to expand
```

---

## 🔐 Credential obfuscation

The default API key and endpoint are XOR + Base64 encoded in the source so they don't appear as plain text when someone views the page source. This is **obfuscation, not encryption** — it deters casual inspection but will not stop a determined attacker. For production use, put a reverse proxy (e.g. Cloudflare Workers) in front and keep secrets server-side.

---

## 📁 File Structure

```
litellm-chat-ui/
├── index.html   # complete app — HTML + CSS + JS in one file
└── server.py    # optional local server (Python stdlib only)
```

---

## 🛠️ Customising the default model

Open `index.html` and find:

```html
<option value="vision-model-1">vision-model-1</option>
```

Change `vision-model-1` to any model ID you want as the default. You can also click ↺ in the UI to load the full model list from your API at runtime.

---

## 📄 License

MIT — do whatever you want with it.
