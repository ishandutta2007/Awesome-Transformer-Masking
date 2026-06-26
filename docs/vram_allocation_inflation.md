# VRAM Allocation Inflation

As context length scales to tens of thousands of tokens, the VRAM required to store the physical attention mask matrix grows quadratically.

## Memory Footprint
A sequence of length $N = 32,000$ requires allocating a $32,000 \times 32,000$ matrix per attention head, consuming gigabytes of VRAM just to store the masking mask.

## Mitigation: FlashAttention
By fusing attention calculations and evaluating masking rules on-the-fly in SRAM registers, no physical mask tensor needs to be saved in HBM.

```mermaid
graph LR
    Vanilla[Vanilla: HBM Mask Storage O(N^2)] -->|FlashAttention| Fused[Fused: Register-Level Online Masking O(1) HBM]
```

[← Back to README](../README.md)
