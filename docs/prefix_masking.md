# Prefix / Unidirectional-to-Causal Hybrid Masking

Prefix masking bridges the gap between bidirectional comprehension and causal generation. It allows fully bidirectional attention over an initial prompt ("prefix"), followed by strict causal attention for generated tokens.

## Application
Commonly used in text-to-text models (such as T5 or UniLM) and decoders fine-tuned for prompt compliance.

## Mask Layout
For a sequence where the first $k$ tokens form the prefix and subsequent tokens are generated:

```mermaid
flowchart TD
    subgraph Bidirectional Prefix Area
        A[Prefix Token 1] <--> B[Prefix Token 2]
    end
    subgraph Causal Generation Area
        B --> C[Generated Token 1]
        C --> D[Generated Token 2]
        D -.->|Masked| B
    end
```

[← Back to README](../README.md)
