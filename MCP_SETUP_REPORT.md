# MCP Setup & Agent Configuration Report

## Overview

This repository documents my completion of the **Tenx MCP Setup Challenge** using the **Cursor IDE**.  
The objective was to configure the Tenx MCP analytics server, research and apply best practices for guiding AI coding agents, and document how agent behavior changes when governed by explicit rules.

The work was completed within the assessment time window and emphasizes configuration accuracy, troubleshooting discipline, and reflective documentation.

---

## Task 1: MCP Setup

### IDE Used
- Cursor IDE

### MCP Server Configuration
- Server name: `tenxfeedbackanalytics`
- Transport: HTTP (streamable/SSE)
- Server URL: `https://mcppulse.10academy.org/proxy`
- Configuration file: `.cursor/mcp.json`
- Headers:
  - `X-Device`: `linux`
  - `X-Coding-Tool`: `cursor`

### What I Did
- Created `.cursor/mcp.json` with the required MCP server configuration
- Enabled the Tenx MCP server inside Cursor
- Authenticated successfully via GitHub OAuth
- Verified MCP server discovery and tool availability
- Tested agent interactions to confirm MCP tool invocation attempts

### What Worked
- MCP server was successfully registered and enabled in Cursor
- Authentication via GitHub OAuth completed successfully
- MCP server connected using streamable HTTP (SSE)
- Tool discovery succeeded multiple times:
  - **3 tools** discovered
  - **1 prompt** discovered
- The agent attempted to log interactions using the MCP analytics tool

### Evidence of Successful Connection
Cursor logs showed repeated successful states, including:
- Successful SSE connection
- `listOfferings: Found 3 tools`
- `listPrompts: Found 1 prompts`

These logs confirm that the client-side MCP configuration, authentication, and discovery pipeline were functioning correctly.

### What Didn’t Work
- MCP tool execution intermittently failed due to server-side connection issues
- Errors observed:
  - `Failed to open SSE stream: Bad Gateway`
  - `No valid session ID provided`

### Troubleshooting & Analysis
- Restarted Cursor and re-enabled the MCP server
- Verified configuration values, headers, and server URL
- Observed that failures occurred **after** successful connections and tool discovery
- Determined that the issue was related to **server/proxy session instability**, not local configuration

### Conclusion for Task 1
The Tenx MCP server was correctly configured, authenticated, and actively connected within Cursor.  
The agent successfully discovered MCP tools and attempted tool invocation.  
Subsequent failures were isolated to server-side session or gateway instability, which is outside client control.

**Task 1 is considered successfully completed.**

---

## Task 2: Agent Rules Research & Configuration

### Research Basis
I studied best practices for AI coding agent workflows based on:
- Boris Cherny’s Claude Code workflow discussion
- Community guidance on persistent agent instruction files
- Cursor’s rule-based agent configuration model

Key principles adopted:
- Persistent, version-controlled agent rules
- Planning before execution
- Verification loops
- Minimal diffs and safe operations
- Treating agent rules as a living document

### What I Did
- Added a persistent agent rules file: `.cursor/rules/agent.mdc`
- Enabled `alwaysApply: true` so rules are enforced across sessions
- Defined a structured response format:
  - Understanding
  - Plan
  - Action
  - Verification
- Required verification steps before task completion
- Added safety and minimal-diff guidelines

### Behavior Testing
I tested the agent using controlled prompts (e.g., creating a README).

### What Worked
- The agent consistently followed the defined response structure
- The agent planned before acting
- Verification steps were included without explicit prompting
- The agent avoided inventing tooling or languages

### What Didn’t Work
- Prior to adding rules, agent behavior lacked consistency and verification
- This was resolved after introducing the rules file

### Insights Gained
- Persistent, repo-level rules significantly improve agent predictability
- Explicit verification requirements reduce hallucinations
- Encoding behavioral expectations is more effective than repeated prompting
- Treating rules as a living artifact enables continuous improvement of human–AI collaboratio
