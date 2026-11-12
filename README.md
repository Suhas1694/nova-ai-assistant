# Campus Copilot

A responsive college study assistant built with Next.js. It includes an assignment checklist and an AI chat endpoint. Chat messages live in React state only; this starter does not write them to a database.

## Run locally

1. Install Node.js 20 or newer.
2. Run `npm install`.
3. Copy `.env.example` to `.env.local` and set `OPENAI_API_KEY`. You can optionally set `OPENAI_MODEL`.
4. Run `npm run dev` and open http://localhost:3000.

The OpenAI key is read only by the server route and must never use a `NEXT_PUBLIC_` prefix. Keep `.env.local` out of Git.

## Deploy with GitHub and Vercel

1. Create a GitHub repository and push this project.
2. In Vercel, choose **Add New → Project**, import the repository, and keep the detected Next.js settings.
3. In Vercel **Project Settings → Environment Variables**, add `OPENAI_API_KEY` and optionally `OPENAI_MODEL` for Preview and Production.
4. Deploy. Later pushes to your connected branch trigger new deployments.

## Security and production notes

- API credentials stay server-side. The chat route validates message shape/length, checks same-origin browser requests, caps request volume, and returns generic provider errors.
- Security response headers are configured in `next.config.ts`.
- The included rate limiter is in-memory and resets when a server instance restarts. Serverless deployments can run multiple instances, so use a shared store such as Redis/Upstash for enforceable production limits.
- This demo has no account system, durable assignments, or per-user quotas. Add authentication and authorization before using it with private student data or opening it to the public. Do not enter sensitive personal information into the demo.
- The assistant can be wrong. Verify facts, calculations, and citations against course materials.
- The task list is demo data and resets on refresh. Connect a protected database if you want to save it.
