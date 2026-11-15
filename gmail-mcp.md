---
layout: default
title: Local Gmail MCP
permalink: /gmail-mcp/
---

# Local Gmail MCP

A personal, locally-run tool that lets a command-line coding agent read and
manage **my own** Gmail mailbox through Google's official Gmail API.

It is not a product, a service, or anything other than a personal tool for my
own use on my own machine. There are no other users.

## What it does

- Search, read, label, archive and draft my mail
- Send mail on my behalf when I ask it to
- Create the Gmail filters I ask for
- Keeps a local, append-only log of every action it takes

## How it is accessed

OAuth 2.0, with the Gmail API, requesting two permissions: `gmail.modify` and
`gmail.settings.basic`. It deliberately does **not** request `mail.google.com`,
the only scope that would permit permanently deleting mail.

## Where my data goes

The tool has no server, no analytics and no telemetry. It talks to Google's
APIs and keeps its credentials, logs and downloaded files in `~/.gmail-mcp/`
with owner-only filesystem permissions. Mail that the coding agent reads is
passed to the agent's AI model provider for processing, under that provider's
terms.

## Read more

- **[Privacy Policy](/gmail-mcp/privacy/)** — the full details
- [Back to my homepage](/)
