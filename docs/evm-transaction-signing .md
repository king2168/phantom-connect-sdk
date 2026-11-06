# EVM transaction signing

Connect SDK signing APIs bind every EVM transaction to its selected network
before the transaction reaches the signing service.

The SDK derives the expected chain ID from a supported `eip155` `networkId`.
For structured legacy and typed transactions, an omitted or zero `chainId` is
replaced with that expected value. A nonzero caller-provided `chainId` must be
valid, supported, and equal to the selected network.

Raw hex and byte inputs are decoded as unsigned EVM transactions and checked by
the same rules. Malformed encodings, already-signed transactions, unsupported
chain IDs, and network mismatches are rejected before signing.

Chain ID strings may use decimal form such as `137` or hexadecimal form such as
`0x89`. Other string formats are invalid.
