---
description: Tool to extract luminous sources from astronomical sky images
long_description: Tool to extract luminous sources from astronomical sky images, based on SEP library
additional_files:
---

# Source extractor

This tool can be used to extract luminous sources from sky images. It is entirely based on the [sep](https://sep.readthedocs.io/en/stable/index.html) package, which is built on [Source Extractor](https://sextractor.readthedocs.io/en/latest/Introduction.html).

## Input

Important input parameters:

1. **Input file** (`.fits` or `.tiff`) - A single-channel sky image to analyze.
2. **Mask file** (`.fits` or `.tiff`; optional) - A 2D numpy array. True values, or numeric values greater than **maskthresh**, are considered masked. Masking a pixel is equivalent to setting data to zero and noise (if present) to infinity.
3. **thresh** - Threshold pixel value for detection: `thresh * err[j, i]`, where `err[j, i]` is given by the **err_option** parameter; `j` and `i` represent the pixel indices
4. **err_option** - Sets the error that is taken into account into the detection of sources:

   - `none` - The value of **thresh** is taken as an absolute threshold.
   - `array_rms` - An array of the background RMS, i.e. for each individual pixel.
   - `float_globalrms` - A float value of the global background RMS.

The rest of the parameters are described in the documentations of [sep.Background](https://sep.readthedocs.io/en/stable/api/sep.Background.html#sep.Background) and [sep.extract](https://sep.readthedocs.io/en/stable/api/sep.extract.html#sep.extract). 


## Output

### Source Catalog

The catalogue of sources is explained [here](https://sep.readthedocs.io/en/stable/api/sep.extract.html#sep.extract).

### Images

There are 4 images as output:

- **Background image** - The output of `sep.Background` function, i.e. the estimated 2D background of the input image.
- **Background noise** - The RMS of the background image.
- **Input image** - The gray-scale input image.
- **Sources** - The sources on the background subtracted input image
- **Segmentation map**:
  - `.tiff`: Each pixel is labeled with 0 or object ID (`0` = background; `i+1` = object `i`).
  - `.png`: Binary mask (`1` = source, `0` = background).

## Acknowledgement

Bertin, E. & Arnouts, S. 1996: [SExtractor: Software for source extraction](https://ui.adsabs.harvard.edu/abs/1996A%26AS..117..393B/abstract), Astronomy & Astrophysics Supplement 317, 393

Barbary, (2016), SEP: Source Extractor as a library, Journal of Open Source Software, 1(6), 58, doi:10.21105/joss.00058
