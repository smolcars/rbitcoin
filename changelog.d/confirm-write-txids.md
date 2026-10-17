Reuse prevalidated transaction IDs for ordered BIP30 duplicate checks instead
of hashing the transactions again. Missing create identities fail closed; the
duplicate-transaction rules are unchanged.
