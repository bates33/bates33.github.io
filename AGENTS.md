# AGENTS.md

## Cursor Cloud specific instructions

This is a Hugo static site blog (PaperMod theme). No Node.js, databases, or backend services are needed.

### System dependency

- **Hugo Extended v0.155.2** must be installed (not available via apt; installed from the `.deb` from GitHub Releases). The update script handles this automatically.

### Key commands

| Task | Command |
|------|---------|
| Dev server | `hugo server --buildDrafts` (serves at `http://localhost:1313/`) |
| Production build | `hugo --gc --minify` |
| New post | `hugo new content posts/<slug>.md` |

### Gotchas

- The PaperMod theme is a **git submodule** at `themes/PaperMod/`. If the directory is empty, run `git submodule update --init --recursive`. The update script handles this.
- Hugo's dev server has **live reload** built in; file changes are reflected instantly without restart.
- Blog images reference an external Cloudflare R2 CDN (`static.bybates.com`). Images will appear broken locally but this does not affect site functionality or builds.
- The site language is Chinese (`zh-cn`). Front matter uses YAML format (see `README.md` for template).
- Do **not** edit files inside `themes/PaperMod/`; use `layouts/` and `assets/css/extended/` for overrides.
