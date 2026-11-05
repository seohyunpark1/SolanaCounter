# SolanaCounter

A Solana counter learning project with an Anchor program and a separate TypeScript client.

```text
SolanaCounter/
├── counter/          # Anchor workspace: Rust program, tests, and configuration
└── counter-client/   # TypeScript client project
    └── src/idl/      # Destination for the generated program IDL
```

## Counter program

Run Anchor commands from `counter/`, where `Anchor.toml` lives:

```bash
cd counter
yarn install
anchor build
anchor test
```

The program initializes a counter at zero, allows its authority to increment it,
and checks for overflow. The current test suite contains three tests.

## Client

The client contains a TypeScript CLI, devnet configuration, and copies of the
generated program IDL and TypeScript type in `src/idl/`. Available commands are
`status`, `balance`, `airdrop`, `init`, `increment`, and `get`.

```bash
cd counter-client
npm ci
npm run cli -- status
npm run cli -- balance
```

Run these commands from `counter-client/`. The client uses devnet and loads the
local practice wallet configured in `src/config.ts`. Initialize your counter
with `npm run cli -- init` before using `increment` or `get`; `init` is only
needed once per wallet for a given program ID on that cluster.

## Local configuration and secrets

`counter/Anchor.toml` uses `~/.config/solana/practice-wallet.json` as the developer
wallet. Create your own local development wallet or configure another wallet path.
The wallet file and recovery words must stay outside this repository.

The root `.gitignore` excludes wallet/keypair JSON files, local `.env` files,
dependencies, build outputs, and validator data in both projects. Public program
IDs and wallet paths are configuration, not private keys. Keep a private backup
of your program keypair if you need to retain its program ID.
