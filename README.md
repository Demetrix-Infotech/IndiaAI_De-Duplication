# IndiaAI Face Deduplication – Full Pipeline Prototype

Privacy-preserving face de-duplication stack designed for large-scale
enrolment programmes (examinations, welfare schemes, SIM/KYC onboarding).
The notebook walks through image quality gating, passive liveness, cancelable
biometric templates, LSH-based blocking, deep similarity re-ranking, audit
logging, fairness diagnostics, and bulk duplicate mining on the LFW
deep-funneled dataset.

## Key Capabilities
- **Quality assessment** – Laplacian blur, Haar-based pose, lighting heuristics.
- **Passive liveness** – Texture entropy and Fourier cues with tunable threshold.
- **Cancelable biometrics** – Keyed Gaussian random projections (revocable IDs).
- **Two-stage matching** – LSH candidate retrieval + cosine/Euclidean re-ranking.
- **Risk-based decisions** – UNIQUE / DUPLICATE / MANUAL_REVIEW with confidence.
- **Audit & fairness** – JSONL trail plus pandas roll-ups of quality/liveness/match scores.
- **Bulk mining** – Stand-alone helper to surface top duplicate pairs from LFW.

## Repository Layout
- `IndiaAI_Face_Deduplication_Prototype.ipynb` – end-to-end walkthrough.
- `requirements_indiaai.txt` – Python dependencies (face_recognition, OpenCV, etc.).
- `lfw_dataset/` – auto-populated deep-funneled dataset (downloaded on first run).
- `face_dedup_data/` – audit log output and temporary artefacts.

## Quick Start
1. **Install dependencies**
   ```bash
   pip install -r requirements_indiaai.txt
   ```
2. **Launch the notebook**
   ```bash
   jupyter notebook IndiaAI_Face_Deduplication_Prototype.ipynb
   ```
3. **Run the sections sequentially**
   - *Setup & Imports* – verify environment.
   - *System Modules (Sections 2–8)* – instantiate quality, liveness, embedding, LSH, logging.
   - *Pipeline Assembly* – build `FaceDeduplicationPipeline`.
   - *Dataset Preparation* – downloads LFW automatically (falls back to synthetic faces if offline).
   - *Process Applications & Evaluation* – review metrics, fairness summary, confusion matrix.
   - *Visual Analytics* – view query vs. top candidate panels and duplicate pair listings.
   - *Bulk Duplicate Mining* – optional exploratory scanner across the dataset.

## Configuration Highlights
- Adjust thresholds in the `Config` section (`MATCH_THRESHOLD_*`, `LIVENESS_THRESHOLD`).
- Limit ingestion workload via `MAX_IMAGES_PER_IDENTITY` and `MAX_TOTAL_IMAGES`.
- Toggle cosine vs. Euclidean scoring, enable plot exports by setting `SAVE_DIR`.
- Liveness parameters are conservative by default; tune for your capture environment.

## Expected Outputs
- Console metrics: accuracy, precision, recall, F1, confusion matrix.
- Fairness table summarising quality, liveness, and similarity scores by decision.
- Matplotlib composites of suspected duplicates with similarity annotations.
- Optional PNG artefacts from bulk mining when a `SAVE_DIR` is provided.

## Sector Replicability
Swap the data ingestion hook or quality/liveness modules to adapt the pipeline to
education, financial KYC, travel security, or telecom SIM registration. The
cancelable template/LSH backbone keeps privacy and audit guarantees intact while
supporting sector-specific business rules.

## Acknowledgements
LFW assets were originally published at <http://vis-www.cs.umass.edu/lfw/>.  
Gary B. Huang, Manu Ramesh, Tamara Berg, and Erik Learned-Miller. *Labeled Faces in the
Wild: A Database for Studying Face Recognition in Unconstrained Environments*.
University of Massachusetts, Amherst, Technical Report 07-49, October 2007.
