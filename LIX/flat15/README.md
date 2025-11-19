# flat15 cells
*NSLS-II LIX and DND-CAT compatible glass window cells for solution scattering*

This design is compatible with the automatic sample exchanger robot at NSLS-II LIX beamline. Place the frame-like "spacer" piece on top of the aluminum base plate, then place the sample strip on top. The notch should be placed toward the door when mounted on the beamline (notch is close to the handle).
```
mc_measure_holder('samples-proc.xlsx','<strip name>',exp=<exposure time>, scan=True,check_sname=True,cell_format='flat15')
```
2023/12: For 2023-3 cycle, we tested the mesh scan with robotic arm sample exchange:
```
mc_auto_measure_samples('samples-proc.xlsx',configName='a1',cell_form='flat15',scan='mesh',xrange=1,offset_y=0.5) #configName is defined as a set of strips with their holder positions in the auto-exchanger
```
throughput ~ 11.5 min / 15 samples at LIX with 1s exposure time, 24 frames in flyscan mode. 9 min / 15 samples with 0.5 s/frame, 24 frames.

At DND-CAT, 
```
hidebeam;stage_out
w15x4_stage
show_beam
qdo plate1.do
```
where plate1.do looks like:
```
area_detectors_set_param("SampleThickness",0.234)
snapshoton
for (mycellrow=asc("A");mycellrow<=asc("D");mycellrow++) {
 area_detectors_take_background
 for (mycellcol=1;mycellcol<=15;mycellcol++) {
  printf("%c %d\n",mycellrow,mycellcol)
  eval(sprintf("w15x4_samp %d %d",mycellrow,mycellcol))
  mvr samp_v 0.5;waitmove
  swcollectexpert
  mvr samp_v 0.75;waitmove
  swcollectexpert
  mvr samp_v 0.75;waitmove
  swcollectexpert
 }
}
```

**File description:**

- slot_guide.stl: 3D model of a guide to place the double adhesive tape to the strip. We find it not very necessary (alignment by eye is usually sufficient), but if you are having difficulty applying the tape straight, this may help.
- spacer_brookhaven.svg: 2D vector file for spacing between the aluminum arm and the sample strips to prevent the glass from contacting the aluminum. This should be laser-cut out of 1mm thick cast acrylic plate (or anything thicker than tape + glass, and is uniform in thickness).
