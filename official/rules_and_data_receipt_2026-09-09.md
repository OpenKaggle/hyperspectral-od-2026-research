# Rules and data receipt — verified 2026-09-09

Official pages:

- Overview: https://www.kaggle.com/competitions/hyperspectral-object-detection-challenge-2026/overview
- Data: https://www.kaggle.com/competitions/hyperspectral-object-detection-challenge-2026/data
- Rules: https://www.kaggle.com/competitions/hyperspectral-object-detection-challenge-2026/rules
- Discussion: https://www.kaggle.com/competitions/hyperspectral-object-detection-challenge-2026/discussion

## Deadlines and phases

- Phase 1: 2026-07-25 through 2026-09-23; submit predictions for the 1,000-image test set.
- Ranking set: 1,000 images, scheduled for release on 2026-09-23. The official page does not state an exact release time.
- Phase 2: 2026-09-23 through the final deadline. Submissions must contain test and ranking predictions in one CSV.
- Final submission / team merger deadline: 2026-09-24 16:00 UTC, which is 2026-09-25 00:00 Asia/Shanghai.
- Code-review package deadline for the top six: 2026-09-27 (official page gives no time/timezone).
- Winner announcement: 2026-09-28.
- Phase 1 submissions do not count for final ranking. Only submissions made in Phase 2 count.

## Evaluation and leaderboard

- Primary: COCO mAP@[0.5:0.95], ten IoU thresholds from 0.50 through 0.95, official `pycocotools COCOeval` bbox mode, standard 101-point interpolation, macro-averaged over classes.
- Secondary: mAP@0.5 under the same procedure.
- Phase 1 public leaderboard: random 50% of the test set; the other half is hidden.
- Phase 2: 100% of test becomes public; ranking set remains private until the end.
- Test and ranking sets are equally weighted in the final overall mAP.
- Public-leaderboard snapshot at 2026-09-09: 143 teams; first place 0.67943.

## Dataset and schema

- Total currently exposed: 7,003 files, 15.65 GB.
- Train: 3,000 16-bit single-channel mosaic PNGs plus 3,000 VOC XML annotations, described as 11 GB.
- Test: 1,000 16-bit single-channel mosaic PNGs, described as 3.7 GB.
- Ranking: 1,000 PNGs scheduled for 2026-09-23; it was described on the page but not present in the 7,003-file explorer at verification time.
- Camera: XIMEA MQ022HG-IM-SM4X4-VIS3; 4x4 spectral filter array; 16 bands over 460–600 nm.
- Official demosaic output: `(H/4, W/4, 16)` in row-major 4x4 filter order.
- Required CSV header: `id,image_id,class_id,confidence,x1,y1,x2,y2`.
- `id` must be a unique, contiguous integer row identifier starting at zero. The organizer states Kaggle removes it internally before scoring.
- `image_id` is the filename stem, `class_id` is 0–17, confidence is 0–1, and coordinates are top-left/bottom-right in demosaiced-image pixels.

## Model and data-use rules

- Only one trained detection model/checkpoint may produce the final submission.
- Multi-model voting, weighted fusion, WBF, and post-NMS fusion across different models are prohibited.
- The same single checkpoint may use flip/crop/multi-scale TTA.
- Public ImageNet/COCO pretrained backbones are allowed and encouraged when the model, source, and license are declared in the code-review README.
- External remote-sensing DINO teacher/distillation and test-set pseudo-label self-training have open discussion questions but no official host answer as of verification; excluded from the baseline.
- There is a public report of potentially incomplete training annotations, with no host reply as of verification; treat it as an unconfirmed data-quality risk, not permission to add labels.
- Manual/forged annotations, undeclared external pretraining data, evaluation attacks, and private data/code sharing outside the team are prohibited.
- Competition data is competition-only: no redistribution, commercial use, cross-channel pollution, or paper publication without explicit provider permission.

## Prize and post-competition deliverables

- Total: 5,000 RMB. First 2,500; second 1,500; third 1,000; three excellence certificates.
- A member from each top-three team receives a symposium registration waiver and presentation invitation.
- Winner license: open source.
- Top six must send the host a complete package: training/inference source, trained weights, reproducing inference script, and README with environment, dependencies, commands, parameter count, and FLOPs.

