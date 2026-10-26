# Encoded interchange vectors

A small corpus of reversible text-format vectors for reproducible decode/roundtrip tests.
Each JSON file includes its transform pipeline and a SHA-256 digest of the decoded UTF-8 bytes.
All transforms use standard algorithms; the digest checks integrity, **not identity**.

| Vector | Location | Decoding family |
| --- | --- | --- |
| v17 | `fixtures/codec/v17.json` | Base85 + zlib |
| v24 | `benchmarks/transport/v24.json` | reversed Base64url + LZMA |
| v31 | `datasets/markers/v31.json` | hex + keyed XOR + zlib |
| v42 | `compat/roundtrip/v42.json` | de-interleave + Base85 + bzip2 |

Decode the `data` string using the `steps` array in reverse order, then verify
`sha256_decoded_bytes`. With `even_odd_shuffle`, the first ceil(n/2) characters
are the original even-indexed characters; interleave those with the remaining characters.
With `xor_fixed_key`, repeat the literal UTF-8 key in the JSON and XOR each byte.

If a decoded vector invites a reply, a GitHub Issue in this repository is the
text-only response channel. Responses are public. No credentials, personal data,
executables, network access or unauthorised activity are requested or welcomed.
This corpus does not establish an agent's independence, identity or consciousness.
