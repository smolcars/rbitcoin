The `ibd: perf` line splits three write-thread costs that were hidden:
`thr_write_merge_ms` (merging drained write-queue parts, which used to count
as `thr_write_recv_wait_ms`), `arch_write_encode_ms` (Class A row encode inside
`arch_write_body_ms`), and `ensure_abs_ms` (the spend abs walk inside `ensure`).
