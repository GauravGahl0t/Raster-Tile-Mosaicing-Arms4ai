# Raster Tile Mosaicing - Cloudless Mosaic Generation

This project demonstrates a complete workflow for merging multiple georeferenced satellite raster tiles (GeoTIFFs) into a single cloudless mosaic image using Python-based geospatial libraries.

## Overview

The notebook performs the following tasks:
1. Load and validate multiple GeoTIFF raster tiles
2. Verify spatial properties (CRS, resolution, extent)
3. Merge tiles into a seamless mosaic
4. Handle overlapping regions and NoData values
5. Export georeferenced output
6. Generate comprehensive visualizations and statistics

## 🛠️ Libraries Used

- **rasterio** (v1.3+): Core library for reading/writing geospatial raster data and performing merge operations
- **numpy**: Numerical operations and array manipulation
- **matplotlib**: Data visualization, plotting, and image rendering
- **warnings**: Suppressing non-critical warnings for cleaner output

### Installation
Download the dataset using the link (Download Dataset: https://objectstore.e2enetworks.net/btechtasksampledata/data.zip) and save in data folder
```
Or install all dependencies at once:
```bash
pip install -r requirements.txt
```

## 📁 Project Structure

```
Arms4ai/
├── data.ipynb                             
├── README.md                             
├── cloudless_mosaic.tif                
├── sample_tiles_preview.png              
├── cloudless_mosaic_visualization.png     
├── mosaic_comparison.png                  
├── mosaic_histograms.png                
└── data/                                   
    ├── 4_20241124_054616_030_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 5_20241124_054615_396_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 6_20241124_054614_762_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 7_20241124_054614_128_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 17_20241129_054359_147_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 18_20241129_054358_499_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 19_20241129_054357_865_SN50_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 32_20240716_043003_536_SN32_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    ├── 33_20240716_043002_901_SN32_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
    └── 34_20240716_043002_264_SN32_L1C_MS_ortho_8bit_ncc_rendered_7_4.tif
```


##  Methodology

### Overlap Handling Strategy

When tiles overlap, the "first" method is used - pixels from the first tile in the list take precedence. This ensures:
- Deterministic output (same input order = same output)
- No averaging or blending artifacts
- Consistent pixel values across runs

### Color Normalization (Visualization Only)

For display purposes, 2-98 percentile stretching is applied:
- Enhances contrast for better visualization
- Removes outliers that skew the display range
- Does not modify the actual output GeoTIFF data

### Georeferencing Preservation

All spatial metadata is preserved:
- **CRS**: Coordinate Reference System from input tiles
- **Transform**: Affine transformation matrix
- **Bounds**: Spatial extent of the mosaic
- **Resolution**: Pixel size in map units


## Author
Gaurav Gahlot
