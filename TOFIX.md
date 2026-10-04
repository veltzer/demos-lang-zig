# TOFIX

Findings from a code scan on 2026-10-04.

## Medium

- `README.md:2` - the repo is named "Demos for the zig programming language" but contains no Zig code at all (only `LINKS.txt` with a single getting-started URL). Add actual `.zig` demos (and a processor that checks them, e.g. `zig fmt --check` / `zig build-exe`) or describe the repo honestly as a placeholder.
- `rsconstruct.toml:1` - `tera.templates/.github/dependabot.yml.tera` is committed but there is no `[processor.tera]` section, so the template is never rendered and `.github/dependabot.yml` can silently drift from it. Add `[processor.tera]` with `src_dirs = ["tera.templates"]` (and the `config/*.lua` it needs as `dep_auto`) like the other templated repos.

## Low

- `README.md:2` - typo "langauge"; the line also differs from `config/project.lua:3`. Better: switch to the fleet `tera.templates/README.md.tera` (used by most demos-lang-* repos) so README is generated from `config/project.lua`, which would also require adding `config/personal.lua` and `config/version.lua`.
- `LINKS.txt:1` - a lone `.txt` link file that no processor checks; fold it into the README (where rumdl and link checks apply) or into a `doc/` folder consistent with sibling repos.
