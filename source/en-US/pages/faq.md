---
slug: faq
title: Frequently Asked Questions
excerpt: Common questions about the TPWFC project architecture, tech stack, and development workflow.
---

# Frequently Asked Questions (FAQ)

Welcome to **TPWFC (Tai Po Wang Fuk Court Fire Documentation Project)**. This document aims to answer common questions about the project's architecture, tech stack, and development workflow.

## 📌 Project Overview

### What is the goal of this project?

Our primary goal is to establish a permanent, objective, and transparent historical archive for the **2025 Tai Po Wang Fuk Court Fire**. We are dedicated to preserving the truth, promoting public safety through data analysis, and providing a digital memorial space.

Additionally, this project serves as a high-quality Full-stack Template for reference, enabling developers to build more secure and maintainable applications during "Vibe Coding".

### Is this an official government website?

**No.** This is a civilian-initiated open-source project and is not affiliated with the HKSAR Government, Fire Services Department, or Hong Kong Police Force.

---

## 🛠️ Tech Stack

### Why Next.js 16?

We use Next.js 16 (App Router) for its robust Server-Side Rendering (SSR) capabilities, which are crucial for SEO and initial load performance. It also integrates seamlessly with our chosen CMS, Payload CMS 3.

### Why Payload CMS 3?

Payload CMS 3 is a headless content management system that offers a flexible admin interface and a powerful GraphQL API. Version 3 is Next.js native, allowing us to run the CMS and the frontend website within the same application instance, significantly simplifying deployment.

### Why SQLite?

We utilize `@payloadcms/db-sqlite` to simplify the architecture and enhance portability. Since this is a "read-heavy" documentation site, SQLite provides excellent performance without the need to maintain a separate database server (like PostgreSQL or MongoDB). Furthermore, using SQLite allows the database file to be committed to the repository or easily synced in local development environments.

### Why Go for the Worker Service?

The Worker Service handles high-concurrency tasks, such as simultaneously crawling multiple web sources and processing large amounts of text data. Go (Golang) was chosen for its high performance, strong type system, and excellent concurrency model (Goroutines).

### Why Biome instead of ESLint/Prettier?

We use [Biome](https://biomejs.dev/) for code linting and formatting. It is significantly faster than the traditional ESLint + Prettier combination and offers a unified toolchain for web development.

---

## 🚀 Quick Start & Development

### How to start the development server?

1. Install dependencies: `bun install`
2. Setup environment variables: `cp .env.example .env`
3. Initialize and seed the database: `bun run db:reset-seed`
4. Start the server: `bun dev`

### How to log in to the Admin Panel?

After running `bun run db:reset-seed` or `bun run seed:admin`, you can visit `http://localhost:3000/admin` and log in with:

- **Email:** `admin@example.com`
- **Password:** `changeme123`

### How to run the Go Worker?

Please navigate to the `worker/` directory and use `Makefile`:

- Build all binaries: `make build`
- Run the full pipeline: `make run-worker ...` (See `worker/README.md` for parameters)

### Which package manager should I use?

We strictly use **Bun** (`bun`) to install dependencies and run scripts. Although some internal scripts in `package.json` might mention `pnpm`, `bun` handles the execution.

---

## 📝 Content Management

### How is content stored?

- **Structured Data (Events, Timeline):** Stored in the SQLite database via Payload CMS.
- **Narrative Content (Pages, Articles):** Typically originates from **Markdown** files in the `data/source/` directory. These files are treated as the "Single Source of Truth" and are synced to the CMS.

### How to edit content?

1. **CMS:** You can edit directly in the Admin Panel (`/admin`).
2. **Markdown:** You can edit Markdown files in `data/source/` and then run the `Normalizer` + `Uploader` Worker components to sync changes to the CMS.

### How does "Sync" work?

The Go Worker pipeline (`Crawler` -> `Normalizer` -> `Uploader`) reads raw data (web sources or local Markdown), converts it into a standardized JSON format, and finally uploads it to Payload CMS via the GraphQL API.

---

## ⚠️ Troubleshooting

### `Error: P1001: Can't reach database server`?

Since we use SQLite, this usually indicates a file permission error or an incorrect path. Ensure the `payload.db` file exists in the root directory, or try re-running the Seed script.

### `Biome` errors during commit?

We enforce strict code style. Please run `bun run format` to automatically fix formatting issues.

### Tests failed?

- **E2E Tests:** Ensure the development server is running, or let Playwright start it automatically.
- **Integration Tests:** Check if the test database is clean.

---

## 🤝 Contributing

### How can I contribute?

- **Code:** Check out our [GitHub Repository](https://github.com/TPWFC).
- **Data/Content:** Join our Discord server to submit corrections or new information.

### Where is the Design System?

We use **Tailwind CSS 4** with **Shadcn UI**. Components are located in the `src/app/(frontend)/components/` directory.

<!-- METADATA_START
VALIDATION: TRUE
LAST_MODIFY: 2025-12-25T13:21:09Z
HASH: 5346b21420085e1f6c6cd1a6b2461d5bfc1449f9f25a07bb799bdfda682bdc83
METADATA_END -->
