# Bi-directional Masked Language Modeling (MLM)

Introduced by BERT, Masked Language Modeling training involves replacing a percentage of input tokens with a special `[MASK]` token, requiring the model to predict the original tokens using context from both directions.

## Bidirectional Context
Because the model can look both left and right, it builds richer representations of sentence semantics compared to unidirectional causal models.

## Information Flow
```mermaid
graph LR
    T1[The] <--> T2[cat]
    T2 <--> T3["[MASK]"]
    T3 <--> T4[on]
    T4 <--> T5[the]
    T5 <--> T6[mat]
    T3 -.->|Predict| Original[sat]
```

[← Back to README](../README.md)
