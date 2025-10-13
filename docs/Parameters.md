# Parameters (Reference)

| Flag | Type | Default | Notes |
|------|------|---------|-------|
| `--repo` | string | `.` | Root directory to analyze. |
| `--round` | {0,1,2} | `0` | R0 coarse / R1 focused / R2 convergence. |
| `--level` | set {0,1,2,3} | `2` | C4-like: L0 Context, L1 Container, **L2 Component**, L3 Code. |
| `--focus` | CSV | `[]` | Focus modules/components (R1+). |
| `--depth` | int | `2` | Call chain expansion depth; use 3–4 in R1. |
| `--exclude` | globs | common | `"node_modules/**,dist/**,build/**,.git/**,vendor/**"` |
| `--file-limit` | int | `8000` | Max files to scan. |
| `--max-file-size` | size | `1.5MB` | Per-file size limit. |
| `--timebox` | kv | `structure=10m,api=10m,vcs=10m` | Upper bounds per phase. |
| `--run-tests` | flag | `false` | Only in sandbox; run minimal **smoke** per focus module. |
| `--resume` | path | — | Resume from a checkpoint file. |
| `--output` | path | `./specifications` | Output directory. |
| `--read-only` | bool | `true` | Do not modify source files. |

**Sandbox rule**: Only run builds/tests **if** a trusted sandbox is detected or `--run-tests` is set.
