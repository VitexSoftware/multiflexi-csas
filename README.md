# MultiFlexi CSAS Credential Prototype

Credential prototype plugin for [MultiFlexi](https://multiflexi.eu/) providing integration with **Česká Spořitelna a.s. (ČSAS / Erste)** API services.

This package was separated from [multiflexi-core](https://github.com/VitexSoftware/php-vitexsoftware-multiflexi-core) into its own standalone project/package.

## What it does

Provides a credential prototype that manages ČSAS API credentials for MultiFlexi applications:

- **CSAS_TOKEN_ID** — Token UUID identifier (user-configured)
- **CSAS_API_KEY** — API key for ČSAS services (auto-provided)
- **CSAS_SANDBOX_MODE** — Sandbox mode toggle (auto-provided)
- **CSAS_ACCESS_TOKEN** — OAuth access token with expiration tracking (auto-provided)

The prototype integrates with the [csas-authorize](https://github.com/Spoje-NET/csas-authorize) tool to automatically obtain and refresh access tokens.

## Installation

### From Debian Package

```bash
sudo dpkg -i multiflexi-csas_0.1.0_all.deb
sudo apt-get install -f  # Install dependencies
```

### Dependencies

- `multiflexi-cli` — MultiFlexi command-line interface
- `csas-authorize` — ČSAS token management tool

## How it works

1. The credential prototype registers itself with MultiFlexi during package installation via `multiflexi crprototype sync`
2. When configuring credentials, available tokens from `csas-access-token` are listed for selection
3. On credential query, a fresh access token is obtained using the selected token UUID
4. The access token and related configuration are provided to MultiFlexi applications

## Files

- `/usr/share/php/MultiFlexi/CredentialProtoType/Csas.php` — Credential prototype class

## License

See [debian/copyright](debian/copyright)