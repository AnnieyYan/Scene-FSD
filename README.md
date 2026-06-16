# Scene-FSD
Self-built Dataset
# Scene-FSD Dataset (Partial Release)

## Overview

Scene-FSD (Scene-oriented Fire and Smoke Dataset) is a large-scale dataset constructed from real surveillance systems to support fire and smoke detection research. It covers four key early‑warning scenarios: **transportation**, **open industrial sites**, **forest monitoring**, and **high‑rise buildings**. All images are sourced from real surveillance scenarios and annotated manually.

This release contains a **partial subset** of the full dataset. The complete dataset will be made publicly available upon paper acceptance.

## Dataset Statistics (Full Dataset for Reference)

| Scenario                     | Images | Bounding Boxes |
|------------------------------|--------|----------------|
| Transportation               | 3,150  | -              |
| Open Industrial Site         | 3,205  | -              |
| Forest monitoring            | 2,890  | -              |
| High‑rise building           | 2,780  | -              |
| **Total**                    | 12,025 | 31,842         |

*Note: The partial release includes a subset of the above. Please check the release package for exact numbers.*

## Directory Structure

- Coordinates are normalized to [0,1] relative to image width/height.
- Class IDs:  
  - `0` : fire  
  - `1` : smoke

All annotations were manually created using LabelImg. For semi‑transparent smoke edges, the approximate contour was annotated; weak initial flames were marked after consensus among multiple annotators. Two rounds of manual review ensured quality.

## Data Splits

The full dataset is split 8:1:1 into training, validation, and testing sets. The partial release follows the same split ratio. Raw images were cropped to 1024×1024, and during training inputs are dynamically scaled to 512×512.

## Usage with YOLO

Create a `dataset.yaml` file (included) with the following content:

```yaml
path: /path/to/Scene-FSD
train: images/train
val: images/val
test: images/test
nc: 2
names: ['fire', 'smoke']
