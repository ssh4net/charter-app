# Charter - Introduction

![Charter](https://ssh4net.github.io/charter-app/images/charter_main_gui.png)

The primary purpose of the Charter application is to sample raw color values from images containing color charts. The application does not include built-in profiles for color charts. Instead, it uses CGATK-format profiles to load chart parameters. For convenience, it comes with CGATK files for two popular color charts: "xRite ColorChecker" and "xRite ColorChecker Digital SG." Users can also add custom profiles.

#### Key Features

- **Dynamic Chart Widget**: Users can interactively position the widget over the color chart in the image. The widget supports:
  - Perspective transformation using red corner patches.
  - Independent or elastic snapping movements for individual patches.
- **Customizable Sampling**: Control sampling radius and averaging methods (mean or mean + median).
- **Data Export**: Export color values and coordinates to applications or libraries like Colour-Science or SciPy.

#### Existing Solutions

Applications for color charts and color mathematics generally fall into these categories:

- **Conditionally free tools**: Simplified, one-click solutions for creating Adobe DCP or ICC profiles (e.g., Adobe Camera DCP Profile Tool, xRite Profiler).
- **Paid applications**: More flexible but often limited to specific outputs like DCP/ICC profiles or 3D LUTs (e.g., Lumariver Profiler, 3D LUT Creator Pro).
- **Professional software**: Expensive tools for advanced color tasks, suitable for daily use but cost-prohibitive for occasional needs.
- **Scientific Python libraries**: Powerful options like Colour-Science or SciPy, which lack graphical interfaces.

#### Rationale for Development

Modern color mathematics for correction or characterization is straightforward unless spectral measurements are involved. Working directly with raw data is more efficient than relying on commercial raw processors, especially with machine vision cameras, where characterization and correction fall entirely on the user.

Attempts to find a simple GUI for color value extraction proved unsuccessful due to:
- Prohibitive costs and lack of trial versions.
- Limitations in handling non-standard charts.
- Incompatibility with charts exhibiting both perspective and non-linear distortions.

#### Addressing Practical Challenges

The glossy material of certain charts, like the xRite Digital SG, adds sensitivity to lighting, making glare-free captures impossible in setups like Light Stage systems. Multi-angle shooting and value averaging are necessary for accurate results. Multi-camera rigs may only partially capture the chart, complicating the workflow further.

#### Development Goals

Initially designed as a companion to Colour-Science, the Charter application prioritizes precision by employing double-precision measurements. Mathematical operations were cross-verified with Colour-Science during development. Over time, core functionality was integrated directly into the application, including:

- White balance calculation.
- Color Correction Matrix computation.
- Decoding gamma encoded images (sRGB, Log).
- Black level subtraction.
- Exporting results for further processing in NumPy (Python) or GLSL (GPU shader code).
- Bake color transformations to 3D LUT.
- Compile color transformations into Common LUT format (more flexible and editable).
- etc.
