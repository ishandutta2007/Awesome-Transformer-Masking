# Causal Masking (Lower-Triangular Mask)

Causal masking is the architectural foundation of autoregressive text generation. It prevents the model from attending to tokens that appear after the current query index, preserving temporal order.

## Mechanism
The causal mask $M$ is a lower-triangular matrix containing $0$ on and below the diagonal, and $-\infty$ above:

$$M = \begin{pmatrix} 
0 & -\infty & -\infty & \dots & -\infty \\ 
0 & 0 & -\infty & \dots & -\infty \\ 
0 & 0 & 0 & \dots & -\infty \\ 
\vdots & \vdots & \vdots & \ddots & \vdots \\ 
0 & 0 & 0 & \dots & 0 
\end{pmatrix}$$

## Information Flow
```mermaid
graph LR
    T1[Token 1] --> T1_Self[T1 Representation]
    T1 --> T2_Self[T2 Representation]
    T2[Token 2] --> T2_Self
    T1 --> T3_Self[T3 Representation]
    T2 --> T3_Self
    T3[Token 3] --> T3_Self
    style T1 fill:#f9f,stroke:#333
    style T2 fill:#bbf,stroke:#333
    style T3 fill:#bfb,stroke:#333
```

[← Back to README](../README.md)
