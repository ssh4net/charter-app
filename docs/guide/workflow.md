# Charter Workflow

To use a Charter, you need to follow these steps:
1. **Capture** an image or multiply images of the color chart with disabled camera effects. Capture in RAW is recommended.
2. Process RAW image to a linear gamma image and native camera color space. If our processing workflow allow to work with raw bayer image (raw mosaiced monochrome image) - export raw bayer image without any processing to any lossless format (PGM, TIFF, EXR, etc).
    > If your camera does not support RAW you can use standard sRGB images. In this case, you need to use the **Import Gamma** settings to decode the image properly. If your camera support Log encoding, you can use **Log Decoding** settings to decode the image properly.
3. Change **Import Gamma/sRGB/Log** settings to decode the image properly.
   > If you are using a raw bayer image, and you know camera sensor bit depth and black level, you can use **Import Exposure/Black Lv** settings to decode the image properly.

   > MV camera sensors that have 12bit DAC, captured raw image can have values in the range 0-4095. To map this raw range to 0% - 100% of a 16bit, you need to use 4-bit shift or **+4EV Exposure** in the Charter app. 10bit will require 6-bit shift or **+6EV Exposure**. For DSLR or mirrorless RAW data (not the camera raw) that can have 14bit, you need to use 2-bit shift or **+2EV Exposure**.
   
   > Set correct Bayer pattern in **Bayer Pattern** settings.

   > If you are using a raw RGB bayer image, you can use **Demosaic RGB** settings to convert the raw bayer image to monochrome in loading time.

4. **Import** the image into Charter.
   > You can adjust **Gamma/Exposure/Black Lv** Import settings after importing the image.

   > **Warning!** Changing Gamma/sRGB/Log mode after importing the image will require re-importing the image.

5. **Load** the CGATK chart file.
   > You can use ColorCheker or ColorChecker Digital SG CGATK files from program CGATK folder or download averaged crowd sourced CGATK files from [BabelColor](https://babelcolor.com/colorchecker.htm)

   > **Warning!** Spectral measurements or non D50 white are not supported yet. Only LAB or XYZ under D50 white measurements are supported.

   > **Warning!** Some CGATK files can have incorrect combination of LGOROWLENGTH and NUMBER_OF_SETS. In that case Charter will try to correct it automatically. Result is not garateed to be correct. If you have a problem with imported chart, please contact it vendor or try to correct it manually in text editor.

6. **Place** the chart on the image.
   By default Charter open a chart and place a widget in the center of the image with some margins.
   You can also use **Rotate H / V / CW / CCW** buttons to rotate the chart.
   Use a corner patches to place the chart on the image using perspective transformation. To finetune independent patches, drag the patch to the desired position.
   > Using Move Radius settings you can change the patches elastic movement radius.

   > You can always reset the chart to the initial state by clicking the **[x]** button in the chart control.

7. **Estimate White Balance**
   If your chart have achromatic patches, you can estimate white balance by clicking the **Estimate WB** button.
   This step is optional, Charter will try to estimate white balance automatically when you click the **Estimate CCM** button.

   On success, Charter will update image preview and results window with estimated white balance.

   > If used **Highlights Scale** settings (enabled by default), Charter will normalize white balance scales to the smallest intensity equal 1.0. And image preview will be updated with reconstructed highlights. Otherwise, image preview will be updated with normalized white balance. Highlights in that case can have unexpected color tint.
   
   > Highlights reconstruction:
   ![HL reconstruction](https://ssh4net.github.io/charter-app/images/charter_wb_hl_recon.png)
   ` source -> scaled -> reconstructed highlights`

   Some optimisation steps output can be visible in console output.

   > **Warning!** If your chart does not have achromatic patches, result will be incorrect or app can crash.

   *TODO: Check how code handle the case when WB can't be estimated and optimisation code return the error.*

8. **Color Correction Matrix**
   Click the **Estimate CCM** button to estimate Color Correction Matrix.

   > **Warning!** If your chart does not have achromatic patches, result will be incorrect or app can crash.

9. Check results in **Results** window.