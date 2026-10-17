A Class A write plan that is not the next append range is now refused before
any row is written (it used to fail after appending). The same-batch spent
overlay finds each create's row by its offset in that range instead of building
a hash map on the write thread. The `ibd: perf` line reports that step as
`arch_write_overlay_ms`; `arch_write_txstat_ms` no longer includes it.
