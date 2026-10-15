# Railway Defect Detection with YOLOv8

An object detection project for identifying railway track defects using YOLOv8. This project establishes a baseline model, explores an experimental model, visualizes predictions, and evaluates detection performance on validation and test datasets.

## Project Overview

The objective of this project is to explore YOLOv8 for railway defect detection and document baseline model performance.

### Models

- **YOLOv8n** — baseline model.
- **YOLOv8s** — experimental model.

The YOLOv8n model is used for the reported test-set evaluation. YOLOv8s results are reported for the validation set only.

## Dataset

This project uses the **Multi-class defects in railway tracks** dataset.

- **Source:** [Mendeley Data — Multi-class defects in railway tracks](https://data.mendeley.com/datasets/88sh5y3tmj/1)
- **DOI:** [10.17632/88sh5y3tmj.1](https://doi.org/10.17632/88sh5y3tmj.1)
- **Version:** 1
- **License:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)

Please refer to the original dataset record for dataset authorship, recommended citation, attribution requirements, and license terms.

The current model labels are represented as `defect_0` to `defect_9`. Their semantic mapping has not yet been independently verified, so these labels should not be interpreted as specific defect types without further verification.

## Methodology

The project explores object detection using YOLOv8 with two model configurations:

1. **YOLOv8n baseline:** used to establish baseline performance.
2. **YOLOv8s experiment:** used to explore a different model size.

The notebook covers model training, prediction visualization, and evaluation on the available dataset splits.

The reported metrics include:

- **Precision:** proportion of predicted detections that are correct.
- **Recall:** proportion of labeled objects successfully detected.
- **mAP50:** mean Average Precision at an IoU threshold of 0.50.
- **mAP50-95:** mean Average Precision averaged across IoU thresholds from 0.50 to 0.95.

### Dataset Cleanup

A dataset cleanup step was performed to remove **110 exact duplicate images** with the `(1)` suffix from the training and test folders.

The latest YOLOv8n test-set evaluation was conducted after this cleanup. The previously reported validation results were obtained from earlier experiments and have not been re-evaluated on the cleaned dataset.

Therefore, validation and test results should be interpreted in the context of their respective evaluation runs. The validation results and latest test results should not be treated as a fully controlled model comparison.

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

The YOLOv8n baseline was evaluated on the test split using the saved `best.pt` checkpoint after the dataset cleanup.

| Metric | Result |
|---|---:|
| Test images | 300 |
| Labeled instances | 1,494 |
| Precision | 0.4886 |
| Recall | 0.5127 |
| mAP50 | 0.4707 |
| mAP50-95 | 0.1858 |

The validation and test results come from different data splits and experiment stages. The validation results were not re-evaluated after the cleanup described above. A YOLOv8s test-set result is not reported here because a corresponding evaluation result is not available.

These metrics represent experimental baseline performance on the available dataset. They do not establish that the model is suitable for real-world railway inspection or safety-critical decisions.

## Evaluation Artifacts

Evaluation plots and metrics for the YOLOv8n baseline are available in the [`results/`](results/) directory.

### Precision–Recall Curve

![Precision–Recall Curve](results/BoxPR_curve.png)

### Confusion Matrix

![Confusion Matrix](results/confusion_matrix.png)

### Normalized Confusion Matrix

![Normalized Confusion Matrix](results/confusion_matrix_normalized.png)

Additional evaluation artifacts include:

- `BoxF1_curve.png` — F1 score curve.
- `BoxP_curve.png` — precision curve.
- `BoxR_curve.png` — recall curve.
- `baseline_metrics.csv` — summary of test-set evaluation metrics.

These artifacts correspond to the YOLOv8n test-set evaluation. The referenced images and CSV must be present in the `results/` directory for the links to work.

## Repository Contents

- `railway_defect_detection_yolov8_baseline.ipynb` — notebook for the baseline experiment.
- `requirements.txt` — Python package dependencies.
- `results/` — evaluation plots and test-set metrics.
- `README.md` — project overview, dataset information, methodology, and results.
- `LICENSE` — license for the project code and notebook.
- `.gitignore` — files and directories excluded from version control.

## Limitations

- The class labels remain generic until their semantic mapping is verified.
- Some classes may have few labeled test instances, which can make per-class metrics unstable.
- The validation results were obtained before the latest dataset cleanup and have not been re-evaluated on the cleaned dataset.
- The reported metrics describe model performance on the evaluated dataset and do not establish real-world railway inspection reliability.
- The model is an experimental baseline and is not validated for railway safety or operational use.
- The YOLOv8s model has validation results reported here, but no test-set result is reported.
- Further evaluation, error analysis, controlled model comparison, and testing on representative real-world railway data are needed before practical deployment.

## Reproducibility

The notebook currently uses Google Drive paths for the dataset and model weights. These paths must be adapted to the environment where the notebook is run.

### Requirements

The `requirements.txt` file lists the following dependencies:

- `ultralytics`
- `PyYAML`
- `matplotlib`
- `pandas`
- `opencv-python`
- `Pillow`

Install the listed dependencies using:

```bash
pip install -r requirements.txt
```

The dependency list does not currently pin package versions. For closer reproducibility, use compatible versions and record the Python and package versions used during the experiment.

### Steps to Reproduce

1. Obtain the dataset from the source linked in the Dataset section and follow its license terms.
2. Open `railway_defect_detection_yolov8_baseline.ipynb` in Google Colab or a compatible Python environment.
3. Install the required packages using `requirements.txt`.
4. Mount Google Drive if required by the notebook.
5. Configure the dataset, `data.yaml`, and model-weight paths for your environment.
6. Verify the dataset structure and label files before training or evaluation.
7. Run the notebook cells in order, following the documented workflow.

For improved reproducibility, record the Python and package versions, training configuration, dataset version, random seed where available, and the exact model checkpoint used for each evaluation.

## Future Work

Potential next steps include:

- Verifying the semantic mapping of the ten defect classes.
- Re-evaluating YOLOv8n and YOLOv8s using the same cleaned dataset splits and comparable evaluation configurations.
- Performing per-class error analysis and reviewing false-positive and false-negative detections.
- Adding representative prediction examples with bounding boxes.
- Testing model generalization on additional railway images that represent different environmental and imaging conditions.

## License

The project code and notebook are licensed under the MIT License. See [LICENSE](LICENSE).

Copyright (c) 2026 Adam Mahabayu Muhibbulloh.

The dataset is distributed separately under its own license. Please refer to the original [Mendeley Data record](https://data.mendeley.com/datasets/88sh5y3tmj/1) and the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/) for dataset terms and attribution.

The MIT License for this repository does not replace or modify the license applicable to the third-party dataset.
