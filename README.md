# AI-Powered-Workplac# WorkMate AI 🤖

**An AI-powered assistant for workplace productivity** by Sinalo Mvo.

🌐 **Live demo:** https://YOUR-PROJECT.vercel.app  ·  📂 **Repo:** https://github.com/YOUR-USERNAME/workmate-ai

WorkMate AI automates everyday office tasks from one clean interface:

| Tool | What it does |
|------|--------------|
| ✉️ Email Generator | Drafts professional emails from purpose, tone and key points |
| 📝 Meeting Summariser | Turns notes/transcripts into summary, decisions and an action-item table |
| 📅 Task Planner | Prioritises tasks (Eisenhower Matrix) and builds a time-blocked schedule |
| 🔎 Research Assistant | Produces structured research briefs and flags what to verify |
| 💬 Chatbot | Conversational assistant with session memory |
| 🛡️ Privacy Shield | Redacts emails, phone, ID and card numbers before sending to the AI |

## Architecture
```
Browser (HTML/CSS/JS)
  └─ PII redaction → prompt template (assets/js/prompts.js)
        └─ POST /api/chat  (serverless, key hidden, rate-limited)
              └─ Google Gemini  or  OpenAI GPT
```
If no API key is configured, the app automatically runs in **Demo mode** (rule-based engine in `assets/js/demo.js`) so the live site always works.

## Project structure
```
workmate-ai/
├── index.html          # Portfolio / landing page
├── app.html            # The assistant
├── api/chat.js         # Serverless AI proxy (Gemini or OpenAI)
├── assets/css/style.css
├── assets/js/prompts.js  # Prompt library (prompt engineering)
├── assets/js/demo.js     # Offline demo engine
├── assets/js/app.js      # UI logic, redaction, markdown rendering
└── docs/               # PROMPTS.md, ETHICS.md, TESTING.md
```

## Run locally
```bash
npm i -g vercel
cp .env.example .env      # add your Gemini or OpenAI key
vercel dev                # open http://localhost:3000
```
Just want to see the UI? Open `index.html` directly: it runs in Demo mode.

## Deploy (free) on Vercel
1. Push this folder to a new GitHub repo:
   ```bash
   git init && git add . && git commit -m "WorkMate AI v1"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/workmate-ai.git
   git push -u origin main
   ```
2. Go to vercel.com → **Add New Project** → import the repo → Framework: **Other** → Deploy.
3. Project → **Settings → Environment Variables**: add `GEMINI_API_KEY` (free from Google AI Studio). Redeploy.
4. The badge in the app turns green: **● Live AI (gemini)**.

> Netlify/GitHub Pages also work for the static site (Demo mode). Vercel is recommended because it runs `api/chat.js`.

## Prompt engineering
See [`docs/PROMPTS.md`](docs/PROMPTS.md). Techniques: role prompting, step-by-step instructions, delimiters, structured output, few-shot examples, guardrails and per-task temperature.

## Responsible AI
See [`docs/ETHICS.md`](docs/ETHICS.md). Highlights: client-side PII redaction (POPIA-aware), no server-side storage, anti-hallucination rules, prompt-injection resistance, transparency badge, human-in-the-loop, rate limiting.

## AI tools used
- **Google Gemini**: primary model behind the app
- **ChatGPT**: prompt iteration and comparing outputs across models
- **Notion AI / ClickUp Brain**: planning, documentation and presentation drafting

## License
MIT © 2026 Sinalo Mvo
e-Productivity-Assistant
