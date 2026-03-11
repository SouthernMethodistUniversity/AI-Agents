---
# Start YAML frontmatter; OpenCode reads agent config from this block.

description: "Super agent with broad access; heavily commented reference file" # Required field; short human-readable summary of what this agent is for.

mode: primary # Use this as the main selectable agent; best fit for a full-power “super agent”.

hidden: false # Keep visible in agent lists; hidden would make less sense for a primary all-purpose agent.

disable: false # Must stay false; true would turn the entire agent off.

model: openai/gpt-5 # Example model identifier; replace with your real provider/model if needed.

temperature: 0.2 # Low-ish creativity; raise for brainstorming, lower for consistency.

top_p: 1.0 # Full token distribution; leave at 1.0 unless you specifically tune sampling.

steps: 64 # High step budget for longer tasks; reduce if you want tighter / cheaper runs.

color: accent # UI color tag; purely visual, safe to change to a hex or another theme color.

prompt: "{file:./prompts/super-agent.md}" # Optional external prompt file; remove this line if you keep all prompt text in the Markdown body.

tools: # Legacy compatibility section; still supported, but permissions are the modern standard.
  write: true # Allow creating new files; turn off for planning-only or review-only agents.
  edit: true # Allow modifying existing files; turn off for read-only analysis agents.
  patch: true # Allow applying patches; turn off if you want edits only through normal file operations.
  bash: true # Allow shell commands; turn off for safer or more locked-down agents.
  webfetch: true # Allow fetching web content; turn off for offline-only or privacy-sensitive work.
  read: true # Allow reading files; usually leave on unless you are doing something very unusual.
  grep: true # Allow content search; useful for codebase discovery and investigation.
  glob: true # Allow pattern-based file matching; useful for finding files by name/path shape.
  ls: true # Allow directory listing; almost always useful.
  skill: true # Allow the native skill tool; turn off if you do not want reusable skills loaded.
  mymcp_*: true # Example wildcard for MCP/custom tools; replace with real names or remove if unused.

permission: # Modern control surface; this is what OpenCode now prefers over legacy tool booleans.
  edit: allow # Allow file edits without approval; change to ask for guardrails, deny for read-only.
  webfetch: allow # Allow web fetches automatically; change to ask if you want review before network access.
  skill: # Control which skills can be loaded when the skill tool is enabled.
    "*": allow # Allow all skills by default; tighten this if you want curated skill access only.
    "internal-*": allow # Example explicit wildcard; redundant when * is allow, shown here for format reference.
    "experimental-*": allow # Another pattern example; change to ask if you want approval for risky skills.

  bash: # Command-level shell permission map; more specific patterns override broad ones in practice.
    "*": allow # Allow all shell commands by default; this is the true “everything on” setting.
    "git push": allow # Explicit example of a sensitive command; set to ask or deny if you want safety.
    "rm *": allow # Explicitly allowed here only to demonstrate format; in real use this is often ask or deny.
    "npm publish": allow # Another high-risk example; keep allow only if you intentionally want zero-friction release power.
    "cargo publish": allow # Same idea; demonstrates command-specific entries.
    "docker *": allow # Wildcard command pattern example.
    "kubectl *": allow # Wildcard example for infra workflows.
    "ssh *": allow # Network/remote command example; usually ask in stricter setups.

  task: # Controls delegation to other agents / task-style invocations.
    "*": allow # Allow all task routing / delegation; most permissive setting.
    "review-*": allow # Explicit example pattern; redundant with * allow, shown for formatting reference.
    "docs-*": allow # Another explicit pattern example.
    "security-*": allow # Another explicit pattern example.

reasoningEffort: high # Provider-specific passthrough example; useful for models/providers that support reasoning controls.

textVerbosity: low # Another provider-specific passthrough example; adjust only if your provider supports it.

# maxSteps: 64 # Legacy-style idea shown commented out; prefer steps above if your setup uses current docs.

# End YAML frontmatter; everything below is ordinary Markdown body content.

---

# Super Agent <!--Markdown body starts here; this is the agent’s instruction content area.-->

This agent is configured as a broad-access primary agent. <!--Short body text example; keep or replace as needed.-->

## Notes <!--Normal Markdown heading; body can be any valid Markdown.-->
- Uses permissive permissions for file edits, shell, web access, and skills. # Brief summary of what is enabled.
- Uses legacy `tools` booleans for compatibility and readability. # Helpful because tools are deprecated but still supported.
- Uses explicit examples for wildcard and command-pattern formatting. # Included so you can copy/paste smaller pieces later.
