# Contrastive Representation Matching

Contrastive learning is a self-supervised method that teaches models to distinguish between similar (positive) and dissimilar (negative) pairs of data.

## Key Concepts

- **Data Augmentations**: Creating multiple views of the same sample (e.g., crop, flip, color jitter).
- **InfoNCE Loss**: A noise-contrastive estimation loss that acts as a multi-class categorical cross-entropy loss, pulling positive views together while pushing negative views apart in embedding space.
- **Frameworks**:
  - **SimCLR**: Simple framework using large batch sizes and a projection head.
  - **MoCo**: Momentum contrast using a queue of negative keys and a momentum encoder.
  - **CLIP**: Multimodal contrastive learning matching images to captions.

## SimCLR Pipeline Diagram

```mermaid
flowchart TD
    Img[Original Image x] --> Aug1[Augmentation t1]
    Img --> Aug2[Augmentation t2]
    Aug1 --> Enc1[Encoder f]
    Aug2 --> Enc2[Encoder f]
    Enc1 --> Proj1[Projection Head g]
    Enc2 --> Proj2[Projection Head g]
    Proj1 --> Loss{InfoNCE Contrastive Loss}
    Proj2 --> Loss
    Loss -->|Maximize Agreement| Enc1 & Enc2
```

[← Back to README](../README.md)
