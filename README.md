# forgecode

Forge AI coding agent CLI layer for OpenCharly images.

The `forgecode` candy installs the `forgecode` npm package globally (via
`package.json`, requiring `nodejs`), landing the `forge` CLI on the npm global
bin path at `~/.npm-global/bin/forge`. Forge is an alternative AI coding agent
([forgecode.dev](https://forgecode.dev)) that runs inside the container.

`forge --version` reports its version offline, so the install and bin wiring are
verifiable without network access.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `forgecode` |
| Requires | `layer-nodejs` |
| Binary | `${HOME}/.npm-global/bin/forge` |
| Install files | `charly.yml`, `package.json` |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-forgecode:v2026.243.0408'
```

After the image is built:

```bash
~/.npm-global/bin/forge --version
~/.npm-global/bin/forge --help
```

## Layout

- `charly.yml` — the `forgecode:` candy entity: the `nodejs` require, the
  `check:` assertions, and the embedded `skill:` entity.
- `package.json` — pins the `forgecode` npm package the build installs globally.
- `CHANGELOG/` — per-CalVer release notes.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-coder:forgecode` — the Forge coding-agent CLI
- Runtime parent: `/charly-coder:nodejs`
- Sibling AI CLIs: `/charly-coder:codex`, `/charly-coder:gemini`, `/charly-coder:claude-code`
- Bundled by: `/charly-hermes:hermes-full-layer` (metalayer), `/charly-hermes:hermes` (box)
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
