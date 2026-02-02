# Assessment Checklist

Use this checklist to track your progress through the assessment tasks.

## Task 1: MCP Setup
- [ ] Create `.cursor/mcp.json` configuration file
- [ ] Add Tenx MCP server with correct URL and headers
- [ ] Enable MCP server in Cursor settings
- [ ] Authenticate via GitHub OAuth
- [ ] Verify connection: Check Cursor logs for "Found 3 tools"

**Quick verify:**
```bash
cat .cursor/mcp.json  # Should show tenxfeedbackanalytics config
```

## Task 2: Agent Rules Configuration
- [ ] Create `.cursor/rules/agent.mdc` file
- [ ] Set `alwaysApply: true` in frontmatter
- [ ] Define structured response format (Understanding → Plan → Action → Verification)
- [ ] Add safety and verification requirements
- [ ] Test agent behavior with a simple prompt

**Quick verify:**
```bash
cat .cursor/rules/agent.mdc | head -10  # Should show YAML frontmatter
```

## Task 3: Documentation
- [ ] Document MCP setup process and results
- [ ] Document agent rules experiments and observations
- [ ] Include what worked, what didn't, and troubleshooting steps
- [ ] Commit and push all changes

**Quick verify:**
```bash
git status  # Should show tracked documentation files
```
