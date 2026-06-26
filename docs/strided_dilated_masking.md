# Strided / Dilated Masking

Strided (or Dilated) masking allows attention heads to skip tokens at fixed intervals, expanding the model's overall receptive field without increasing computational complexity.

## Mechanism
Instead of attending to every contiguous neighbor, a token attends to indices $i - d, i - 2d, i - 3d$, where $d$ is the dilation stride.

## Grid Visual
```mermaid
graph TD
    Q[Query Token i] -->|Attend| K1[Key i-2]
    Q -->|Attend| K2[Key i-4]
    Q -->|Attend| K3[Key i-6]
    Q -.->|Masked| M1[Key i-1]
    Q -.->|Masked| M2[Key i-3]
    style K1 fill:#bbf
    style K2 fill:#bbf
    style K3 fill:#bbf
    style M1 fill:#ddd
    style M2 fill:#ddd
```

[← Back to README](../README.md)
