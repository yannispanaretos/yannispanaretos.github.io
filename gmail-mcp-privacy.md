---
layout: default
title: Privacy Policy — Local Gmail MCP
permalink: /gmail-mcp/privacy/
---

# Privacy Policy — Local Gmail MCP

**Last updated: 13 November 2026**

This policy describes how *Local Gmail MCP* ("the tool") handles data. The tool
is a personal, locally-run program used by
[Ioannis Panaretos](https://yannis.panaretos.com/) to read and manage his own
Gmail mailbox from a command-line coding agent. It is not a commercial
service, is not available to the public, and has no users other than its owner.

## What the tool does

The tool connects to Google via the official **Gmail API** using the **OAuth 2.0**
protocol. It can read, search, label, draft and send mail on the owner's
account, and can create the mail filters the owner asks for.

It requests exactly two permissions:

| Permission | Why it is needed |
|---|---|
| `gmail.modify` | Read mail, manage labels, archive or trash messages, create and send mail and drafts. |
| `gmail.settings.basic` | Create and manage Gmail filters (the owner's own rules for sorting mail). |

It deliberately does **not** request the `mail.google.com` scope, which is the
only scope that would allow permanently deleting messages rather than moving
them to Trash.

## Where your data goes

**Nowhere.** All mail and all credentials stay on the machine the tool runs on.

- Mail content is read directly from the Gmail API over an encrypted
  (HTTPS/TLS) connection to Google, and is held only in the running process's
  memory and in the local audit log described below.
- The tool has no server, no analytics, no telemetry, and no third-party
  service of any kind. It makes no network request other than to Google's
  APIs.
- The tool does not send mail anywhere except to the Gmail account itself and
  to the recipients the owner explicitly asks it to write to.

## What is stored locally, and where

| Item | Location | Protection |
|---|---|---|
| OAuth client credentials | `~/.gmail-mcp/<profile>/gcp-oauth.keys.json` | Directory `0700`, file `0600` (owner read/write only) |
| OAuth access & refresh tokens | `~/.gmail-mcp/<profile>/credentials.json` | Directory `0700`, file `0600` |
| Audit log of tool calls | `~/.gmail-mcp/<profile>/audit.jsonl` | File `0600`; records tool names and outcomes, with sensitive values redacted |
| Downloaded mail & attachments | `~/.gmail-mcp/<profile>/downloads/`, `~/.gmail-mcp/<profile>/attachments/` | Directory `0700` |

Each Gmail account the owner connects ("profile") gets its own separate
directory, so the accounts never share tokens, logs or state.

The OAuth refresh token is the credential that grants ongoing access. It is
stored unencrypted on the owner's own machine, protected by filesystem
permissions, and can be revoked at any time — see below.

## Sharing

None. The tool shares nothing with the owner, with Google beyond the API calls
the permissions above describe, or with anyone else. Google receives the
requests the tool makes and applies its own
[Privacy Policy](https://policies.google.com/privacy) to them.

## Retention and deletion

- The tool retains no copy of the owner's mail beyond what the owner chooses to
  download, and what the audit log records about which tools were called.
- Deleting `~/.gmail-mcp/` removes every local credential, log and downloaded
  file the tool has created.
- Revoking access is done through Google's own controls:
  [myaccount.google.com/permissions](https://myaccount.google.com/permissions).
  Revoking there immediately invalidates the stored refresh token, and the tool
  stops being able to read or send mail on that account.

## Children

The tool is not directed at children and collects no information from anyone.

## Changes to this policy

If the tool's behaviour changes, this page is updated to match. The "last
updated" date at the top always reflects the current version.

## Contact

Questions about this policy or the tool can be sent to
[yannis.panaretos@gmail.com](mailto:yannis.panaretos@gmail.com).
