Note: original full text and images at https://pixls.us/articles/create-lens-calibration-data-for-lensfun/


# Checklist for taking vignetting correction photos

## Preparation
* detach/unmount all filters and lenshood from the lens
* overcast sky, the sky is homogeneously lit
* open space

## Camera settings
* focus at infinity
* vignetting compensation off
* image stabilisation off, both optical and sensor
* lowest real ISO, this is normally 100 or 200, don't use extended ISO values
* aperture priority
* exposure +2EV, without clipping the highlights

## Take images
* fastest/widest aperture (1 image, e.g. at f/2)
* widest +1EV, widest +2EV, widest +3EV (3 images, e.g. f/2.8, f/4, f/5.6)
* most closed aperture (1 image, e.g. f/22)


## Check raw files
exiftool -lens* <raw image file>
exiftool -ShadingCompensation <raw image file>
exiftool -*stabilisation* <raw image file>

## Tip
After all raw samples for vignetting have been taken, run this:
```bash
exiftool -d %Y_%m_%d '-filename<$FocalLength/$FocusDistanceUpper/%f.%e' .
or
exiftool -d %Y_%m_%d '-filename<${FocalLength;s/ mm//}/${FocusDistanceUpper;s/ m//}/%f.%e' .
```

