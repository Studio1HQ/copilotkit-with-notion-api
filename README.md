<div align="center">

<img src="https://raw.githubusercontent.com/Studio1HQ/Studio1HQ/main/assets/banners/copilotkit-with-notion-api.webp" alt="Notion Database Copilot with CopilotKit: Query and edit a Notion database by chatting with an AI copilot" width="100%" />

<br />
<br />

# Notion Database Copilot with CopilotKit

### Query and edit a Notion database by chatting with an AI copilot

A Next.js app that shows a Notion database as a table and adds a CopilotKit chat popup. The copilot reads the rows and can update row titles and links through the Notion API.

<br />

[![Built by Studio1](https://img.shields.io/badge/Built_by_Studio1-f97316?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNjAgMTYwIiBmaWxsPSJub25lIj48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTAgMzVDMCAxNi42ODA3IDE0LjA3NDQgMS42NDg0NCAzMiAwLjEyNjk1M1YxNDFINTEuMDUyM0M1Mi40MzA4IDEzNy4zNDQgNTQuNzQ0NiAxMzMuNjg5IDU3Ljk5MzggMTMwLjAzM0M2MS4xNDQ2IDEyNi41MDggNjQuNjg5MiAxMjMuNDQgNjguNjI3NyAxMjAuODI5QzcyLjU2NjIgMTE4LjM0OSA3Ni4zNTY5IDExNi43ODIgODAgMTE2LjEyOVY4Ni43NTQ0Qzc1LjQ3MDggODcuOTI5MiA3MS4zODQ2IDg5LjY5MTkgNjcuNzQxNSA5Mi4wNDE1QzY0IDk0LjUyMjUgNjAuNzUwOCA5Ny40NiA1Ny45OTM4IDEwMC44NTRDNTYuNTM0NSAxMDIuNzIgNTUuMjU0NSAxMDQuNjU5IDU0LjE1MzkgMTA2LjY3MVYwSDEyNUMxNDQuMzMgMCAxNjAgMTUuNjY5OSAxNjAgMzVWMTI1QzE2MCAxNDQuMzMgMTQ0LjMzIDE2MCAxMjUgMTYwSDEyNFYxOEgxMDQuOTQ4QzEwMy41NjkgMjEuNjgxNiAxMDEuMjU1IDI1LjM2MjggOTguMDA2MiAyOS4wNDQ0Qzk0Ljg1NTQgMzIuNTk0MiA5MS4zMTA4IDM1LjY4NDEgODcuMzcyMyAzOC4zMTRDODMuNDMzOCA0MC44MTIgNzkuNjQzMSA0Mi4zODk2IDc2IDQzLjA0NzRWNzIuNjMwNEM4MC41MjkyIDcxLjQ0NzMgODQuNjE1NCA2OS42NzI0IDg4LjI1ODUgNjcuMzA1N0M5MiA2NC44MDc2IDk1LjI0OTIgNjEuODQ5MSA5OC4wMDYyIDU4LjQzMDdDOTkuNDY1NSA1Ni41NTEzIDEwMC43NDUgNTQuNTk4NiAxMDEuODQ2IDUyLjU3MjNWMTYwSDM1QzE1LjY3IDE2MCAwIDE0NC4zMyAwIDEyNVYzNVoiIGZpbGw9IiNmZmZmZmYiLz48L3N2Zz4K)](https://studio1hq.com)
[![Built with CopilotKit](https://img.shields.io/badge/Built_with_CopilotKit-141414?style=for-the-badge)](https://copilotkit.ai)

[CopilotKit docs](https://docs.copilotkit.ai) &nbsp;·&nbsp; [CopilotKit](https://copilotkit.ai) &nbsp;·&nbsp; [More examples](https://github.com/Studio1HQ) &nbsp;·&nbsp; [studio1hq.com](https://studio1hq.com)

</div>

<br />

## Overview

This app connects an AI copilot to a Notion database. The database is shown as a table. A [CopilotKit](https://copilotkit.ai) chat popup gives the model the full table as context, so you can ask questions about your rows. The model can also edit rows, and the change is written back to Notion through the Notion API.

## Features

- **Table context for the model**: `useCopilotReadable` exposes the current rows to the copilot.
- **Read data**: Ask questions about the rows, such as what is due soon or which links are missing.
- **Write data**: The copilot actions `updateRowName` and `updateRowLink` update a row's title or link in Notion. Each takes the row `index` and the new value.
- **Live UI updates**: The table state updates after an edit, and toast messages report success or failure.
- **Typed server config**: Required env variables are validated at startup with `@t3-oss/env-nextjs` and Zod.

## Tech stack

| Layer | Tool |
| --- | --- |
| Framework | [Next.js](https://nextjs.org/) 14, React 18, TypeScript |
| Copilot | [CopilotKit](https://copilotkit.ai) (`react-core`, `react-ui`, `runtime`) |
| Data | [Notion API](https://developers.notion.com/) (`@notionhq/client`) |
| LLM | [OpenAI](https://platform.openai.com/) (`gpt-3.5-turbo` via `OpenAIAdapter`) |
| UI | Tailwind CSS, shadcn/ui table, Sonner toasts |

## Getting started

### Prerequisites

- Node.js and npm
- A Notion database and an internal integration with access to it, from [Notion integrations](https://www.notion.so/my-integrations)
- An [OpenAI API key](https://platform.openai.com/api-keys)

The code expects these database properties: `name` (title), `link` (URL) and `dueDate` (date). Property names are set in `lib/constants.ts`.

### Installation

```bash
git clone https://github.com/Studio1HQ/copilotkit-with-notion-api.git
cd copilotkit-with-notion-api
npm install
cp .env.example .env
```

### Environment variables

| Variable | Description |
| --- | --- |
| `NOTION_SECRET_API_KEY` | Secret key of your Notion integration. |
| `NOTION_DB_ID` | ID of the Notion database to read and edit. |
| `OPENAI_API_KEY` | OpenAI API key used by the CopilotKit runtime. |
| `COPILOTKIT_PUBLIC_KEY` | Optional. CopilotKit public key. |

### Run

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). Other scripts: `npm run build`, `npm run start`, `npm run lint`.

## How it works

- `app/page.tsx` is a server component. It calls `fetchNotionDB` (in `lib/actions.ts`), maps the rows to `name`, `link` and `dueDate`, and renders `NotionTable`.
- `app/layout.tsx` wraps the app in `CopilotKit` with `runtimeUrl="/api/copilotkit"` and adds a `CopilotPopup` with instructions to answer from the database content.
- `app/api/copilotkit/route.ts` creates a `CopilotRuntime` with an `OpenAIAdapter` (`gpt-3.5-turbo`).
- `components/notion-table.tsx` registers the readable and the two actions. The actions call the server actions `updateNotionDBRowTitle` and `updateNotionDBRowLink`, which use `notion.pages.update`.

## Resources

- [CopilotKit docs](https://docs.copilotkit.ai): readables, actions and the runtime.
- [CopilotKit](https://copilotkit.ai): the copilot framework used here.
- [Notion API docs](https://developers.notion.com/): integrations and database queries.
- [Notion](https://notion.so): the database provider.

## License

Released under the [MIT License](LICENSE).

<br />

---

<div align="center">

<a href="https://studio1hq.com">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-dark.svg" />
    <img src="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-light.svg" alt="Studio1" width="160" />
  </picture>
</a>

Built by **[Studio1](https://studio1hq.com)**, the technical content and DevRel partner for devtool teams. Made with [CopilotKit](https://copilotkit.ai).<br />
Browse more open-source examples at [github.com/Studio1HQ](https://github.com/Studio1HQ).

[![Website](https://img.shields.io/badge/studio1hq.com-0b0807?style=for-the-badge&logo=googlechrome&logoColor=white)](https://studio1hq.com)
[![Book a call](https://img.shields.io/badge/Book_a_strategy_call-f97316?style=for-the-badge&logo=googlecalendar&logoColor=white)](https://cal.com/studio1/collab)
[![X](https://img.shields.io/badge/%40Studio1HQ-141414?style=for-the-badge&logo=x&logoColor=white)](https://x.com/Studio1HQ)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/studio1hq/)

<sub><a href="https://studio1hq.com">studio1hq.com</a> · Technical content, docs, video and DevRel for devtools</sub>

</div>
