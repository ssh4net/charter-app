[Home](https://ssh4net.github.io/charter-app/)

[Charter GUI](https://ssh4net.github.io/charter-app/user_gude#charter-gui)
- [Image control](https://ssh4net.github.io/charter-app/user_gude#image-control)
  - [View Layers](https://ssh4net.github.io/charter-app/user_gude#source--decoded--corrected--post)
  - [Zoom](https://ssh4net.github.io/charter-app/user_gude#2x--11--05x)
  - [Image Info](https://ssh4net.github.io/charter-app/user_gude#source-image-information)
- [Import Settings](https://ssh4net.github.io/charter-app/user_gude#import-image-settings)
  - [Gamma decode](https://ssh4net.github.io/charter-app/user_gude#linear--srgb--gamma--log)
  - [Gamma/Black Lv/Exposure](https://ssh4net.github.io/charter-app/user_gude#import-gamma--exposure--black-lv)
- [Load Image](https://ssh4net.github.io/charter-app/user_gude#load-image)
  - [Add New Tab +](https://ssh4net.github.io/charter-app/user_gude#add-new-tab-)
  - [Post Process](https://ssh4net.github.io/charter-app/user_gude#output-image-settings-post-process)
- [Load Chart](https://ssh4net.github.io/charter-app/user_gude#load-chart)
  - [Reset Chart x](https://ssh4net.github.io/charter-app/user_gude#x)
  - [Flip/Rotate](https://ssh4net.github.io/charter-app/user_gude#rotate-h--v--cw--ccw)
  - [Moving/Radius](https://ssh4net.github.io/charter-app/user_gude#moving-radius)
  - [Fisheye distortion](https://ssh4net.github.io/charter-app/user_gude#fisheye)
  - [Perspective Corners](https://ssh4net.github.io/charter-app/user_gude#corners)
  - [Corners size](https://ssh4net.github.io/charter-app/user_gude#zoom-patches)
- [Sampling Settings](https://ssh4net.github.io/charter-app/user_gude#sampling-control)
  - [Windows size](https://ssh4net.github.io/charter-app/user_gude#radius)
  - [Method](https://ssh4net.github.io/charter-app/user_gude#median--mean)
- [Multi Sampling](https://ssh4net.github.io/charter-app/user_gude#multi-sampling)
  - [Method](https://ssh4net.github.io/charter-app/user_gude#min--avg--median)
- [Estimate White Ballance](https://ssh4net.github.io/charter-app/user_gude#estimate-wb)
- [Estimate CCM](https://ssh4net.github.io/charter-app/user_gude#estimate-ccm)
- [DeltaE](https://ssh4net.github.io/charter-app/user_gude#delta-e)
- [Copy/Paste WB&CCM](https://ssh4net.github.io/charter-app/user_gude#copy-ccm--paste-ccm)

# Results
- [White Ballance](#white-ballance)
- [RAW to XYZ D50](#raw-to-xyz-d50)
- [Delta-E CIE2000](#delta-e-cie2000)
- [D50 to D65](#d50-to-d65)
- [XYZ D50 to sRGB](#xyz-d50-to-srgb)
- [RAW to sRGB](#raw-to-srgb)
- [Print Samples](#print-samples)
- [Save CSV](#save-csv)

![Result](https://ssh4net.github.io/charter-app/images/charter_results.png)


Every output field can be copied to clipboard. Output format for copied data depend on used settings: **Plain, Numpy, Eigen, Matlab, GLSL, CSV**.
Outputs can be varied depend on used **CCM Estimation settings**.

### White Ballance

Show estimated per-channel scale. 
Depend on used **CCM Estimation settings** show:
- **Normalized** - the sum of channel intensities is not changed, or the sum of scales equals 3.0.
- **Scaled** - estimated scales adjusted to the smallest intensity equal 1.0
- **Identity** - if used **single step** mode. And WB scales included in **RAW to XYZ D50**

### RAW to XYZ D50

Show estimated RAW Color Space to CIE XYZ (D50 white point) color transformation matrix (CCM).
Depend on used **CCM Estimation settings** show:
- if used **two step** mode **RAW to XYZ D50** color transfomation matrix wihtout embedded WB scales.
  `raw_to_xyz_ccm * (raw_colors * wb_scales)`
- if used **single step** mode **RAW to XYZ D50** color transfomation matrix with embedded WB scales.
  `raw_to_xyz_wwb_ccm * raw_colors`

### Delta-E CIE2000

Show estimated Delta-E CIE2000 error between reference colors and sampled colors with CCM or WB and CCM applied.

- **Average** average Delta-E error from all measured swatches
- **Maximum** maximal Delta-E error from all measured swatches
- **Minimum** minimal Delta-E error from all measured swatches

### D50 to D65

D50 White Point to D65 White Point cromaticity adaptation matrix (Von Krees). Chromaticity adaptation matrix to provide a proper adaptation between XYZ D50 White Point to XYZ D65 White point.

### XYZ D50 to sRGB

Integrated XYZ D50 to sRGB D65 color transformation matrix.

### RAW to sRGB

Show estimated, integrated RAW Color space to sRGB color transformation matrix.
Depend on used **CCM Estimation settings** show:
- **CCM without WB scales** - RAW to sRGB transformation matrix that can be used after **White Ballance** applied to convert RAW white ballanced colors to sRGB colors.
- **CCM with WB scales** - RAW to sRGB transformation matrix that can be used convert directly RAW colors to sRGB with white ballance in a single step.
  > ***CCM with WB scales*** is not recommended as multiplying raw colors by CCM can't reconstruct, repair or clamp highlights. And in result hightlights can have unexpected results. 
  *Pure pink color highlights are one of common results when use this matrix*.

### Print Samples

Output two windows with sampled colors:
- **Source** - sampled source colors.
- **Corrected** - corrected colors with applied CCM and WB scales.

### Save CSV

Output CSV file with:
- **Reference LAB** - reference colors in CIE LAB color space.
- **Reference XYZ** - reference colors in CIE XYZ color space.
- **Original RGB** - sampled source colors in RGB color space.
- **Linear RGB** - sampled source colors in linear RGB color space.
- **CCM** - estimated CCM matrix.
- **Coordinates** - coordinates of placed patches on image (optional).