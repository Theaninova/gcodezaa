# GCodeZAA

This is a post-processing script to enable smooth(-ish) non-planar top surfaces through
a process I've come to call "Z Anti-Aliasing", to differentiate it from true non-planar
top surfaces. Maybe "Surface Layer Contouring" would be a better name.

This script is not super user friendly, but should be fine as a proof-of-concept to hopefully
get this implemented in slicers directly.

## Features

- Close to zero extra printing time cost
- Works on any model
- Works on any surface (not just the top most like many other projects)
- Sub-layer z-details. You can finally add surface textures in your 3d editor!
- Greatly improved surface finish of shallow angle surfaces
- Supports most of the slicer features

## Limitations

- Only works in OrcaSlicer
- Non-planar extrusion flow is not great and needs further testing
- Overlapping/double extrusion (this might be solveable by using ironing lines)
- Random artifacts in walls (this might be solveable by using ironing lines)
- Only STLs are supported
- Requres inner/outer wall order
- Only Klipper is supported (marlin could be done with some more work)
- Layer height is less flexible towards coarse heights

## Todo

- [x] Ironing support
- [ ] Wall width flow compensation
- [ ] Travel moves!
- [ ] proper detection if the surface is covered by another line in the next layer to avoid artifacts.
      Percentage coverage would be even better as a transition factor between normal z and contoured z.
- [ ] Overhang z contouring
- [ ] Integrate properly into OrcaSlicer

## Usage

1. Slice normally
2. Create a new directory for the plate models
3. For each object on the plate, right click and select "Export as one STL..." and save it **as the exact object name** to the directory
4. Export the gcode file
5. Run the script as `python gcodezaa [path to gcode] -o [path to output] -m [path to the stl directory]`

You can use PrusaSlicer to preview the generated GCode, though line height and width will not be displayed properly.

## Results

![](./images/benchy_roof_side.jpg)
![](./images/benchy_side.jpg)
