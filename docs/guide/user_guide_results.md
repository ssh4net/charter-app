[Home](https://ssh4net.github.io/charter-app/)

[Charter GUI](#charter-gui)
- [Image control](#image-control)
  - [View Layers](#source--decoded--corrected--post)
  - [Zoom](#2x--11--05x)
  - [Image Info](#source-image-information)
- [Import Settings](#import-image-settings)
  - [Gamma decode](#linear--srgb--gamma--log)
  - [Gamma/Black Lv/Exposure](#import-gamma--exposure--black-lv)
- [Load Image](#load-image)
  - [Add New Tab +](#add-new-tab-)
  - [Post Process](#output-image-settings-post-process)
- [Load Chart](#load-chart)
  - [Reset Chart x](#x)
  - [Flip/Rotate](#rotate-h--v--cw--ccw)
  - [Moving/Radius](#moving-radius)
  - [Fisheye distortion](#fisheye)
  - [Perspective Corners](#corners)
  - [Corners size](#zoom-patches)
- [Sampling Settings](#sampling-control)
  - [Windows size](#radius)
  - [Method](#median--mean)
- [Multi Sampling](#multi-sampling)
  - [Method](#min--avg--median)
- [Estimate White Ballance](#estimate-wb)
- [Estimate CCM](#estimate-ccm)
- [DeltaE](#delta-e)
- [Copy/Paste WB&CCM](#copy-ccm--paste-ccm)

# Results

![Result](https://ssh4net.github.io/charter-app/images/charter_results.png)

### White Ballance

Show estimated per-channel scale. 
Depend on used **CCM Estimation settings** show:
- **Normalized** - the sum of channel intensities is not changed, or the sum of scales equals 3.0.
- **Scaled** - estimated scales adjusted to the smallest intensity equal 1.0
