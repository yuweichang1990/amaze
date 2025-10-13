# Suggested Slash Command Interface (Tool-agnostic)

These flags are **suggested**. Your platform can map them to its own options.

```
/reverse-analyze   --repo .   --round 0|1|2   --level 0|1|2|3[,2|3...]   --focus "parser,api"   --depth 2   --exclude "node_modules/**,dist/**,build/**,.git/**,vendor/**"   --file-limit 8000   --max-file-size 1.5MB   --timebox "structure=10m,api=10m,vcs=10m"   --run-tests   --resume specifications/R1/checkpoint.json   --read-only true   --output ./specifications
```

**Defaults**
- `--round 0`
- `--level 2`
- `--repo .`
- `--read-only true`
- **no build / no tests**

**Fallback**
- On timeout/limits, **downgrade** (e.g., deliver L1/L2 only) and record gaps in `assumptions.md`.

## Common Iterative Scenarios

After R2 analysis completes, the prompt will guide next steps. Here are typical iteration commands:

### Selective Re-analysis
```
/reverse-analyze --round 1 --focus "auth,payment" --resume "specifications/R2/checkpoint.json"
```

### Full Round Repeat
```
/reverse-analyze --round 1 --resume "specifications/R2/checkpoint.json"
```

### Major Revision
```
/reverse-analyze --round 0 --resume "specifications/R2/checkpoint.json"
```
