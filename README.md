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

The client currently contains dependency setup and the IDL destination folder.
Client scripts will be added as the tutorial progresses.

```bash
cd counter-client
npm ci
```

## Local configuration and secrets

`counter/Anchor.toml` uses `~/.config/solana/practice-wallet.json` as the developer
wallet. Create your own local development wallet or configure another wallet path.
The wallet file and recovery words must stay outside this repository.

The root `.gitignore` excludes wallet/keypair JSON files, local `.env` files,
dependencies, build outputs, and validator data in both projects. Public program
IDs and wallet paths are configuration, not private keys. Keep a private backup
of your program keypair if you need to retain its program ID.
