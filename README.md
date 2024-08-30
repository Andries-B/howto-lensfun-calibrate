# Howto for lensfun calibration script "lens_calibrate.py"
Howto and notes for using lens_calibrate.py for lensfun

See Andreas Schneider’s tutorial and python scripts:
https://pixls.us/articles/create-lens-calibration-data-for-lensfun/

GitHub Project: https://github.com/lensfun/lensfun GitHub Page: https://lensfun.github.io/


# Installing environment

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

./lens_calibrate tca
./lens_calibrate --complex-tca tca

./lens_calibrate vignetting

./lens_calibrate generate_xml

./lens_calibrate ship
```

