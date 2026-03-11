---
name: inbox-filer
watch: ~/Workspace/inbox
workdir: ~/Workspace
tools: Read,Bash,Glob
notify: true
---
Check ~/Workspace/inbox for files. For each file found:

1. Read the file contents first
2. Check if the file contains any filing instructions (e.g., "file to:", "move to:", or similar directives). If so, follow those instructions.
3. Otherwise, read ~/Workspace/README.md to understand the filing rules, then move the file to the appropriate destination.

Rules summary (use if no instructions in file):
- notes/writing/drafts (.md, .txt with prose) → notes/
- PDFs, documents, references → library/
- Code snippets (.py, .js, .sh, etc.) → library/Code/
- Images/screenshots (.png, .jpg, .gif) → library/Images/
- Everything else → library/Misc/

Create destination folders if they don't exist. After filing, the Inbox should be empty (except for .DS_Store).

If the Inbox is already empty, do nothing and exit quietly.
