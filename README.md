# Rail Defects Detection with YOLOv8

An object detection project for identifying railway track defects using YOLOv8. This project establishes a baseline model, visualizes predictions, and evaluates detection performance on a test dataset.

## Project Overview

The objective of this project is to explore YOLOv8 for railway defect detection and document the baseline model's performance.

### Models
- YOLOv8n — baseline model
- YOLOv8s — experimental model

## Dataset

This project uses the **Multi-class defects in railway tracks** dataset.

- **Source:** [Mendeley Data — Multi-class defects in railway tracks](https://data.mendeley.com/datasets/88sh5y3tmj/1)
- **DOI:** [10.17632/88sh5y3tmj.1](https://doi.org/10.17632/88sh5y3tmj.1)
- **Version:** 1
- **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Please refer to the original dataset record for the authorship, citation requirements, and license terms.

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

| Metric | Result |
|---|---:|
| Precision | 0.4880 |
| Recall | 0.5111 |
| mAP50 | 0.4671 |
| mAP50-95 | 0.1846 |

Validation and test results come from different data splits and should not be compared as equivalent evaluations. A YOLOv8s test-set result is not reported here.

## Limitations

- Class labels remain generic until their semantic mapping is verified.
- Some classes have few test instances, which can make per-class metrics unstable.
- The model is an experimental baseline and is not validated for railway safety or operational use.
- Further evaluation and improvement are needed before practical deployment.

## Repository Contents

- `railway_defect_detection_yolov8_baseline.ipynb` — baseline notebook.

Evaluation artifacts are saved separately in the project's Google Drive folder. They can be added to this repository if appropriate.

## Reproducibility

The notebook currently uses Google Drive paths for the dataset and model weights. These paths must be adapted to the environment where the notebook is run.

To reproduce the experiment:
1. Obtain the dataset from the source linked above and follow its license terms.
2. Set up the required Python packages, including Ultralytics and PyYAML.
3. Configure the dataset and model-weight paths.
4. Run the notebook cells in order.

## License

The project code and notebook are licensed under the MIT License. See [LICENSE](LICENSE).

The dataset is distributed separately under its own license. Please refer to the original [Mendeley Data record](https://data.mendeley.com/datasets/88sh5y3tmj/1) and the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/) for dataset terms and attribution.
