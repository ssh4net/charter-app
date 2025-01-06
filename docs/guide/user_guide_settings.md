[Home](https://ssh4net.github.io/charter-app/)

[Charter GUI](https://ssh4net.github.io/charter-app/guide/user_guide#charter-gui)

[Charter Results](https://ssh4net.github.io/charter-app/guide/user_guide_results#results)

[Cherter Range Mapping](https://ssh4net.github.io/charter-app/guide/user_guide_results#range-mapping)

### Menu
- File
  - [Load/Save Project](#loadsave-project)
  - [Export LUT](#export-lut)
  - [Export Image](#export-image)
- [Options](#options)
  - [CCM Estimation](#ccm-estimation)
  - [Log Decoding](#log-decoding)
  - [Bayer Pattern](#bayer-pattern)
  - [Demosaic RGB](#demosaic-rgb)
  - [Patch Sorting](#patch-sorting)
  - [Image Export Settings](#image-export-settings)
  - [Bit Depth](#bit-depth)
  - [Copy Format](#copy-format)
  - [Save CSV Options](#save-csv-options)
- [Window](#window)
  - 
- [Settings](#settings)

# Charter Menu and Settings

## File

### Load/Save Project

Loading Charter project to the current Tab.

Saving Charter project from the current Tab.

**Results:**
- White Ballance.
- Color Correction Matrix.
- Delta-E CIE2000.
- Delta-E Heat map.

**Chart:**
- Path to used chart CGATK file.
- Chart and chart swatches placement.

**Image:**
- Path to used image file.
- Image import settings: gamma, exposure, black level.
- Image export settings: gamma, exposure, black level.

### Export LUT

Export White Balance and estimated Color Correction Matrix in Common LUT format or bake it as a *.cube 3D LUT file.

### Export Image

Export image in linear or sRGB gamma encoding.

### Quit

End application work.

## Options

### CCM Estimation

- **WB First** - Estimate White Balance first, then estimate Color Correction Matrix.
- **Highlights Scale** - Normalize WB scales to the smallest intensity equal 1.0.
- **Single step** - Estimate White Balance and Color Correction Matrix in one step.

### Log Decoding

**S-Log/S-Log2/S-Log3/...** - Used Log decoding curve.
**Custom** - Log decoding curve - you can use any color space from inclided OCIO config file.
***Log Decoding** is not well tesed. Use with caution.*

### Bayer Pattern

**RGGB/GRBG/GBRG/BGGR** - Used Bayer pattern for RAW image decoding. **RGGB** is default.

### Demosaic RGB

Demosaic RGB image.
Usually raw images are monochrome, when some apps can export raw images as RGB. In this case, you can use **Demosaic RGB** to convert RGB image to monochrome in loading time.

### Patch Sorting

**Index/Rows/Columns** - Patch sorting method. **Index** is default.
CGATK files usually have swatches sorted by a rows or columns. When Colour-Science library can have a presets for common color charts stored in most intuitive way, when grayscale swatches one after another.
Some CGATK files can have patches sorted by index.
Use this option to set the most suitable sorting method for your CGATK file or your output target.

### Image Export Settings

### Export Settings

- **Linear** - Export image in linear gamma.
- **sRGB EOTF** - Export image in sRGB gamma.
*At this moment **Charter** limited to sRGB color space as a target. Other color spaces and gamma encodings will be added in the future.*

### Bit Depth

**8/16 int or 16/32 float** - Export image bit depth. **16 int** is default.

### Copy Format

**Plain/Numpy/Eigen/Matlab/GLSL/CSV** - Output format for copied data. **Plain** is default.

### Save CSV Options

- **Labels** - Output labels column.
- **Headers** - Output headers row.
- **All Charts** - Export all tabs charts data in CSVs.
- **Coordinates** - Output coordinates of placed patches on the image (optional).

## Window

Dockable windows control. Windows can be detached and moved to another screen.
**Warning**: App do not store windows position and size. You must set it up every time you start the app.

- **Image Control/Chart/Result/Range Mapping** - Show/Hide dockable windows.
- **Dock All** - Dock all windows to the main window.

## System

**Console** - Show/Hide console window. Console window is used for debugging and development.
*At this moment enabled by defailt. Can show additional information about Charter work and results.*
