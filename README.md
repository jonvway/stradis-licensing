# stradis-licensing

The **license revocation list** (kill-switch) for the Stradis app.

`revoked.json` is fetched by every running copy (every ~6h + on launch). To
**terminate a license**, add its id to the `revoked` array and commit:

```json
{ "revoked": ["lic_ab12cd34"] }
```

The id is printed by `scripts/licensing/mintLicense.mjs` when you issue a
license. Effect is near-instant for online testers (within the ~6h refresh or
next launch); offline testers when they reconnect (the token's own expiry is the
backstop). The ids are opaque — nothing here is sensitive, which is why this
repo is public (the app fetches the raw file with no auth).
