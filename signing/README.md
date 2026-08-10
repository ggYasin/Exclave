# Inclave release signing

Every installable Inclave release must be signed by the certificate in this directory.
Its SHA-256 fingerprint is:

```
2cc74b93a847d39c7049d73d4508a0a649a9d7b1da71c1999ed79f672f973987
```

The private PKCS12 keystore is never stored in Git. GitHub Actions obtains it from the
`release-signing` environment secrets and verifies this fingerprint both before and after
building. A release build fails if signing credentials are absent or if any APK has a
different signer.

Future releases must retain the package ID `com.github.ggyasin.exclave.clone`, use this
same signing identity, and increase `VERSION_CODE` in `version.properties`.
