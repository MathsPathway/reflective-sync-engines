# reflective-sync engines

Prebuilt copies of the reflective-sync engine, one library per target, for the
Flutter SDK to use so an app can build without a Rust toolchain.

This repository holds releases and nothing else. The source is not here.

## How they are used

The SDK's build hook reads `engines.json` from the SDK itself, not from here.
That file names a release, the SHA-256 of each library in it, and a
fingerprint of the engine sources the release was built from. The hook
downloads a library from this repository's releases only when that
fingerprint matches the SDK checkout it is running in, and bundles the file
only if its hash is the pinned one. So nothing in this repository is trusted
on its own: a file that has changed is refused.

A release is made by pushing an `engines-*` tag to the source repository,
whose workflow builds every target through the same build hook an app uses.

## Licence

No open-source licence applies to these files.
