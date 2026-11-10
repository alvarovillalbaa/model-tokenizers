# model-tokenizers agent instructions

- Read README.md and docs/specs/README.md before changing behavior.
- Status is planned: do not claim an executable package, CLI, or trained tokenizer exists.
- This repository owns tokenizer training, inspection, comparison, and artifact requirements.
- Dataset ingestion/curation/splits and encoding/packing pipelines belong to model-data.
- Never import lab or assume sibling checkouts. Use explicit corpus and artifact references.
- Preserve source provenance and exact historical source evidence.
- Declare dependencies and backend compatibility before adding an implementation.
- Do not download corpora, model weights, GPU stacks, or contact providers implicitly.
- Keep large artifacts, caches, credentials, and unique experiment outputs outside Git.
- Run focused checks for actual changes and git diff --check; keep documentation honest.
