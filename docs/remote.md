# Remote Server

DigitalOcean droplet running OpenClaw agent.

## Connection Details

- **Host:** 137.184.178.195
- **DNS:** bot.ruperts.world
- **User:** root
- **SSH:** `ssh root@137.184.178.195`
- **Sandbox:** Outbound SSH is blocked by default sandbox. Always use `dangerouslyDisableSandbox: true` for SSH commands.
- **Host key:** Already added to `~/.ssh/known_hosts`

## Server Layout

- **OS:** Ubuntu (Digital Ocean droplet)
- **Agent:** OpenClaw
- **Workspace:** `~/.openclaw/workspace/`
  - `.git/` — git-tracked
  - `.clawhub/`, `.openclaw/` — OpenClaw internals
  - `AGENTS.md`, `HEARTBEAT.md`, `IDENTITY.md`, `SOUL.md`, `TOOLS.md`, `USER.md` — agent config files
  - `docs/` — documentation
  - `history/` — conversation/event history
  - `memory/` — agent memory
  - `notes/` — notes (large directory, 17 subdirs)
  - `opt/` — optional packages/tools
  - `skills/` — agent skills

## Usage

1. For single commands: `ssh root@137.184.178.195 '<command>'`
2. For file transfer: `scp` or `rsync` with the same credentials
3. Always use `dangerouslyDisableSandbox: true` on Bash calls involving SSH/SCP/rsync to this host

## Notes

- The droplet is running an OpenClaw agent that may be actively writing to the workspace
- Be cautious about overwriting files the agent may be using
- Sync: stash (`github:rupertsworld/agents`) for skills, docs, logs
