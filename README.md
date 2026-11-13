# Total Recall

Total Recall connects AI agents to Life OS, a personal system for managing
tasks, notes, projects, and memories. It helps agents find and use that
information.

The connection uses the Model Context Protocol (MCP). MCP gives agents a way
to discover and call tools. Total Recall sends those requests to Life OS. Life
OS stores the information and handles memory approval.

## How it works

Total Recall offers two tools:

- `search` finds Life OS actions that match a request. It does not return saved
  records.
- `execute` runs the actions found by `search`. It can return records or a
  proposal for review.

For example, an agent can search for a way to save a preference. Then it can
ask Life OS to create a proposal. A person reviews the proposal in Life OS.

## Run locally

You need Node.js 24, pnpm 10, and access to a Life OS service. The service must
accept requests from Total Recall.

1. Install the packages:

   ```sh
   pnpm install
   ```

2. Copy `.dev.vars.example` to `.dev.vars`.
3. Set `TOTAL_RECALL_TOKEN`, `LIFE_OS_BASE_URL`, and `LIFE_OS_SERVICE_TOKEN` in
   `.dev.vars`. Use a private token for each token field.
4. Run the service:

   ```sh
   pnpm dev
   ```

The MCP endpoint is `/mcp`. An MCP client must send an access token. Total
Recall accepts the configured `TOTAL_RECALL_TOKEN` or a valid Life OS OAuth
access token. The client needs the right scope for each tool.

Keep both tokens private. Do not commit `.dev.vars` or put tokens in chat. See
[SECURITY.md](SECURITY.md) for token guidance.

## Run the project checks

Run all checks from the project folder:

```sh
pnpm verify
```

This command runs the format, lint, type, test, and API contract checks.
Lefthook also checks commit messages. Use a Conventional Commit message such as
`fix: correct search results`.
Release Please creates release pull requests from commits on `main`.

## Learn more

- [Life OS memory API](docs/life-os-memory-api.md) describes memory proposals.
- [MCP mental model](learning/mcp-mental-model.md) explains MCP terms.
- [Memory taxonomy](learning/memory-taxonomy.md) describes kinds of memory.
