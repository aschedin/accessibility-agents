# Locked-down fork

Based on [Community-Access/accessibility-agents](https://github.com/Community-Access/accessibility-agents)
at commit `a538edc9edfb98cdd8bae96d6b79542874b478f7`.

## What is different

- Removed the five `glow_*` tools, which could upload files to an outside service.
- Removed `scan_uploaded_document`, `extract_document_images`,
  `write_document_alt_text` and `get_specialist`, which served remote chat
  clients. The first three could fetch any public web link.
- Removed `mcp-server/server.js`, the HTTP server for hosting; the plugin does not
  use it.
- The edit gate now also watches the PowerShell tool.
- Marketplace renamed to `aschedin-a11y`; version `7.1.0-locked.1`.

## What can still reach the network

The `run_axe_scan` and `run_playwright_*` tools load the address they are given
in a local browser. They do nothing unless you install Playwright.

## Limits

The edit gate is a reminder, not a security boundary: it does not see every way
a shell command can write a file. Upstream docs and tests still mention the
removed tools; they were not updated.

## Taking upstream updates

Review the changes before merging them, and bump the version afterwards.
