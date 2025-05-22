- [Workflow](https://ssh4net.github.io/charter-app/guide/workflow)
- [Charter GUI](https://ssh4net.github.io/charter-app/guide/user_guide#charter-gui)
- [Charter Results](https://ssh4net.github.io/charter-app/guide/user_guide_results#results)
- [Cherter Range Mapping](https://ssh4net.github.io/charter-app/guide/user_guide_results#range-mapping)

### Menu
- File
  - [Load/Save Project](#loadsave-project)
  - [Recent Files](#recent-files)
  - [Export LUT](#export-lut)
  - [Bit Depth](#bit-depth)
  - [Bit Depth](#bit-depth)
  - [Image Export Settings](#image-export-settings)
  - [Export Image](#export-image)
  - [Load RAW](#load-raw)
  - [Export DNG](#export-dng)
  - [Export DCP](#export-dcp)
- [Colour](#colour)
  - [Gamut](#gamut)
  - [CCM Estimation](#ccm-estimation)
  - [Log Decoding](#log-decoding)
  - [CLF Settings](#clf-settings)
- [Options](#options)
  - [Bayer Pattern](#bayer-pattern)
  - [Demosaic RGB](#demosaic-rgb)
  - [Patch Sorting](#patch-sorting)
  - [Copy Format](#copy-format)
  - [Save CSV Options](#save-csv-options)
- [Window](#window)
- [System](#system)

# Charter Menu and Settings

## File

### Load/Save Project

Loading Charter project to the current Tab.

Saving Charter project from the current Tab.

### Recent Files

Load recent files from the list. (Projects, images, charts CGATK files).

### CLF Settings

- **Extended** - Export all color correction steps as CLF nodes:
RAW to XYZ D50, XYZ D50 to D##, XYZ D## to Color Space. Most flexible and editable mode. (default)
- **Combined** - Export all color correction steps as a single combined CLF node: RAW to Color Space.

### Export LUT

Export White Balance and estimated Color Correction Matrix in Common LUT format or bake it as a *.cube 3D LUT file.

### Bit Depth

**8/16 int or 16/32 float** - Export image bit depth. **16 int** is default.

### Export Settings

Export image settings.

- **Linear** - Export image in linear gamma (default).
- **sRGB EOTF** - Export image in sRGB gamma.

### Export Image

Export image in linear or sRGB gamma encoding.

## Load RAW
Load mozaiced RAW image:
- **BIN/RAW** - Load binary/RAW sensor data.
- **Camera RAW** - Load camera RAW image (e.g., DNG, CR2, NEF, etc.).
- **DNG** - Load DNG image. (only mozaiced RAW data)

## Export DNG
Export **DNG** image with embedded **DCP profile**.
**Warning**: Embedding only mandatory for DCP profile tests metadata.

## Export DCP
Export **Digital Camera Profile** (DCP) file. Can be used in various raw processors (e.g., Lightroom, RawTherapee, etc.).

### Quit

End application work.

## Colour

### Gamut
- **sRGB** (default) - sRGB color space. (D65 white point)
- **AdobeRGB** - Adobe RGB color space. (D65 white point)
- **ProPhotoRGB** - ProPhoto RGB color space. (D50 white point)
- **ACES2065-1** - ACES color space (AP0). (D60 white point)
- **ACEScg** - ACES color space (AP1). (D60 white point)
- **Rec2020** - Rec.2020 color space. (D65 white point)
- **DCI-P3** - DCI-P3 color space. (D65 white point)
- **Filmlight E-Gamut** - Filmlight E-Gamut color space. (D65 white point)
- **XYZ** - CIE XYZ color space. (D50 white point)

### CCM Estimation

- **WB First** - Estimate White Balance first, then estimate Color Correction Matrix.
- **Highlights Scale** - Normalize WB scales to the smallest intensity equal 1.0.
- **Single step** - Estimate White Balance and Color Correction Matrix in one step.

### Log Decoding

**S-Log/S-Log2/S-Log3/...** - Used Log decoding curve.
**Custom** - Log decoding curve - you can use any color space from inclided OCIO config file.
***Log Decoding** is not well tesed. Use with caution.*

## Options

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

**Log Level** - Set log level. [Off/Debug/Info/Warn/Error/Critical] **Info** is default.
