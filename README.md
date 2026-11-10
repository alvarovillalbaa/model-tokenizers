# model-tokenizers

Last updated: 2026-11-10

Train, inspect, and compare tokenizer artifacts independently of dataset
preparation and model training.

**Status: planned.** This repository contains a component specification and
backlog. It has no executable engine, installable package, or working CLI yet.

## Independent use

Start from [the specification](docs/specs/README.md) and
[the tokenizer backlog](docs/specs/backlog.md). The intended tool accepts pinned
corpus or tokenizer artifact references and produces tokenizer artifacts/cards
or comparison reports. It should not require Lab, a trainer, GPU orchestration,
or a sibling checkout.

## Ownership

Tokenizer fitting/training, vocabulary and special-token policy, normalization
compatibility, artifact inspection, compression evaluation, domain/language
comparisons, tokenizer cards, and hash-pinned tokenizer artifact requirements.

[model-data](https://github.com/alvarovillalbaa/model-data) owns dataset ingestion, curation, deduplication,
splits, encoding/packing pipelines, dataset/shard manifests, and data cards.
Model-data may consume one of this component's pinned tokenizer artifacts;
it must not train or silently change the selected tokenizer.

## Compose

Consume a dataset/corpus manifest from model-data or another producer. Export
an explicit tokenizer artifact reference for any compatible data pipeline,
trainer, inference adapter, or tokenizer comparison consumer. The artifact
boundary carries revision, content hash, format/backend compatibility,
normalization behavior, and special-token policy. Shared source copies and
mandatory Lab dependencies are unnecessary.

[Target interfaces](docs/specs/README.md) ·
[Artifact requirements](docs/specs/artifacts.md) ·
[Extraction provenance](docs/sources/lab-provenance.json)

MIT applies to the authored code and documentation. Corpora, imported tokenizer
artifacts, backend libraries, and models retain their own terms.
