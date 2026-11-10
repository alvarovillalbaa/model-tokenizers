# Tokenizer component specification

Last updated: 2026-11-10

Status: planned. The interfaces below describe intended capabilities; none is
implemented as a package or command.

## Purpose and consumers

Provide tokenizer training, artifact inspection, and comparisons usable by
data researchers, model developers, and existing tokenizer users independently.
A user should be able to inspect or compare existing artifacts without training
a model or installing a dataset-curation system.

## Target standalone interfaces

| Capability | Explicit inputs | Intended outputs |
| --- | --- | --- |
| Train | Pinned corpus manifests/bytes, algorithm/backend, vocabulary size, sampling/seed, normalization and special-token policy | Tokenizer artifact bundle, content hash, complete training configuration/provenance, and tokenizer card |
| Inspect | Existing tokenizer artifact revision/hash and declared format/backend | Vocabulary/special-token/normalization summary, compatibility and integrity findings |
| Compare | Named artifact revisions/hashes and the same frozen evaluation corpus slices | Per-domain/language compression and token-count tables, applicable unknown-token behavior, coverage, and limitations |

A consumer can use each capability independently. Exact commands and wire
schemas will be selected against the first implementation, rather than
invented by this specification.

## Boundary with dataset preparation

Model-data owns ingestion, curation, deduplication, split construction, dataset
manifests, and its encoding/packing pipeline. This component consumes an
explicitly supplied corpus; it does not silently broaden sources or choose a
train/evaluation split. It emits a selected tokenizer artifact rather than
rewriting another repository's dataset pipeline.

Corpus identity, slice membership, normalization, and measurement conventions
must be explicit for a comparison. Tokenizer compression measurements alone do
not prove downstream model quality. Open Evals remains the evaluation platform
when an experiment needs model-quality evidence.

## Next work

- [ ] Implement a tiny CPU training/serialization path with declared backend dependencies.
- [ ] Load and inspect a pinned artifact independently of training.
- [ ] Define vocabulary, normalization, and special-token compatibility checks.
- [ ] Compare two artifacts on the same small frozen domain/language slices.
- [ ] Emit a tokenizer card and immutable artifact reference.
- [ ] Exercise an artifact consumer without importing this repository's source checkout.

[Artifact requirements](artifacts.md) ·
[Original tokenizer blueprint](blueprint.md) · [Backlog](backlog.md)

## Acceptance

An implementation must install and run independently, document actual inputs
and outputs, include an example and focused checks, and report unsupported
formats honestly. A CPU smoke must retain corpus/config/backend identity and
demonstrate artifact load/inspection after serialization. No implementation or
experimental result is claimed by this repository's current documentation.
