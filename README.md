# About Dataset

This dataset contains range and color data captured by a novel RGB-D camera. The dataset features three outdoor scenes: a chair, mulch stacks in Home Depot, and a palletw on a driveway. There are two indoor scenes: both of an office. For each depth image, corresponding amplitude and color images are provided. 

## Data Acquisition 

All data in this set was acquired using a novel RGB-D camera that combines a standard RGB camera with an amplitude-modulated continuous wave (AMCW) time-of-flight (ToF) camera. This camera's innovative hardware design allows for the simultaneous generation of aligned RGB and depth data. The native resolutions are 240x320 for depth data and 1440x1920 for RGB data.

### Note

Each of the folders has the following subfolders
- `ampl_png` amplitude from TOF camera, uint16 format, at resolution (640x480) 
- `zmap_png` distance in cartesian Z-coordinate: image plane to object, uint16 format, mm units, at resolution (640x480)
- `dist_png` radial distance from image plane center to object, uint16 format, mm units, at resolution (640x480)
- `rgb_jpg` rgb image from optical camera, aligned at resolution (640x480) 
- `rgb_jpg_native` rgb image at native resolution from optical camera (1920x1440)

**The data from the ToF camera is originally at a 320x240 resolution and has been upsampled using nearest neighbor interpolation to match the 640x480 resolution of the rgb_jpg images**

-`dist_png` provides the radial distance as measured by the ToF camera.
-`zmap_png` gives the Cartesian Z-coordinate, obtained by transforming the radial distance using the camera's intrinsic parameters

A `calibration.ipynb` file in the root directory demonstrates how to transform radial distance (`dist_png`) to Cartesian Z-coordinate (`zmap_png`) using spherical to Cartesian transformation. It also provides the camera's intrinsic parameters for transforming depth data into point clouds.

## Directory Structure 

```
Scene/
  -rgb_jpg/
    -oyla_0000.jpg
    -oyla_0001.jpg
    -...
  -zmap_png/
      -oyla_0000.png
      -oyla_0001.png
      -...
  -dist_png/
      -oyla_0000.png
      -oyla_0001.png
      -... 
  -ampl_png/
      -oyla_0000.png
      -oyla_0001.png
      -...
  -rgb_jpg_native/
      -oyla_0000.jpg
      -oyla_0001.jpg
      -...
```

## Authors

[ekamresh](https://github.com/ekamresh)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details