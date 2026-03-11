---
name: comms
description: >
  Send and read messages via Beeper (bridged messaging).
  Use when the user wants to send a message, check messages, reply to someone,
  or says "text", "message", "send", "check messages", "reply to".
---

# Comms

Send and read messages through Beeper, which bridges SMS, iMessage, WhatsApp, Signal, and other platforms into one interface.

## Prerequisites

- Beeper Desktop must be installed and running locally.
- The Beeper Desktop API must be enabled: Settings → Developers → toggle "Beeper Desktop API".
- The Beeper MCP server should be registered with Claude Code (runs on `http://localhost:23373/v0/mcp`).

If the MCP tools are not available, check that Beeper Desktop is running and the API is enabled.

## Usage

Use the Beeper MCP tools directly — search for them with ToolSearch (e.g., query "+beeper") to discover available operations like listing chats, reading messages, and sending messages.

## Workflow

1. **First use:** Verify Beeper MCP tools are available via ToolSearch. If not, check prerequisites above.
2. **Sending:** Confirm the message content and recipient with the user before sending. Never send without confirmation.
3. **Reading:** Summarize messages concisely. Don't dump raw output — present the key content.
4. **Replying:** When the user says "reply to X", find the relevant chat, show recent context, draft a reply, and confirm before sending.

## Notes

- Refer to any provided documentation for contact details and preferences.
- Never send messages without explicit user confirmation.
- The Beeper API is local-only — Beeper Desktop must be running.
