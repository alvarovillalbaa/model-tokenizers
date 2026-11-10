# Tokenizer artifact requirements

Last updated: 2026-11-10

Status: planned requirements, not a generated tokenizer artifact or file schema.

A tokenizer artifact must have an explicit immutable revision and content hash.
The bundle/card should identify the serialization format and compatible backend,
vocabulary, normalization behavior, special-token IDs/policy, training corpus
manifest/hash and sampling/configuration/seed, dependency/code revisions, source
rights, and known limitations.

Inspection and comparison must preserve the supplied artifact identity.
Consumers must not interpret a mutable name as a pinned tokenizer or silently
substitute another artifact. Special-token IDs and normalization changes require
explicit compatibility decisions.

Model-data references the selected artifact when producing encoded/packed
shards; it owns those shard manifests and processing results. Model training
and inference consumers separately own their model/task compatibility checks.
Large artifact bytes live outside Git; this repository keeps small authorized
fixtures, specifications, configurations, cards, and references/hashes.
