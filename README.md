# comment-cleaner

`comment-cleaner` is a small command-line tool for enforcing a **no-comments-in-code** convention by removing ordinary explanatory comments from source files while preserving comments that have a functional purpose.

## Installation

Make the script executable:

```bash
chmod +x comment-cleaner
```

## Usage

```text
Usage:
  comment-cleaner --check <file-or-directory> [...]
  comment-cleaner --clean <file-or-directory> [...]
  comment-cleaner -- check <file-or-directory> [...]
  comment-cleaner -- clean <file-or-directory> [...]

Examples:
  comment-cleaner --check .
  comment-cleaner --clean .
  comment-cleaner -- check src/foo.ts src/bar.ts
  comment-cleaner -- clean src/foo.ts src/bar.ts
```

Directory arguments are processed recursively through all nested directories.

## Supported files

The cleaner currently supports:

- TypeScript: `.ts`, `.tsx`
- JavaScript: `.js`, `.jsx`, `.mjs`, `.cjs`
- Shell: `.sh`, `.bash`, `.zsh`, `.ksh`, `.fish`
- YAML: `.yaml`, `.yml`
- TOML: `.toml`
- `Dockerfile`
- `Makefile`
- Shell scripts identified by a supported shebang

## Preserved comments

Comments with a functional purpose are preserved, including:

- ESLint directives such as `eslint-disable`
- TypeScript directives such as `@ts-ignore` and `@ts-expect-error`
- `prettier-ignore` directives
- TypeScript triple-slash reference directives
- Webpack, Vite, and Rollup magic comments
- SPDX/license headers
- Generated-file markers such as `@generated` and `DO NOT EDIT`
- Shebangs such as `#!/usr/bin/env bash`

## Excluded

The following common dependency, VCS, build, cache, and vendor directories are skipped automatically:

```text
.git
.hg
.svn
node_modules
dist
build
coverage
.next
.nuxt
.turbo
.cache
.parcel-cache
.vite
target
out
vendor
```
