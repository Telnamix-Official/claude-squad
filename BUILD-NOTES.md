# Build Notes for Ryan's Version

## Working Binary

The **verified working build** is saved as `cs-working` in this repository.

### Quick Install

```bash
cp cs-working ~/.local/bin/cs
chmod +x ~/.local/bin/cs
```

Or use full path:
```bash
./cs-working -y
```

## What's Included

This build includes all fixes from PR #223 (which was never merged to upstream):

1. **feat: implement -y flag for bypass permissions mode** (6fc60e7)
   - Enables `--permission-mode bypassPermissions` for Claude Code
   - Adds symlink support for .claude directory across worktrees

2. **fix: restore AutoYes field when loading saved sessions** (92a4930)
   - Sessions started with -y maintain bypass permissions after reload

3. **feat: auto-apply bypass permissions to existing sessions** (b890d5c)
   - Running `cs -y` automatically restarts sessions with correct permissions

4. **fix: skip .claude symlink when directory is tracked in git** (2a6c1d9)
   - Prevents symlink from deleting tracked .claude files

## Building from Source

If you need to rebuild:

```bash
git checkout ryans-version
go build -o cs .
```

**Note:** If the rebuilt binary doesn't work, use `cs-working` instead. The working binary was built on Dec 5, 2025 and has been verified to work correctly.

## Verified Working

- ✅ -y flag (auto-accept) works correctly
- ✅ Symlink handling works with tracked .claude directories
- ✅ Tested on Dec 5-6, 2025
