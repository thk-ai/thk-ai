---
title: 'Master''s thesis "Tribraide": Kai Altwicker develops a fusion-based detector for AI-generated images'
date: "2026-04-29"
lang: en
---

# Master's thesis "Tribraide": Kai Altwicker develops a fusion-based detector for AI-generated images

![Kai Altwicker during his talk on "Tribraide" at the Institute of Media and Imaging Technology at TH Köln.](../../figures/news/salm26a/salm26a-tribraide-titel.jpg){fig-alt="Speaker in front of the title slide of the master's thesis Tribraide"}

`2026-04-29`

With "Tribraide", Kai Altwicker has developed a detector for AI-generated images in his master's thesis at the [Institute of Media and Imaging Technology](https://www.th-koeln.de/informations-medien-und-elektrotechnik/institut-fuer-medien--und-phototechnik-imp_14807.php) at TH Köln that goes beyond conventional single-model approaches. The work combines spatial-domain, frequency, and reconstruction analyses and exploits the complementarity of these feature spaces to detect synthetic content. The thesis was supervised by [Prof. Dr. Jan Salmen](https://www.th-koeln.de/personen/jan.salmen/) and [Prof. Dr. Gregor Fischer](https://www.th-koeln.de/personen/gregor.fischer/).

## Approach

Instead of relying on a single detector, Tribraide fuses three complementary views of the image: a spatial-domain analysis, a frequency-spectrum analysis, and a reconstruction-error analysis. Each view responds to different traces of generative methods — structural artefacts, characteristic frequency patterns, and inconsistencies under back-projection. Merging the feature spaces yields a classifier that outperforms individual models in both robustness and detection rate.

![Slide on the sampling procedure and the bucketing strategy for variable image resolutions in the training dataset.](../../figures/news/salm26a/salm26a-dataset.jpg){fig-alt="Talk slide on dataset sampling with a bucketing strategy"}

## Robustness under realistic image alterations

A central finding concerns the stability of the method under typical image-processing steps such as compression and noise. Whereas many detectors lose discriminative power even under moderate JPEG compression, Tribraide remains reliable thanks to the fusion of the three feature spaces — a property profile that is essential for practical use in media forensics and image authentication.

![Discussion of the results during the colloquium at the Institute of Media and Imaging Technology at TH Köln.](../../figures/news/salm26a/salm26a-diskussion.jpg){fig-alt="Colloquium room with speaker and audience during the results discussion"}

## Continuation at TH Köln

Kai Altwicker remains at TH Köln and is now a doctoral researcher in the group of [Prof. Dr. Pascal Cerfontaine](https://www.th-koeln.de/personen/pascal.cerfontaine/) (AI4Science). A detailed article on the master's thesis is available via [this link](https://lnkd.in/d2VfGjX9).
