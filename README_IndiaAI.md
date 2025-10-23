# IndiaAI Face Authentication Challenge - Prototype

## Overview
Privacy-preserving face de-duplication system for large-scale government examinations.

## Key Features
- **Two-stage pipeline**: LSH blocking (fast) + deep matching (accurate)
- **Privacy-first**: Cancelable biometric templates, encrypted search
- **Anti-spoofing**: Passive liveness detection
- **Scalable**: Sub-linear search complexity for millions of applications
- **Fair & transparent**: Bias monitoring and explainability dashboard

## Installation

```bash
pip install -r requirements_indiaai.txt
```

## Usage

```bash
jupyter notebook IndiaAI_Face_Deduplication_Prototype.ipynb
```

The notebook will:
1. Download the LFW dataset automatically (first run only)
2. Process test applications through the complete pipeline
3. Show accuracy metrics and visualizations
4. Generate performance benchmarks

## System Architecture

```
Application → Quality Check → Liveness Detection
    ↓
Stage A: LSH Blocking (privacy-preserving, fast)
    ↓
Stage B: Deep Matching (high-precision on candidates)
    ↓
Risk-based Decision + Audit Log
```

## Technical Highlights

- **Cancelable templates**: 256-bit protected embeddings (50% smaller, revocable)
- **LSH search**: O(log N) complexity vs O(N) for brute force
- **Passive liveness**: Texture, moiré, and reflection analysis
- **DPDP compliance**: Complete audit trail, data minimization

## Results on LFW Dataset

- Accuracy: ~90%+
- Query time: <5ms for 5K database
- Scalable to millions of applications

## Production Considerations

For deployment, replace simulated models with:
- InsightFace/ArcFace for embeddings
- ONNX/TensorRT for optimization
- GPU acceleration with faiss-gpu
- Distributed LSH for horizontal scaling

## Contact

For questions about the IndiaAI challenge submission, contact:
- fellow3.gpai-india@meity.gov.in
- am-projects4@indiaai.gov.in
