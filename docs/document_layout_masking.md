# Document Layout / Block-Diagonal Masking

To train Transformers efficiently, multiple short documents are often packed into a single training sequence. Document Layout (or Block-Diagonal) Masking prevents tokens from attending across document boundaries.

## Contamination Mitigation
Without block-diagonal masking, a token from Document A would attend to tokens in Document B, corrupting gradient updates. The mask creates isolated dense blocks along the diagonal.

## Matrix Visual
```mermaid
flowchart TD
    subgraph Batch Tensor
        Doc1["Document 1 (Block 1)"]
        Doc2["Document 2 (Block 2)"]
        CrossMask["Cross-Doc Attention (Masked -inf)"]
    end
    style Doc1 fill:#bbf
    style Doc2 fill:#bfb
```

[← Back to README](../README.md)
