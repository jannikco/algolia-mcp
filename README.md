# Algolia MCP server

Inspect available indices and query a chosen product index to review search relevance.

A direct-provider MCP server with useful local execution. No PipMCP account is required for local use. Provider API access and any provider charges are your responsibility.

## Quick start

Requires Node.js22+. Clone this repository, then run:

```sh
npm ci --ignore-scripts
npm test
npm start
```

The default command inspects the tools offline. Configure your own credentials in your environment:

- `ALGOLIA_API_KEY`
- `ALGOLIA_APP_ID`
- `ALGOLIA_APP_ID`



Credential help: https://raw.githubusercontent.com/algolia/api-clients-automation/main/specs/bundled/search.yml

## Execute a real read

Replace example record IDs with records you are authorized to access.

```sh
npm start -- --call list_indices '{}'
```

## Use with an MCP client

Launch `node /absolute/path/algolia-mcp/server.mjs` using stdio transport; pass credentials through the client environment. Stdout is reserved for JSON-RPC.

## Tools

| Tool | Effect | Purpose |
| --- | --- | --- |
| list_indices | Read | List Algolia indices using a key with listIndexes permission. |
| search_index | Read | Search one index without modifying its records. |

## Concrete workflow

Inspect available indices and query a chosen product index to review search relevance.

1. list_indices
2. search_index

## Optional writes

Writes are disabled by default. Set CONNECTOR_ALLOW_WRITES=true and supply `_approval: {approved:true,idempotencyKey:"unique-request-id"}` on the specific call. Do not reuse a key for a different request. Uncertain outcomes are never automatically replayed; inspect the provider before another attempt.

## Capability evidence

Local: **Tested — HTTP fixtures and real stdio tools/call**. Managed: **Documented**. Provider authentication and live operations have not been established by these fixture tests. Evidence applies per operation and execution mode; setup discovery does not imply provider execution.

## Managed production

[Activate with PipMCP](https://pipmcp.com/github/start?app=algolia&integration=algolia-mcp&utm_source=github&utm_campaign=github-algolia-mcp&utm_content=readme) when you want the hosted service.  Local credentials are not uploaded by this code. Review provider permissions in the managed onboarding. [Directory and related projects](https://jannikco.github.io/pipmcp-connectors/integrations/algolia/).

## Provenance and maintenance

- https://raw.githubusercontent.com/algolia/api-clients-automation/main/specs/bundled/search.yml

Maintainer:jannikco. MIT license for this code. See connector.json for selected operations and integration.json for evidence. Runtime dependencies retain their own licenses. Report sensitive issues through https://pipmcp.com/contact; do not post credentials or customer data in public issues.
