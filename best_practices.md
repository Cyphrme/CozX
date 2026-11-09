# Best Practices




##  Best practices from I-JSON

https://www.rfc-editor.org/rfc/rfc7493

Coze recommends all of I-JSON, except for section 4.3.  Coze recommends using
UTC Unix timestamps.  If that's not suitable then follow the advice of section
4.3.
https://www.rfc-editor.org/rfc/rfc7493


## Digest file names

Coz core serializes a digest as the algorithm name, `:`, then the b64ut value.
The optional prefix `coz:` may be prepended. `:` is the delimiter because it is
not in the b64ut alphabet (`A–Z`, `a–z`, `0–9`, `-`, `_`).  Future `alg` labels
must not contain `:`, so a value splits into a label and a digest.  See
[External Digest Serialization][digest].

```text
SHA-256:oDBDAg4xplHQby6iQ2lZMS1Jz4Op0bNoD5LK3KxEUZo
ES256:U5XUZots-WmQYcQWmsO751Xk0yeVi9XUKWQ2mGz6Aqg
coz:ES256:U5XUZots-WmQYcQWmsO751Xk0yeVi9XUKWQ2mGz6Aqg
```

**Windows**
`:` is not legal in a Windows file name.  Git for Windows will not check such a
name out.  Windows also uses `:` for NTFS alternate data streams
(`name:stream`). When the serialized form is used as a file name, write each
delimiter colon as `_`.  Since this may cause ambiguation, the labeled "coz" may
be prepended for parsing rules.

For example:

 - SHA-256_oDBDAg4xplHQby6iQ2lZMS1Jz4Op0bNoD5LK3KxEUZo
 - ES256_U5XUZots-WmQYcQWmsO751Xk0yeVi9XUKWQ2mGz6Aqg
 - coz_ES256_U5XUZots-WmQYcQWmsO751Xk0yeVi9XUKWQ2mGz6Aqg

[digest]: https://github.com/Cyphrme/Coz#external-digest-serialization

