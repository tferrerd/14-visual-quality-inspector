# Committed dataset

**Source dataset:** MVTec AD bottle category, Voxel51 mirror

**Selection:** 60 source training-normal bottle images plus all 83 published bottle test images; original split/defect labels preserved. Full-source PNG images and available masks are included for this subset.

**Data license:** [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). This applies to the data, independently of the project code.

## Sources

- https://www.mvtec.com/research-teaching/datasets/mvtec-ad
- https://huggingface.co/datasets/Voxel51/mvtec-ad/tree/30a183a3b96e3aef953f230784b123b719b09d97

## CSV files

| File | Rows | Bytes |
|---|---:|---:|
| [bottle_index.csv](raw/bottle_index.csv) | 143 | 19,684 |
| [bottle_grayscale32.csv](raw/bottle_grayscale32.csv) | 143 | 518,042 |

Attribution: Paul Bergmann, Michael Fauser, David Sattlegger, Carsten Steger / MVTec Software GmbH, MVTec AD (2019); Voxel51 mirror. bottle_index.csv describes actual source images and defect masks. bottle_grayscale32.csv is explicitly derived: grayscale conversion and Pillow resizing to 32×32 pixels; values are image measurements, not generated observations. Fit on source training-normal images only; reserve test labels/masks for evaluation.

The CSV files contain published observations or their documented format conversion; no training records were invented. Source formats and raw CSV exports are distinguished by the manifest. File checksums and schemas are recorded in [csv-manifest.json](csv-manifest.json).
