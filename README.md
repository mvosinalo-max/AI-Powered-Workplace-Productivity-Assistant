# AI Workplace Buddy

AI-powered workplace productivity assistant by **Sinalo Mvo**.

Features: chat assistant (multiple conversations, stored only in the browser, clear-history), email writer, meeting summariser, task planner, research assistant.

Tech: React + TanStack Start, Tailwind CSS, Vercel AI SDK, Lovable AI Gateway (OpenAI GPT model).

- Prompts: `src/lib/ai/prompts.server.ts`
- AI endpoints: `src/routes/api/chat.ts`, `src/routes/api/generate.ts`
- Pages: `src/routes/`

Run locally: `bun install && bun run dev` (requires `LOVABLE_API_KEY` on the server).
