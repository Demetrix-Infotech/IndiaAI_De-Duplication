# IndiaAI Face Deduplication – Quick Duplicate Mining

This repository now ships a lightweight notebook that focuses on one task:
mining the LFW deep-funneled dataset (or any look-alike folder of cropped face
JPEGs) for highly similar pairs and rendering them side by side with their
similarity score.

## Quick Start
1. **Install dependencies**
   ```bash
   pip install -r requirements_indiaai.txt
   ```
2. **Prepare data**  
   Extract the LFW deep-funneled archive into `lfw_dataset/`. The helper inside
   the notebook automatically resolves the nested
   `lfw-deepfunneled/lfw-deepfunneled` directory. You can also point the script
   to another image folder by editing `IMAGE_FOLDER`.
3. **Run the notebook**
   ```bash
   jupyter notebook IndiaAI_Face_Deduplication_Prototype.ipynb
   ```
   - Optionally execute the first code cell to install requirements.
   - Update the configuration block (dataset path, metric, thresholds, limits,
     and optional `SAVE_DIR`).
   - Run the final cell to compute face encodings, score pairwise similarities,
     and visualise the top matches.

## Output
- Console summary of the strongest duplicate candidates with similarity scores.
- Matplotlib panels showing each matched pair side by side.
- Optional PNG exports when `SAVE_DIR` is set.

## Notes
- The workflow relies on `face_recognition` for encodings; ensure dlib wheels
  are available for your platform.
- Reduce `MAX_IMAGES_PER_IDENTITY` or `MAX_TOTAL_IMAGES` if you need faster
  iteration; increase them for broader coverage.
- Switch `METRIC` between `"euclidean"` and `"cosine"` to explore different
  scoring strategies.

## Acknowledgements
LFW assets were originally published at <http://vis-www.cs.umass.edu/lfw/>.  
Gary B. Huang, Manu Ramesh, Tamara Berg, and Erik Learned-Miller. *Labeled Faces
in the Wild: A Database for Studying Face Recognition in Unconstrained
Environments*. University of Massachusetts, Amherst, Technical Report 07-49,
October 2007.
