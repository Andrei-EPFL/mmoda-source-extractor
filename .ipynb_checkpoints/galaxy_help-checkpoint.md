---
description: Tool to extract luminous sources from sky images
long_description: Tool to extract luminous sources from sky images
additional_files:
---

# Source extractor

This tool can be used to extract luminous sources from sky images. It is entirely based on the [sep](https://sep.readthedocs.io/en/stable/index.html) package, which is built on [Source Extractor](https://sextractor.readthedocs.io/en/latest/Introduction.html).

## Input

The tool accepts as input a FITS file.
Moreover, most arguments from [sep.Background](https://sep.readthedocs.io/en/stable/api/sep.Background.html#sep.Background) and [sep.extract](https://sep.readthedocs.io/en/stable/api/sep.extract.html#sep.extract) have been included as possible tunable parameters.

## Output

### Catalog of sources

The catalogue of sources, explained [here](https://sep.readthedocs.io/en/stable/api/sep.extract.html#sep.extract).

### Images

There are 4 images as output:
- **Background image** – The output of `sep.Background` function, i.e. the estimated 2D background of the input image.
- **Background noise** – The RMS of the background image.
- **Input image** – The gray-scale input image.
- **Sources** – The sources on the background subtracted input image

## Acknowledgement

Bertin, E. & Arnouts, S. 1996: [SExtractor: Software for source extraction](https://ui.adsabs.harvard.edu/abs/1996A%26AS..117..393B/abstract), Astronomy & Astrophysics Supplement 317, 393

Barbary, (2016), SEP: Source Extractor as a library, Journal of Open Source Software, 1(6), 58, doi:10.21105/joss.00058
