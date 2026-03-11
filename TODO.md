# TODO

## Build/install step

Need a build or install step that compiles the workspace for each environment — resolving paths, setting up symlinks, and injecting environment-specific config (e.g. workspace path). Right now `~/Workspace` and `~/.openclaw/workspace` are hardcoded in AGENTS.md; skills use `<workspace_dir>/` as a placeholder. A build step could replace these with actual paths per environment, or generate a config file that the agent reads at runtime.
