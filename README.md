# M2-US Dataset Splits

This README describes the `train`, `val`, and `test` folders in this directory. Together, these folders organize the M2-US ultrasound data for 26 tasks across four task types: classification, segmentation, regression, and detection.

## Split folders

- `train/` contains the training data and task manifests.
- `val/` contains the validation data and task manifests.
- `test/` contains the separate test data supplied for ranking evaluation. Follow the study's evaluation protocol when using this split.

Each split follows the same general structure:

```text
<split>/
├── Classification/
├── Segmentation/
├── Regression/
├── Detection/
└── csv_files/
```

The task directories contain task-specific datasets and their associated files. `csv_files/` contains CSV manifests for the tasks in that split. The three splits may not contain identical task manifests.

## Manifest contents

Each CSV includes a `task_id` to identify its task. The remaining columns vary by task type and generally link the samples to their files and labels:

- **Classification:** image paths and class labels.
- **Segmentation:** image paths and corresponding mask paths.
- **Regression:** image paths and landmark-coordinate columns, such as `point_1_xy` and `point_2_xy`.
- **Detection:** image paths and bounding-box coordinates; some manifests also reference XML annotations.

Image and annotation paths in the manifests are relative paths. Preserve the split directory structure so these paths continue to resolve. Task-specific label definitions and annotation formats should be interpreted using the corresponding task metadata and dataset documentation.
