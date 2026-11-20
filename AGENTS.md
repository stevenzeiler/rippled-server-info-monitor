# AGENTS.md

## Stack
ES6 JavaScript run with `babel-node` (Babel 5), ripple-lib 0.12, node-statsd, underscore. Dormant since 2015.

## Layout
- `statsd.js` - entry point; reads `peers.json`, builds the supervisor
- `lib/server_info.js` - one rippled connection and `fetch()`
- `lib/server_info_monitor.js` - interval poller; override `onData`/`onError`
- `lib/statsd_monitor.js`, `lib/statsd_supervisor.js` - gauge writer and per-peer supervisor
- `peers.json` - server IP groups
- `test/` - manual scripts
- `docs/STATUS.md` - current state

## Commands
- `npm install`
- `npm start` (runs `babel-node statsd.js`)
- Env: `STATSD_HOST`, `STATSD_PORT`

## Rules
- Never commit secrets or credentials.
- Use Conventional Commits (`docs:`, `fix:`, `feat:`).
- Keep `docs/STATUS.md` current when behaviour or state changes.
