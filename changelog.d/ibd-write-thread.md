Changed

- **Class A commit checks the append range before it writes.**
  A plan that is not the next fk range is refused before any row is
  written; it used to fail after appending. The same-batch spent overlay
  finds each create's row by offset instead of building a hash map.
- **Ordered BIP30 checks reuse the create txids from structure time.**
  The write thread no longer hashes every transaction again. A missing
  identity fails closed; the duplicate-transaction rules are unchanged.
- **Scripthash flush no longer rewrites unchanged allocator headers.**
  Every body is still synced; allocator mutations already write their
  headers.
- **`ibd: perf` names write-thread costs that were hidden.**
  `thr_write_merge_ms` is merging drained writeq parts (it used to count
  as `thr_write_recv_wait_ms`), `arch_write_encode_ms` is Class A row
  encode, `ensure_abs_ms` is the spend abs walk, and
  `arch_write_overlay_ms` is the spent overlay (no longer inside
  `arch_write_txstat_ms`).
