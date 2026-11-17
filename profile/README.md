<p align="center">
  <img src="assets/avatar.png" alt="millsymills.com" width="120" height="120" />
</p>

<h1 align="center">millsymills.com</h1>

<p align="center">Security engineering · MCP tooling · infrastructure managed as code</p>

---

I'm **Andrew Mills**. I build [Model Context Protocol](https://modelcontextprotocol.io)
servers that give AI agents scoped access to real systems, and I run the
infrastructure behind them the same way I'd secure anything else: declared in
code, reviewed in pull requests, and enforced by CI.

Based in the Pacific Northwest · Remote.

## MCP servers

Each project documents its supported operations, configuration, and write
controls in its own README.

| Server | Stack | What it does |
|--------|-------|--------------|
| [unraid-mcp](https://github.com/millsymills-com/unraid-mcp) | Python · FastMCP | Unraid GraphQL API — array, Docker, VMs, shares. |
| [unifi-mcp](https://github.com/millsymills-com/unifi-mcp) | Python · FastMCP | UniFi Network, Protect, and Site Manager — [current tool inventory](https://github.com/millsymills-com/unifi-mcp#tool-inventory), writes explicitly gated. |
| [gandi-mcp](https://github.com/millsymills-com/gandi-mcp) | Python · FastMCP | Gandi v5 — domains, LiveDNS, email, certificates. Three-tier safety model on writes and purchases. |
| [protonmail-mcp](https://github.com/millsymills-com/protonmail-mcp) | Go | Proton Mail — addresses, custom domains, mail settings, encryption keys. |
| [flipperzero-mcp](https://github.com/millsymills-com/flipperzero-mcp) | Python | Flipper Zero over USB and Wi-Fi protobuf RPC. |
| [shortcut-mcp](https://github.com/millsymills-com/shortcut-mcp) | Python · FastMCP | Shortcut REST API — stories, epics, workflows. |

## Infrastructure

[**millsymills-com-org**](https://github.com/millsymills-com/millsymills-com-org)
declares organization settings, org-wide rulesets, and repository configuration
with OpenTofu, including the management repository itself. Repository content
and CI coverage are maintained in each project.

## How this org is run

- **Infrastructure changes through PRs** — the management repository has
  separate [plan](https://github.com/millsymills-com/millsymills-com-org/blob/main/.github/workflows/tofu-plan.yml)
  and [apply](https://github.com/millsymills-com/millsymills-com-org/blob/main/.github/workflows/tofu-apply.yml)
  workflows using AWS OIDC, plus a scheduled
  [drift check](https://github.com/millsymills-com/millsymills-com-org/blob/main/.github/workflows/tofu-drift.yml).
- **Checks with documented boundaries** — the management repository's
  [gate verification design](https://github.com/millsymills-com/millsymills-com-org/blob/main/docs/adr/0001-gate-bypass-mitigation.md)
  explains the checks and their limits. Each project's workflows show its
  actual lint, test, and security-scanning coverage.
- **Release-signature auditing** — the management repository
  [verifies tag signatures after push](https://github.com/millsymills-com/millsymills-com-org/blob/main/.github/workflows/release.yml).
  Pre-push signed-tag enforcement is
  [planned, not implemented](https://github.com/millsymills-com/millsymills-com-org/issues/36).

## Contact

[millsymills.com](https://millsymills.com) · mills@millsymills.com
