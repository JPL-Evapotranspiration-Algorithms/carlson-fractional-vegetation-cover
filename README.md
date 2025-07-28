# carlson-fractional-vegetation-cover

Fractional Vegetation Cover (FVC) Remote Sensing Method from Carlson et al 1997 Python Package

Gregory H. Halverson (they/them)<br>
[gregory.h.halverson@jpl.nasa.gov](mailto:gregory.h.halverson@jpl.nasa.gov)<br>
NASA Jet Propulsion Laboratory 329G
  

## Overview

This package provides a Python implementation of the Fractional Vegetation Cover (FVC) algorithm described by Carlson & Ripley (1997). It converts NDVI (Normalized Difference Vegetation Index) data to FVC using a linear scaling method, suitable for remote sensing applications.

## Features

- Converts NDVI to Fractional Vegetation Cover (FVC)
- Supports both NumPy arrays and `rasters.Raster` objects
- Based on peer-reviewed scientific literature

## Installation

Install via pip:

```fish
pip install carlson-fractional-vegetation-cover
```

## Usage

```python
import numpy as np
from carlson_fractional_vegetation_cover import carlson_fractional_vegetation_cover

# Example NDVI array
NDVI = np.array([[0.1, 0.3, 0.5], [0.04, 0.52, 0.25]])
FVC = carlson_fractional_vegetation_cover(NDVI)
print(FVC)
```

## Algorithm

The algorithm linearly scales NDVI values between two reference points:

- NDVIv (full vegetation): 0.52 ± 0.03
- NDVIs (bare soil): 0.04 ± 0.03

The formula:

```
FVC = clip((NDVI - NDVIs) / (NDVIv - NDVIs), 0.0, 1.0)
```

Values below NDVIs are set to 0 (bare soil), above NDVIv to 1 (full vegetation), and in between are linearly scaled.

## References

- Carlson, T.N., & Ripley, D.A. (1997). On the relation between NDVI, fractional vegetation cover, and leaf area index. Remote Sensing of Environment, 62(3), 241-252. [https://doi.org/10.1016/S0034-4257(97)00104-1](https://doi.org/10.1016/S0034-4257(97)00104-1)

## License

See LICENSE file for details.