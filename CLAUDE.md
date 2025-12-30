# CLAUDE.md - Wax Documentation Repository

## Project Overview

Official documentation site for **Wax** - a multi-language (TypeScript, C++, Python) object-oriented API library for the Hive blockchain. Built with Retype static site generator, deployed via GitLab Pages with interactive, executable code examples.

Documentation covers: blockchain API requests, transaction building/signing, asset manipulations (HIVE/HBD/VESTS), encryption, key generation, and multiple signer implementations (Keychain, MetaMask, Beekeeper, PeakVault, HB Auth).

## Tech Stack

- **Static Site Generator:** Retype v3.11.0
- **Package Manager:** pnpm v9.1.1
- **Node:** v20 (CI image)
- **Linting:** markdownlint-cli v0.45.0
- **Git Hooks:** Husky v9.1.7
- **Deployment:** GitLab Pages

## Directory Structure

```
wax-doc/
├── src/                           # Documentation source
│   ├── index.md                   # Homepage
│   ├── closing-note.md            # Resources and closing
│   ├── _includes/head.html        # Custom themes + JS
│   ├── static/
│   │   ├── snippets/              # Git submodule (wax-doc-snippets)
│   │   └── *.svg, *.ico           # Logos and assets
│   └── interfaces/                # Main docs (~40 .md files)
│       ├── getting-started.md
│       ├── api/                   # API configuration
│       ├── signers/               # Keychain, MetaMask, etc.
│       ├── transaction/           # Transaction building
│       ├── asset-manipulations/
│       ├── manabars/
│       ├── encryption/
│       ├── formatters/
│       └── key-generation/
├── retype.yml                     # Retype configuration
├── .markdownlint.jsonc            # Linting rules
├── .gitlab-ci.yml                 # CI/CD pipeline
└── .husky/pre-commit              # Pre-commit linting hook
```

## Development Commands

```bash
# Install dependencies
pnpm install

# Start local dev server (port 5005)
pnpm start

# Build static site (output: .retype/)
pnpm run build

# Run markdown linting (excludes snippets submodule)
pnpm run lint
```

## Key Files

| File | Purpose |
|------|---------|
| `retype.yml` | Site configuration (branding, input/output, snippets) |
| `.markdownlint.jsonc` | Markdown linting rules |
| `.gitlab-ci.yml` | CI/CD pipeline (lint, build, deploy) |
| `src/_includes/head.html` | Custom theming and language persistence JS |
| `src/static/snippets/` | Submodule with executable code examples |

## Coding Conventions

### Markdown Front Matter
```yaml
---
order: -1          # Negative = higher priority in sidebar
icon: home         # Sidebar icon
expanded: true     # Section expanded by default
label: "Title"     # Display name
---
```

### Code Examples
- Use multi-language tabs with `+++` syntax (JavaScript/Python)
- Reference snippets from submodule:
  ```
  :::code source="../../static/snippets/file.ts" language="typescript" title="Test it yourself"
  ```
- Collapsed outputs use `===` syntax

### Callouts
```markdown
!!!primary Title
Content here
!!!

!!!secondary Note
!!!

!!!error Warning
!!!
```

### Linting Rules
- MD041 (first-line-heading): Disabled - Retype allows banner images first
- MD013 (line-length): Disabled - Badges can exceed limits
- MD045 (no-alt-text): Disabled - Retype displays alt text under images
- All other rules enabled

### Git Workflow
- Snippets managed via submodule at `src/static/snippets/`
- Pre-commit hook runs `pnpm run lint` (blocks on failure)
- Commit messages: concise, action-oriented

## CI/CD Notes

**Stages:** lint (.pre) → build → pages (deploy)

**Pipeline Features:**
- Lint runs on all commits
- Build replaces base URL and commit hash placeholders
- Branch previews: non-main branches deploy to `/{branch-slug}/`
- Main branch deploys to root with redirects

**Key Variables:**
```yaml
GIT_SUBMODULE_STRATEGY: recursive  # Includes snippets submodule
```

**Runner Tags:**
- `public-runner-docker` (lint, build)
- `data-cache-storage` (pages deploy)

**Artifacts:** `.retype/` directory, expires in 1 week
