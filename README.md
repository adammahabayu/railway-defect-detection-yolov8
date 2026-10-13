# Rail Defects Detection with YOLOv8

An object detection project for identifying railway track defects using YOLOv8. This project establishes a baseline model, explores an experimental model, visualizes predictions, and evaluates detection performance on validation and test datasets.

## Project Overview

The objective is to explore YOLOv8 for railway defect detection and document baseline model performance.

### Models

- **YOLOv8n** — baseline model
- **YOLOv8s** — experimental model

## Dataset

This project uses the **Multi-class defects in railway tracks** dataset.

- **Source:** [Mendeley Data — Multi-class defects in railway tracks](https://data.mendeley.com/datasets/88sh5y3tmj/1)
- **DOI:** [10.17632/88sh5y3tmj.1](https://doi.org/10.17632/88sh5y3tmj.1)
- **Version:** 1
- **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Please refer to the original dataset record for authorship, citation requirements, and license terms.

The current model labels are represented as `defect_0` to `defect_9`. Their semantic mapping has not yet been independently verified.

## Experimental Results

### YOLOv8n — Validation Set

| Metric | Result |
|---|---:|
| Precision | 0.4587 |
| Recall | 0.4185 |
| mAP50 | 0.3906 |
| mAP50-95 | 0.1579 |

### YOLOv8s — Validation Set

| Metric | Result |
|---|---:|
| Precision | 0.4523 |
| Recall | 0.4520 |
| mAP50 | 0.3837 |
| mAP50-95 | 0.1556 |

### YOLOv8n — Test Set

The YOLOv8n baseline was evaluated on the test split using the saved `best.pt` checkpoint.

| Metric | Result |
|---|---:|
| Test images | 310 |
| Labeled instances | 1,494 |
| Precision | 0.4880 |
| Recall | 0.5111 |
| mAP50 | 0.4671 |
| mAP50-95 | 0.1846 |

Validation and test results come from different data splits and should not be compared as equivalent evaluations. A YOLOv8s test-set result is not reported here.

## Evaluation Artifacts

The YOLOv8n test evaluation generated the following artifacts:

- `baseline_metrics.csv` — summary of the test metrics.
- `confusion_matrix.png` — confusion matrix.
- `confusion_matrix_normalized.png` — normalized confusion matrix.
- `BoxPR_curve.png` — precision-recall curve.
- `BoxF1_curve.png` — F1-confidence curve.

These files are currently stored in the `final_test_yolov8n_recheck` evaluation output folder in Google Drive. They are not included in this repository unless uploaded separately.

## Limitations

- Class labels remain generic until their semantic mapping is verified.
- Some classes have few test instances, which can make per-class metrics unstable.
- The model is an experimental baseline and is not validated for railway safety or operational use.
- Further evaluation, error analysis, and improvement are needed before practical deployment.

## Repository Contents

- `railway_defect_detection_yolov8_baseline.ipynb` — baseline notebook.
- `README.md` — project overview, dataset information, and evaluation results.
- `LICENSE` — project code license.

Evaluation artifacts can be added to the repository if appropriate.

## Reproducibility

The notebook currently uses Google Drive paths for the dataset and model weights. These paths must be adapted to the environment where the notebook is run.

To reproduce the experiment:

1. Obtain the dataset from the source linked above and follow its license terms.
2. Set up the required Python packages, including Ultralytics and PyYAML.
3. Configure the dataset and model-weight paths.
4. Run the notebook cells in order.

For a more reproducible comparison, also record the software versions, training configuration, dataset version, and random seed where available.

## License

The project code and notebook are licensed under the MIT License. See [LICENSE](LICENSE).

Copyright (c) 2026 Adam Mahabayu Muhibbulloh.

The dataset is distributed separately under its own license. Please refer to the original [Mendeley Data record](https://data.mendeley.com/datasets/88sh5y3tmj/1) and the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/) for dataset terms and attribution.
