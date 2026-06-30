# ISLab-ROBONE-Sample-50

**A 50-image public reference sample of the ROBONE plastic-waste detection
dataset**, released by the **Intelligent System Laboratory (ISLab),
Department of Electrical, Electronic, and Computer Engineering,
University of Ulsan, South Korea**.

This sample accompanies the IEEE Sensors Journal paper:

> **J. Choi and K. Jo, "Illumination-Invariant Lightweight Plastic Waste
> Detection for Industrial Edge Sensors," _IEEE Sensors Journal_, 2026.**

---

## ⚠️ Citation is mandatory

**Any use of this sample — academic, educational, or otherwise — requires
citation of the paper above.**  This requirement is binding under the
license terms (see `LICENSE`).  Specifically, you must:

1. Cite the paper in any publication, preprint, technical report,
   thesis, slide deck, course material, or blog post that uses the
   sample (visualization, qualitative example, sanity-checking,
   benchmarking, derived dataset, etc.).
2. Preserve the attribution and license terms in any redistribution
   or derivative work.
3. Indicate clearly when the sample (or any subset, transformation, or
   model trained on it) is being used, and link back to this
   repository.

**BibTeX:**

```bibtex
@article{Choi2026RIC,
  author  = {Jehwan Choi and Kanghyun Jo},
  title   = {Illumination-Invariant Lightweight Plastic Waste Detection
             for Industrial Edge Sensors},
  journal = {IEEE Sensors Journal},
  year    = {2026},
  note    = {Sample dataset: ISLab-ROBONE-Sample-50,
             \url{https://github.com/<owner>/ISLab-ROBONE-Sample-50}}
}
```

> Replace `<owner>` with the actual GitHub owner once the repository
> is published.

---

## Contents

```
ISLab-ROBONE-Sample-50/
├── images/         00000001.jpg ... 00000050.jpg   (1920x1200 RGB)
├── labels/         00000001.txt ... 00000050.txt   (YOLO format)
├── classes.txt     class name per id (0-based)
├── README.md       this file
└── LICENSE         license terms (CC BY-NC-SA 4.0, citation-binding)
```

## Label format (YOLO)

Each `labels/NNNNNNNN.txt` has one detection per line:

```
<class_id> <cx_norm> <cy_norm> <w_norm> <h_norm>
```

with `class_id` 0-based from `classes.txt` and all box coordinates
normalized to `[0, 1]` with respect to the image width / height
(absolute box: `[(cx - w/2) * W, (cy - h/2) * H, w * W, h * H]`).

## Class mapping

| `class_id` | Name  | Description |
|-----------:|:------|:------------|
| 0          | PET   | Polyethylene Terephthalate (transparent bottles) |
| 1          | PET-C | PET, colored variant |
| 2          | PP-B  | Polypropylene, black variant |
| 3          | PS-W  | Polystyrene, white variant |

The four classes correspond to the highest-volume polymer streams targeted
by the polymer-level sorting stations described in the paper
(Section IV-A).

## Sampling protocol (reproducible)

- **Source split**: validation set (`val/`) of the full ROBONE dataset.
- **Random sampling**: uniform over images with ≥ 1 annotation, fixed
  seed `42` via Python `random.sample`.
- **Renaming**: sequential `00000001` to `00000050`.
- **Annotation conversion**: COCO `[x, y, w, h]` (absolute pixels,
  top-left origin) → YOLO `[cx, cy, w, h]` (normalized, center origin).

## Limitations

- **50 images is qualitative only**; it is not sufficient for training
  or for statistically meaningful benchmarking.  Treat it as a
  reference for image characteristics, annotation style, and
  industrial conveyor-belt visual conditions.
- The full ROBONE dataset (≈ 76,700 images, ≈ 510,000 annotations
  across train / val / test splits) is collected from operational South
  Korean recycling facilities and **cannot be publicly distributed**
  due to commercial confidentiality.

## License

Released under the
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
(CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
**with a binding citation requirement**.  See `LICENSE`.

In short:
- ✅ Research, education, qualitative reference.
- ✅ Sharing and adapting with attribution + same license + citation.
- ❌ Commercial use without separate agreement.
- ❌ Redistribution that strips or alters the citation / license.

## Contact

Jehwan Choi · `cjh1897@ulsan.ac.kr`
Prof. Kanghyun Jo (PI) · `acejo@ulsan.ac.kr`
Intelligent System Laboratory (ISLab), University of Ulsan, Ulsan 44610,
South Korea.
