# Reproduction for renovatebot/renovate#47072

## Current behavior

The project pins Node to `20.17.0` (`.nvmrc` and `engines.node`) and allows `npm >=10` (`engines.npm`).
When Renovate updates `package-lock.json`, it resolves `npm >=10` to the latest release (`12.2.0`) and installs it on Node `20.17.0`.
npm 12 requires `^22.22.2 || ^24.15.0 || >=26.0.0`, so `npm install` fails with `ERR_REQUIRE_ESM` and the branch gets an artifact error.

## Expected behavior

Renovate picks the newest npm release whose `engines.node` accepts Node `20.17.0` (currently `11.21.1`), and the lockfile update succeeds.

## Link to the Renovate issue or Discussion

https://github.com/renovatebot/renovate/issues/47072
