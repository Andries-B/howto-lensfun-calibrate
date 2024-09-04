# Howto for lensfun calibration script "lens_calibrate.py"
Howto and notes for using lens_calibrate.py for lensfun

GitHub Project: https://github.com/lensfun/lensfun GitHub Page: https://lensfun.github.io/

See Andreas Schneider’s tutorial and python scripts:
https://pixls.us/articles/create-lens-calibration-data-for-lensfun/

Original python program lens_calibrate.py:
https://gitlab.com/cryptomilk/lens_calibrate

# Setting up Python environment (Ubuntu 22.04)

- [ ] install darktable, hugin, imagemagick (convert) and gnuplot

```bash
sudo apt-get install python3-pip python3-venv
sudo apt-get install build-essential python-all-dev libexiv2-dev libboost-python-dev

python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```


# Running lens_calibrate.py
```bash
source .venv/bin/activate

./lens_calibrate init

./lens_calibrate distortion

./lens_calibrate --complex-tca tca

./lens_calibrate vignetting

./lens_calibrate generate_xml

./lens_calibrate ship
```

# Vignetting and Panasonic Lumix camera's
Lumix camera's output 2 different raw files,
depending on the camera setting "vignetting compensation" (menu "VIGNETTING.COMP").
When the vignetting compensation setting is OFF,
the raw file is a more pure raw file.
When the vignetting compensation setting is ON,
the camera applies some sort of vignetting compensation to the raw file.
Lumix L-mount and MFT camera's default to VIGNETTING.COMP set to ON,
but the user can change it in the menu.
The camera stores the vignetting compensation setting in an exif tag "Shading Compensation" in the raw file.
E.g. exiftool can read the tag "Shading Compensation".

Lensfun is intended for correcting pure raw images. So all (most?) calibration data in its database are done with vignetting compensation OFF.
When applying the default calibration profile to an image that has been shot with vignetting compensation ON,
the corners will be too bright (like over compensation).
For those images a different calibration profile is needed,
that takes into account the in camera processing that is already in the image. 

In summary: 1 lens, 1 camera, 1 setting ON or OFF -> 2 different raw files -> 2 different profiles

The lensfun database must contain unique lens names.

Solution: create 2 different profile names, e.g.
```bash
<model>my lens</model>
<model>my lens Lumix vignetting compensation ON</model>
```

In darktable, both lenses show up in the menu. The first profile will be selected by default. From the menu the other can be selected.

Exiftool command to determine vignetting compensation mode from raw file
```bash
exiftool -shadingcompensation *.RW2
```
