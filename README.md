# ISLab-ROBONE-Sample-50

A **50-image public reference sample** of the **ROBONE plastic-waste
detection dataset**, released by the **Intelligent System Laboratory
(ISLab)**, Department of Electrical, Electronic, and Computer Engineering,
**University of Ulsan**, Republic of Korea.

The sample is provided so that researchers can inspect the data
characteristics of the ROBONE collection — industrial conveyor-belt
imagery, fine-grained polymer-level labelling, and high-resolution
(1920×1200) RGB capture — without access to the full proprietary
dataset, which is not redistributable.

---

## Contents

```
ISLab-ROBONE-Sample-50/
├── images/         00000001.jpg ... 00000050.jpg   (1920×1200 RGB, JPEG)
├── labels/         00000001.txt ... 00000050.txt   (YOLO format)
├── classes.txt     class name per id (0-based)
├── README.md       this file
├── CITATION.cff    machine-readable citation metadata
└── LICENSE         license terms (CC BY-NC-SA 4.0)
```

## Label format (YOLO)

Each `labels/NNNNNNNN.txt` file has one detection per line:

```
<class_id> <cx_norm> <cy_norm> <w_norm> <h_norm>
```

where `class_id` is 0-based (matching `classes.txt`) and all box
coordinates are normalized to `[0, 1]` with respect to the image width
and height. The absolute box in pixels is recovered as
`[(cx − w/2)·W, (cy − h/2)·H, w·W, h·H]`.

## Class mapping (`classes.txt`)

| `class_id` | Name  | Description |
|-----------:|:------|:------------|
| 0          | PET   | Polyethylene Terephthalate (transparent bottles) |
| 1          | PET-C | PET, colored variant |
| 2          | PP-B  | Polypropylene, black variant |
| 3          | PS-W  | Polystyrene, white variant |

The four classes correspond to the highest-volume polymer streams handled
by polymer-level sorting stations in operational South Korean recycling
facilities.

## Sampling protocol (reproducible)

- **Source split**: validation set of the full ROBONE collection.
- **Random sampling**: uniform over images with at least one annotation,
  using Python `random.sample` with a fixed seed of `42`.
- **File renaming**: sequential `00000001` through `00000050`.
- **Annotation conversion**: COCO `[x, y, w, h]` (absolute pixels,
  top-left origin) → YOLO `[cx, cy, w, h]` (normalized, center origin).
- **No augmentation, no resizing**: images are the original JPEGs.

## Acquisition context

The full ROBONE collection (~76,700 images, ~510,000 annotations)
was acquired from operational South Korean recycling facilities to
support research on industrial plastic-waste detection and sorting. The
full collection cannot be redistributed due to commercial confidentiality
with the partner facilities; this 50-image sample is released as a
public qualitative reference.

## Intended use

- Inspecting the imagery and annotation style of ROBONE.
- Sanity-checking detector implementations against the data
  distribution (resolution, polymer-class definitions, lighting,
  conveyor-belt scene).
- Academic and educational illustrations.

The sample is **not** intended as a training or benchmarking set on its
own — 50 images are insufficient for statistically meaningful detector
evaluation.

## License

Released under the
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0
International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
license. See `LICENSE`.

In short:

- ✅ Free for academic research, education, and qualitative reference.
- ✅ You may share and adapt with **attribution** and **same license**.
- ❌ **No commercial use** without a separate agreement.
- ❌ Redistribution must preserve the attribution and license notices.

## Attribution

When using this sample, please credit:

> **ISLab-ROBONE-Sample-50** — Intelligent System Laboratory,
> University of Ulsan (2026).
> `https://github.com/<owner>/ISLab-ROBONE-Sample-50`

A machine-readable citation entry is also provided in `CITATION.cff`,
which GitHub renders as a *"Cite this repository"* button on the
repository sidebar.

## Contact

- Jehwan Choi · `cjh1897@ulsan.ac.kr`
- Prof. Kanghyun Jo (PI) · `acejo@ulsan.ac.kr`

Intelligent System Laboratory (ISLab)
Department of Electrical, Electronic, and Computer Engineering
University of Ulsan, Ulsan 44610, Republic of Korea
