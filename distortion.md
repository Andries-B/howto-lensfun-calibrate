# Calculating distortion parameters

Note: original full text and images at https://pixls.us/articles/create-lens-calibration-data-for-lensfun/

Summary 

```bash
Start Hugin
Select menu [ Interface | Expert ]
Load tiff file from distortion/exported
Set the lens type to Normal (rectiliniar) for normal standard lenses

Set focal length
Set focal length multiplier (for full frame the value is 1)

Select tab |Control Points|
Disable auto fine-tune
Enabe auto add
Disable auto-estimate

Zoom image to 200% (or keyboard [2])
Click 2 control point (1 left, 1 right)
Select from the mode dropdown list [ Add new line ]
Now continue adding corresponding control points in both pictures till you’re in the middle on both sides
Zoom out by pressing [0] and check it if everything has been added correctly

While you are zoomed out, find a line which is about 3rd into the image from the top to repeat adding a line. Zoom to 200% again, select the first control points and again [ Add new line ] which will result in line4

Zoom out by pressing [0] and check that you have two lines, line3 and line4

Select tab |Stitcher|
Select Projection [ Rectiliniar ]

Select tab |Photos|
Select under Optimize, Geometric [ Custom parameters ]
A new tab |Optimizer| will appear

Select tab |Optimizer|
Select the 'a', 'b' and 'c' lens parameters
Click [ Optimize now! ] and accept calculation with Yes

The calculated correction values for 'a', 'b' and 'c' are now displayed in the tab
Right-click on the filename, [ Lens | Save lens to ini file ]
Find 'a', 'b' and 'c' in the ini file; copy them to lenses.conf

```
