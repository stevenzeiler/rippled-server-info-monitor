# Status

Last reviewed: 2026-11-20 (pass 02 of the GitHub audit; docs only, nothing was run).

## What works
- By reading the code: `ServerInfo`, `ServerInfoMonitor`, `StatsdMonitor` and `StatsdSupervisor` form a complete polling pipeline, started by `npm start`.

## Known broken or unverified
- Not run in this pass; no automated tests (`test/` holds manual scripts).
- `peers.json` is a 2015 list of server IPs and `graphite.rippletest.net` is a 2015 host; they are likely dead **(inference)**.
- `StatsdMonitor.start()` returns nothing, so `StatsdSupervisor._monitors` fills with `undefined` and `restart()` does not stop the old intervals **(inference from reading `lib/`)**.
- `babel-node` is required but not in `package.json`; `package.json` name is `server_info`, with empty description and author and no `repository`; `main` points at a missing `index.js`.
- Unused dependencies appear to include `hbase` and `moment` (not imported in the files read).
- Peers are contacted over `ws://` port 443, which is unusual **(inference)**.

## Next
1. Add Babel to devDependencies and a README-accurate `package.json`.
2. Fix the supervisor to hold monitor instances and stop them on restart.
3. Replace the 2015 peer list with configuration; decide on a LICENSE file.

## Not yet from the standard
CONTRIBUTING.md, docs/ARCHITECTURE.md, docs/RELEASING.md, docs/decisions/, events/CATALOG.md, CHANGELOG.md, SECURITY.md, LICENSE, .github/.
