---
description: Tool to extract luminous sources from sky images
long_description: Tool to extract luminous sources from sky images
additional_files:
---

# Source extractor

This tool can be used to extract luminous sources from sky images. It is entirely based on the [sep](https://sep.readthedocs.io/en/stable/index.html) package, which is built on [Source Extractor](https://sextractor.readthedocs.io/en/latest/Introduction.html).

## Input

Important input parameters:

1. **Input file** - A FITS or a TIFF file that contains the sky image with one channel
2. **thresh** - Threshold pixel value for detection: `thresh * err[j, i]`, where `err[j, i]` is given by the **err_option** parameter; `j` and `i` represent the pixel indices
3. **err_option** - Sets the error that is taken into account into the detection of sources:

    A. `array_rms` - An array of the background RMS, i.e. for each individual pixel. 
   
    B. `float_globalrms` - A float value of the global background RMS.

The rest of the parameters are described in the documentations of [sep.Background](https://sep.readthedocs.io/en/stable/api/sep.Background.html#sep.Background) and [sep.extract](https://sep.readthedocs.io/en/stable/api/sep.extract.html#sep.extract). 

**TODO**: We plan to include the`mask` parameter.

## Output

### Catalog of sources

The catalogue of sources is explained [here](https://sep.readthedocs.io/en/stable/api/sep.extract.html#sep.extract).

### Images

There are 4 images as output:

- **Background image** - The output of `sep.Background` function, i.e. the estimated 2D background of the input image.
- **Background noise** - The RMS of the background image.
- **Input image** - The gray-scale input image.
- **Sources** - The sources on the background subtracted input image
- **Segmentation map**: 
  - A `.tiff` file - the array of integers with same shape as data. Pixels not belonging to any object have value 0. All pixels belonging to the `i`-th object (e.g., `objects[i]`) have value `i+1`. 
  - A `.png` file - the image obtained from the `.tiff`file, where all pixels belonging to a source have a value of 1 and the rest of the pixels have a value of 0.

## Acknowledgement

Bertin, E. & Arnouts, S. 1996: [SExtractor: Software for source extraction](https://ui.adsabs.harvard.edu/abs/1996A%26AS..117..393B/abstract), Astronomy & Astrophysics Supplement 317, 393

Barbary, (2016), SEP: Source Extractor as a library, Journal of Open Source Software, 1(6), 58, doi:10.21105/joss.00058
