Avoid rewriting unchanged scripthash allocator headers during archive flushes.
Flush still syncs every body; allocator mutations already write their headers.
