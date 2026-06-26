# Cross-Modal Image-Text Masking

In multimodal models, cross-modal masking controls information exchange between disparate modalities (e.g., aligning visual patches with text tokens).

## Rules
* Text tokens can attend to image patches to ground text queries in visual space.
* Image patches are blocked from attending causally to future text tokens to preserve generative boundaries.

## Architecture
```mermaid
direction LR
graph TD
    Image[Image Patches] -->|Fully Visible| CrossAttention[Cross-Attention Matrix]
    Text[Text Query] -->|Causal Masking| CrossAttention
    CrossAttention --> Output[Multimodal Representation]
```

[← Back to README](../README.md)
