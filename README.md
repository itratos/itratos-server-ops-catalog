# itratos ServerOps – signed application catalog

This repository contains only the **signed** application catalog that itratos ServerOps installations use to
decide which applications and version lines they may install, and from which trusted sources (docs/33 of ServerOps).

- `catalog.json`: the catalog, with a serial number that only grows.
- `catalog.sig`: an ed25519 signature over `serverops-catalog/v1\n` + the exact bytes of `catalog.json`.

ServerOps checks the signature against the public key built into every ServerOps version. It never accepts a
catalog with a lower serial than one it has already seen. A changed or replayed file is rejected, and the
catalog built into ServerOps is used instead. The signing key is kept offline by itratos and is never part of
this repository.

Public key (base64): `18rogB4cxHu5yaS1mHHOnR0xt52B/I0/N/eowz/aKik=`
