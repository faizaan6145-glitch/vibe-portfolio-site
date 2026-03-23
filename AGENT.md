# Setup Notes (Node.js / npm PATH issues)

## Problem summary
In PowerShell terminals inside Cursor, `npm` was failing with:
`The term 'npm' is not recognized ...`

After Node.js was installed, `C:\Program Files\nodejs\npm.cmd` and `node.exe` existed, but:
`where.exe npm` and `where.exe node` still returned nothing (so `npm`/`node` were not on the terminal PATH).

When running via full path (`npm.cmd`), `npm` could start but then failed with:
`"node" is not recognized ...`

## Temporary solution (works now)
Run these in the same Cursor PowerShell terminal where you want to start the site:

```powershell
# Add Node.js to PATH for this terminal session only
$env:Path = "$env:Path;C:\Program Files\nodejs"

# (Optional) verify Node works
node -v

# Start Astro dev server
& "C:\Program Files\nodejs\npm.cmd" run dev
```

If you prefer not to set PATH, this can also work for some setups:
```powershell
& "C:\Program Files\nodejs\npm.cmd" run dev
```
But if you see `"node" is not recognized`, use the session PATH method above.

## Why this happens
- Node.js is installed, but your PowerShell terminals don’t have `C:\Program Files\nodejs` on their PATH by default.
- Even when you run `npm.cmd` by full path, some internal steps call `node` by name, so it still needs to be found on PATH.

## Permanent solution (fix for all new terminals)
Add Node.js to the Windows PATH so `npm` and `node` work everywhere:

1. Open **Start** → search **Environment Variables**
2. Click **Edit the system environment variables**
3. Click **Environment Variables…**
4. Find **Path** under **User variables** (recommended) or **System variables**
5. Click **Path** → **Edit…**
6. Click **New** and add:
   - `C:\Program Files\nodejs`
7. Click **OK** to close all windows
8. Close all terminals (and ideally sign out/in or reboot)
9. Open a new terminal and verify:
   ```powershell
   where.exe npm
   where.exe node
   npm -v
   node -v
   ```

## Next command
Once Node is available in PATH, start the dev server with:
```powershell
npm run dev
```

