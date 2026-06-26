# The Tasks-Specific Layout Era (~2019–2022)

Following the initial success of the Transformer, architectures diverged to support non-generative tasks. Specialized attention masking patterns emerged to customize representation learning for encoder-only and encoder-decoder models.

## Architectural Adaptations
* **Masked Language Modeling (MLM):** Popularized by BERT (Devlin et al., 2018), this approach corrupts the input by replacing select tokens with `[MASK]`. The model uses fully bidirectional masking to reconstruct the original tokens from surrounding left-and-right contexts.
* **Prefix / Hybrid Masking:** Popularized by UniLM and T5, this model permits bidirectional attention over a prompt (or "prefix") but enforces strict causal masking on all subsequent generated tokens.

## Mask Comparison
```mermaid
graph TD
    subgraph MLM / Bidirectional
        B1[Token 1] <--> B2[Token 2]
        B2 <--> B3[Token 3]
        B3 <--> B4[Token 4]
    end
    subgraph Prefix / Hybrid
        P1[Prefix 1] <--> P2[Prefix 2]
        P2 --> C1[Gen 1]
        C1 --> C2[Gen 2]
        C2 -.->|Causal Block| P1
    end
```

[← Back to README](../README.md)
