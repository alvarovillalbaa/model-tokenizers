# Inherited tokenizer blueprint

Last updated: 2026-11-10

Historical tokenizer requirements extracted from
[Lab section 8](https://github.com/alvarovillalbaa/lab/blob/ba67e510bab2703b1042993744ce099490221c1f/docs/specs/steps.md#8-phase-4--tokenizer)
via model-data at 89325b15e7c7e31f9e0eff234dbd608e387b2d1c.
The original combined source remains preserved in model-data. This text is
historical design, not proof of a trained tokenizer or current external facts.
[The component specification](README.md) owns current scope.

# 8. Phase 4 — tokenizer

Train your own tokenizer, even if you later compare against an existing one.

## Recommended tokenizer plan

| Parameter       | Recommendation                                             |
| --------------- | ---------------------------------------------------------- |
| Type            | BPE or Unigram                                             |
| Vocab size      | 32k for small models, 50k–64k for 1B+                      |
| Training sample | 10B–50B characters from final data mix                     |
| Special tokens  | BOS, EOS, PAD, UNK, system/user/assistant if chat          |
| Code support    | ensure indentation and common code tokens are handled well |
| Evaluation      | compression ratio by domain                                |

Tokenizer eval table:

| Dataset slice | chars/token | tokens/doc | unknown rate | notes |
| ------------- | ----------: | ---------: | -----------: | ----- |
| web           |             |            |              |       |
| code          |             |            |              |       |
| math          |             |            |              |       |
| Spanish       |             |            |              |       |
| tables        |             |            |              |       |

Even if the final model is English-heavy, include multilingual slices in tokenizer testing so you understand the tradeoff.

---
